### **Lab 04 : Stratégie de défense (Blue Team)**

L'objectif de ce lab est de mettre en place une stratégie de défense robuste pour protéger l'infrastructure contre les attaques futures. Voici les étapes à suivre, en utilisant **Grafana** et **Prometheus** comme outils principaux de surveillance, ainsi que des mesures de sécurité supplémentaires pour le serveur web Linux et le serveur Windows Server 2019, y compris une section sur la **cryptographie** pour protéger les données sensibles.

---

### **1. Mise en place d'outils de détection et de surveillance**

Pour surveiller et détecter les activités suspectes, nous allons déployer une stack de monitoring basée sur **Prometheus** (pour la collecte de métriques) et **Grafana** (pour la visualisation et l'analyse des données). **Grafana et Prometheus seront installés sur un serveur dédié** pour surveiller à la fois le **serveur web Linux** et le **serveur FTP Windows Server 2019**.

#### **a. Installation de Prometheus**

- **Rôle :** Prometheus est un système de surveillance et d'alerte open source qui collecte des métriques à partir de diverses sources (serveurs, applications, etc.).
- **Configuration :**
  - Installer Prometheus sur un serveur dédié pour éviter les conflits de ressources.
  - Configurer les **exporters** pour collecter les métriques des serveurs (exemple : Node Exporter pour les métriques système Linux, WMI Exporter pour Windows).
  - Définir des **alertes** dans Prometheus pour détecter les anomalies (exemple : utilisation CPU élevée, trafic réseau suspect).

#### **b. Installation de Grafana**

- **Rôle :** Grafana est un outil de visualisation de données qui permet de créer des tableaux de bord pour surveiller les métriques collectées par Prometheus.
- **Configuration :**
  - Installer Grafana sur un serveur dédié pour des raisons de performance et de sécurité.
  - Configurer Grafana pour se connecter à Prometheus en tant que source de données.
  - Créer des tableaux de bord pour surveiller :
    - L'utilisation des ressources (CPU, mémoire, disque) des serveurs Linux et Windows.
    - Le trafic réseau.
    - Les logs d'accès au serveur web.
  - Configurer des alertes dans Grafana pour notifier l'équipe en cas d'activité suspecte.

#### **c. Sécurisation des serveurs Prometheus et Grafana**

- **Authentification forte :** Utiliser des mots de passe complexes et activer l'authentification à deux facteurs (2FA) pour Grafana.
- **Chiffrement :** Configurer HTTPS pour sécuriser les communications entre les utilisateurs et Grafana/Prometheus.
- **Restriction d'accès :** Limiter l'accès aux serveurs Prometheus et Grafana à certaines adresses IP ou réseaux autorisés.

---

### **2. Mise en place d'un Honeypot pour la détection des menaces**

Un **honeypot** est un système de piège permettant de détecter les tentatives d'intrusion en attirant les attaquants vers un faux serveur vulnérable. Nous allons utiliser **Cowrie**, un honeypot spécialisé dans l'émulation de connexions SSH et Telnet.

#### **a. Installation de Cowrie**

1. **Prérequis :**
   - Un serveur Linux avec Python 3.7 ou supérieur.
   - Un utilisateur non privilégié pour exécuter Cowrie.

2. **Installation :**
   ```bash
   sudo apt update
   sudo apt install git python3-venv python3-pip
   git clone https://github.com/cowrie/cowrie.git
   cd cowrie
   python3 -m venv cowrie-env
   source cowrie-env/bin/activate
   pip install --upgrade pip
   pip install -r requirements.txt
   ```

3. **Configuration :**
   - Modifier le fichier `cowrie.cfg` pour configurer les ports d'écoute SSH et Telnet.
   - Démarrer Cowrie :
     ```bash
     ./bin/cowrie start
     ```

4. **Surveillance :**
   - Les logs de Cowrie sont stockés dans le répertoire `var/log/cowrie/`.
   - Intégrer les logs dans Grafana pour une surveillance centralisée.

---

### **3. Sécurisation avancée du serveur web Linux**

Pour protéger le serveur web, nous allons ajouter plusieurs couches de sécurité :

#### **a. Installation de Fail2Ban**

Fail2Ban surveille les tentatives de connexion répétées et bloque automatiquement les adresses IP suspectes.

1. **Installation de Fail2Ban :**
   ```bash
   sudo apt install fail2ban -y
   ```
2. **Configuration :**
   - Modifier le fichier `/etc/fail2ban/jail.conf` et activer la protection pour SSH et Apache/Nginx.
   - Redémarrer le service :
     ```bash
     sudo systemctl restart fail2ban
     ```

#### **b. Installation d'un IPS/IDS : Suricata**

Suricata est un système de détection et de prévention des intrusions.

1. **Installation de Suricata :**
   ```bash
   sudo apt install suricata -y
   ```
2. **Configuration des règles :**
   - Modifier le fichier `/etc/suricata/suricata.yaml` pour activer les règles de détection des attaques.
   - Redémarrer Suricata :
     ```bash
     sudo systemctl restart suricata
     ```

#### **c. Installation d'un WAF : ModSecurity**

ModSecurity protège les applications web contre les attaques courantes.

1. **Installation de ModSecurity avec Nginx :**
   ```bash
   sudo apt install libnginx-mod-security -y
   ```
2. **Configuration :**
   - Activer ModSecurity dans la configuration de Nginx.
   - Charger les règles OWASP ModSecurity Core Rule Set (CRS).
   - Redémarrer Nginx :
     ```bash
     sudo systemctl restart nginx
     ```

---

### **4. Politique de sécurité des données sensibles**

#### **a. Cryptographie pour protéger les données sensibles**

1. **Chiffrement des données au repos :**
   - Utiliser **LUKS** pour chiffrer les disques sur le serveur Linux.
   - Configurer **BitLocker** pour chiffrer les disques sur le serveur Windows Server 2019.

2. **Chiffrement des données en transit :**
   - Configurer **TLS/SSL** pour sécuriser les communications entre les serveurs et les clients.
   - Utiliser des certificats SSL valides et les renouveler régulièrement.

3. **Gestion des clés de chiffrement :**
   - Utiliser un **HSM (Hardware Security Module)** ou un service de gestion des clés comme **AWS KMS** pour stocker et gérer les clés de chiffrement de manière sécurisée.

---

### **5. Simulation d'attaques et validation du système**

Pour valider l'efficacité des mesures de sécurité mises en place, nous allons simuler des attaques et vérifier que les outils de détection et de protection fonctionnent correctement.

#### **a. Simulation d'une attaque brute force SSH**

1. **Utiliser un outil comme Hydra pour simuler une attaque brute force :**
   ```bash
   hydra -l utilisateur -P wordlist.txt ssh://<adresse_ip_serveur>
   ```
2. **Vérifier que Fail2Ban détecte et bloque l'adresse IP de l'attaquant.**

#### **b. Simulation d'une attaque web (SQL Injection)**

1. **Utiliser un outil comme SQLmap pour tester la vulnérabilité du serveur web :**
   ```bash
   sqlmap -u http://<adresse_ip_serveur>/page_vulnérable --dbs
   ```
2. **Vérifier que ModSecurity détecte et bloque l'attaque.**

#### **c. Simulation d'une attaque réseau (DDoS)**

1. **Utiliser un outil comme hping3 pour simuler une attaque DDoS :**
   ```bash
   hping3 -S --flood -p 80 <adresse_ip_serveur>
   ```
2. **Vérifier que Suricata détecte l'attaque et que les alertes sont visibles dans Grafana.**

---

### **6. Conclusion**

Avec cette architecture, nous avons mis en place une stratégie de **Blue Team** complète intégrant :\
✅ **Surveillance avancée avec Prometheus et Grafana.**\
✅ **Détection proactive avec un honeypot Cowrie.**\
✅ **Sécurisation renforcée des services web et réseau avec Fail2Ban, Suricata et ModSecurity.**\
✅ **Protection des serveurs Linux et Windows.**\
✅ **Cryptographie pour protéger les données sensibles.**\
✅ **Plan de réponse aux incidents en cas de menace détectée LAB-05.**
