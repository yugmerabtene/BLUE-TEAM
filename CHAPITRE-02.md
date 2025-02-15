### **Chapitre-02 : Concepts fondamentaux de la Blue Team**

---

#### **Théorie**

##### **1. Principes de base : Confidentialité, intégrité, disponibilité (CIA)**
Le modèle **CIA** est la base de la sécurité de l'information. Il se compose de trois piliers :
- **Confidentialité** : Assurer que les informations ne sont accessibles qu'aux personnes autorisées.
  - Exemple : Chiffrement des données, contrôle d'accès.
- **Intégrité** : Garantir que les données ne sont pas altérées de manière non autorisée.
  - Exemple : Utilisation de signatures numériques, vérification des hashs.
- **Disponibilité** : S'assurer que les systèmes et les données sont accessibles quand nécessaire.
  - Exemple : Redondance des serveurs, plan de reprise après sinistre (PRA).

##### **2. Modèles de sécurité**
- **Défense en profondeur** : Stratégie qui implique la mise en place de plusieurs couches de sécurité pour protéger les actifs. Si une couche échoue, les autres peuvent encore fournir une protection.
  - Exemple : Pare-feu, IDS/IPS, antivirus, formation des utilisateurs.
- **Moindre privilège** : Principe selon lequel les utilisateurs et les systèmes ne devraient avoir que les permissions minimales nécessaires pour accomplir leurs tâches.
  - Exemple : Un employé du service comptable n'a pas besoin d'accéder aux serveurs de développement.
- **Segmentation** : Division d'un réseau en zones distinctes pour limiter la propagation des menaces.
  - Exemple : Séparation des réseaux clients, serveurs et administrateurs.

##### **3. Cycle de vie de la sécurité**
La sécurité est un processus continu qui comprend quatre phases principales :
- **Prévention** : Mettre en place des mesures pour éviter les incidents (pare-feu, correctifs, formation).
- **Détection** : Identifier les activités suspectes ou les violations (surveillance des logs, IDS).
- **Réponse** : Réagir aux incidents pour limiter les dommages (isolement des systèmes infectés, analyse forensique).
- **Récupération** : Restaurer les systèmes et les données après un incident (sauvegardes, tests de restauration).

---

#### **Exercices**

##### **Exercice 1 : Modèle de défense en profondeur**
1. **Expliquez en détail le modèle de défense en profondeur** :
   - Couche 1 : Pare-feu pour filtrer le trafic entrant et sortant.
   - Couche 2 : Système de détection d'intrusion (IDS) pour surveiller le trafic réseau.
   - Couche 3 : Antivirus pour détecter les logiciels malveillants.
   - Couche 4 : Formation des utilisateurs pour prévenir les attaques de phishing.
2. **Donnez un exemple concret d'application de ce modèle dans une entreprise**.

##### **Exercice 2 : Principe de moindre privilège**
1. **Donnez un exemple concret d'application du principe de moindre privilège** :
   - Un développeur n'a pas besoin d'accéder aux données financières de l'entreprise.
   - Un employé du service client n'a pas besoin de droits d'administration sur les serveurs.
2. **Expliquez comment ce principe réduit les risques de sécurité**.

---

#### **Travaux Pratiques (TP)**

##### **TP 1 : Configuration d'un pare-feu (pfSense) et segmentation réseau**
**Objectif** : Configurer un pare-feu pfSense pour segmenter un réseau et appliquer des règles de sécurité.

**Étapes** :
1. **Installez pfSense** :
   - Téléchargez pfSense (https://www.pfsense.org/) et installez-le sur une machine virtuelle ou physique.
   - Configurez les interfaces réseau (WAN, LAN, OPT1 pour un réseau DMZ).
2. **Configurez les règles de pare-feu** :
   - Créez des règles pour autoriser ou bloquer le trafic entre les réseaux.
     - Exemple : Autoriser le trafic HTTP/HTTPS du LAN vers Internet, mais bloquer l'accès au LAN depuis la DMZ.
3. **Segmentez le réseau** :
   - Créez trois réseaux distincts :
     - LAN : Pour les utilisateurs internes.
     - DMZ : Pour les serveurs accessibles depuis Internet (par exemple, un serveur web).
     - WAN : Pour la connexion Internet.
4. **Testez la configuration** :
   - Vérifiez que les règles de pare-feu fonctionnent comme prévu.
   - Utilisez des outils comme `ping` ou `nmap` pour tester la connectivité entre les réseaux.

---

#### **Travaux Dirigés (TD)**

##### **TD 1 : Application des concepts de sécurité**
**Objectif** : Appliquer les concepts de défense en profondeur, moindre privilège et segmentation dans un scénario réel.

**Scénario** :
- Une entreprise dispose d'un réseau interne, d'un serveur web accessible depuis Internet et d'une base de données sensible.

**Étapes** :
1. **Défense en profondeur** :
   - Configurez un pare-feu pour filtrer le trafic.
   - Installez un IDS (par exemple, Suricata) pour surveiller le trafic réseau.
   - Mettez en place un antivirus sur tous les postes de travail.
2. **Moindre privilège** :
   - Limitez les accès à la base de données aux seuls administrateurs.
   - Restreignez les droits des utilisateurs sur le serveur web.
3. **Segmentation** :
   - Isolez le serveur web dans une DMZ.
   - Séparez le réseau interne du réseau de gestion.

---

#### **Outils utilisés dans ce chapitre**
- **pfSense** : Pare-feu open source pour la segmentation et la sécurité réseau.
- **Suricata** : Système de détection d'intrusion (IDS).
- **Nmap** : Outil de scan réseau pour tester la connectivité.
- **Wireshark** : Pour analyser le trafic réseau.

---

#### **Résumé du chapitre**
- Le modèle CIA (Confidentialité, Intégrité, Disponibilité) est la base de la sécurité de l'information.
- Les modèles de sécurité comme la défense en profondeur, le moindre privilège et la segmentation sont essentiels pour protéger les systèmes.
- Le cycle de vie de la sécurité (prévention, détection, réponse, récupération) permet de gérer les risques de manière proactive.
- Les exercices et TP permettent de mettre en pratique ces concepts dans un environnement simulé.
