### **Lab 04 : Stratégie de défense (Blue Team)**  
L'objectif de ce lab est de mettre en place une stratégie de défense robuste pour protéger l'infrastructure contre les attaques futures. Voici les étapes à suivre, en utilisant **Grafana** et **Prometheus** comme outils principaux de surveillance, ainsi que des mesures de sécurité supplémentaires pour le serveur web Linux, y compris une section sur la **cryptographie** pour protéger les données sensibles.

---

### **1. Mise en place d'outils de détection et de surveillance**  
Pour surveiller et détecter les activités suspectes, nous allons déployer une stack de monitoring basée sur **Prometheus** (pour la collecte de métriques) et **Grafana** (pour la visualisation et l'analyse des données).  

#### **a. Installation de Prometheus**  
- **Rôle :** Prometheus est un système de surveillance et d'alerte open source qui collecte des métriques à partir de diverses sources (serveurs, applications, etc.).  
- **Configuration :**  
  - Installer Prometheus sur un serveur dédié pour éviter les conflits de ressources.  
  - Configurer les **exporters** pour collecter les métriques des serveurs (exemple : Node Exporter pour les métriques système).  
  - Définir des **alertes** dans Prometheus pour détecter les anomalies (exemple : utilisation CPU élevée, trafic réseau suspect).  

#### **b. Installation de Grafana**  
- **Rôle :** Grafana est un outil de visualisation de données qui permet de créer des tableaux de bord pour surveiller les métriques collectées par Prometheus.  
- **Configuration :**  
  - Installer Grafana sur un serveur dédié pour des raisons de performance et de sécurité.  
  - Configurer Grafana pour se connecter à Prometheus en tant que source de données.  
  - Créer des tableaux de bord pour surveiller :  
    - L'utilisation des ressources (CPU, mémoire, disque).  
    - Le trafic réseau.  
    - Les logs d'accès au serveur web.  
  - Configurer des alertes dans Grafana pour notifier l'équipe en cas d'activité suspecte.  

#### **c. Sécurisation des serveurs Prometheus et Grafana**  
- **Authentification forte :** Utiliser des mots de passe complexes et activer l'authentification à deux facteurs (2FA) pour Grafana.  
- **Chiffrement :** Configurer HTTPS pour sécuriser les communications entre les utilisateurs et Grafana/Prometheus.  
- **Restriction d'accès :** Limiter l'accès aux serveurs Prometheus et Grafana à certaines adresses IP ou réseaux autorisés.  

---

### **2. Mise en place de mesures de sécurité sur le serveur web Linux**  
Pour protéger le serveur web, nous allons déployer des outils de sécurité supplémentaires :  

#### **a. Installation d'un IPS/IDS : Suricata**  
- **Rôle :** Suricata est un système de détection et de prévention d'intrusions (IDS/IPS) qui analyse le trafic réseau en temps réel pour détecter les activités malveillantes.  
- **Configuration :**  
  - Installer Suricata sur le serveur web.  
  - Configurer des règles pour détecter les attaques courantes (exemple : scans de ports, tentatives d'exploitation de vulnérabilités).  
  - Intégrer Suricata avec Prometheus pour collecter et visualiser les alertes dans Grafana.  

#### **b. Déploiement d'un WAF (Web Application Firewall)**  
- **Rôle :** Un WAF protège les applications web contre les attaques courantes telles que les injections SQL, les XSS, etc.  
- **Configuration :**  
  - Utiliser un WAF open source comme **ModSecurity** avec **Nginx** ou **Apache**.  
  - Configurer des règles pour bloquer les requêtes malveillantes.  
  - Surveiller les logs du WAF dans Grafana pour détecter les tentatives d'attaque.  

#### **c. Renforcement de la sécurité du serveur Linux**  
- **Mises à jour régulières :** Appliquer les correctifs de sécurité pour le système d'exploitation et les logiciels installés.  
- **Configuration des pare-feux :** Utiliser **UFW** ou **iptables** pour restreindre l'accès aux ports essentiels (exemple : SSH, HTTP, HTTPS).  
- **Désactivation des services inutiles :** Désactiver les services non utilisés pour réduire la surface d'attaque.  
- **Surveillance des logs :** Configurer **rsyslog** ou **journald** pour centraliser les logs et les intégrer à Prometheus/Grafana.  

---

### **3. Cryptographie pour la protection des données sensibles**  
La cryptographie est essentielle pour protéger les données sensibles, que ce soit en transit ou au repos. Voici les mesures à mettre en place :  

#### **a. Chiffrement des données en transit**  
- **TLS/SSL :**  
  - Configurer TLS/SSL pour toutes les communications entre les clients et le serveur web (HTTPS).  
  - Utiliser des certificats SSL valides et à jour, de préférence avec des algorithmes forts comme ECDSA ou RSA 2048 bits.  
  - Renouveler les certificats avant leur expiration pour éviter les interruptions de service.  
- **VPN :**  
  - Utiliser un VPN pour sécuriser les communications entre les serveurs internes et les utilisateurs distants.  
  - Configurer OpenVPN ou WireGuard avec des clés de chiffrement fortes.  

#### **b. Chiffrement des données au repos**  
- **Chiffrement de disque :**  
  - Utiliser **LUKS** (Linux Unified Key Setup) pour chiffrer les partitions de disque contenant des données sensibles.  
  - Configurer une gestion sécurisée des clés de chiffrement (exemple : stocker les clés dans un HSM - Hardware Security Module).  
- **Chiffrement des bases de données :**  
  - Activer le chiffrement natif des bases de données (exemple : Transparent Data Encryption pour PostgreSQL ou MySQL).  
  - Chiffrer les sauvegardes de bases de données avant de les stocker.  
- **Chiffrement des fichiers sensibles :**  
  - Utiliser des outils comme **GPG** (GNU Privacy Guard) pour chiffrer les fichiers sensibles avant de les envoyer ou de les stocker.  

#### **c. Gestion des clés de chiffrement**  
- **Stockage sécurisé :**  
  - Utiliser un gestionnaire de clés (exemple : HashiCorp Vault) pour stocker et gérer les clés de chiffrement de manière sécurisée.  
  - Limiter l'accès aux clés de chiffrement aux seuls utilisateurs et services autorisés.  
- **Rotation des clés :**  
  - Mettre en place une politique de rotation régulière des clés de chiffrement pour limiter les risques en cas de compromission.  
  - Automatiser la rotation des clés pour éviter les erreurs humaines.  

---

### **4. Politique de sécurité**  
Rédiger une politique de sécurité adaptée aux besoins de l'entreprise, en conformité avec les normes européennes (RGPD, NIS, ISO 27001). Voici les points clés à inclure :  
- **Gestion des accès :** Mettre en place une politique de moindre privilège et utiliser des outils de gestion des identités (IAM).  
- **Sauvegarde des données :** Configurer des sauvegardes régulières et chiffrées des données critiques.  
- **Formation des employés :** Sensibiliser les employés aux bonnes pratiques de sécurité (exemple : détection des phishing).  
- **Plan de réponse aux incidents :** Définir les étapes à suivre en cas de détection d'une attaque LAB-05.  

---

### **5. Simulation de défense**  
Pour tester l'efficacité de la stratégie de défense, réaliser des simulations d'attaques :  
- **Scénarios d'attaque :**  
  - Scanner de ports avec **Nmap**.  
  - Tentative d'injection SQL sur l'application web.  
  - Attaque par force brute sur le serveur SSH.  
- **Vérification des outils :**  
  - Vérifier que Suricata détecte les scans de ports et les attaques réseau.  
  - Vérifier que le WAF bloque les injections SQL et les XSS.  
  - Vérifier que Prometheus et Grafana alertent en cas d'anomalies (exemple : pic de trafic, utilisation CPU élevée).  
- **Amélioration continue :** Ajuster les règles et configurations en fonction des résultats des tests. 
