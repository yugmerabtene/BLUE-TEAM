### **Chapitre 4 : Méthodes et outils utilisés par la Blue Team**

---

#### **Théorie**

##### **1. Méthodes utilisées par la Blue Team**
La Blue Team utilise plusieurs méthodes pour protéger les systèmes et détecter les menaces. Voici les principales :

- **Analyse des logs** :
  - Examen des logs système, réseau et applicatifs pour identifier des activités suspectes.
  - Les logs peuvent provenir de pare-feu, serveurs, routeurs, etc.
  - Objectif : Détecter les anomalies, les tentatives d'intrusion ou les comportements malveillants.

- **Chasse aux menaces (Threat Hunting)** :
  - Processus proactif de recherche de menaces qui n'ont pas été détectées par les outils automatisés.
  - Utilisation de techniques avancées pour identifier les attaques sophistiquées (APT, malware persistant).
  - Objectif : Découvrir et neutraliser les menaces avant qu'elles ne causent des dommages.

- **Analyse forensique** :
  - Investigation approfondie après un incident pour comprendre ce qui s'est passé.
  - Collecte et analyse des preuves numériques (fichiers, logs, mémoire RAM).
  - Objectif : Identifier la cause de l'incident, les systèmes compromis et les données affectées.

##### **2. Outils utilisés par la Blue Team**
Les outils sont essentiels pour mettre en œuvre les méthodes de la Blue Team. Voici quelques-uns des outils les plus couramment utilisés :

- **SIEM (Security Information and Event Management)** :
  - Outils : Splunk, ELK Stack (Elasticsearch, Logstash, Kibana), QRadar.
  - Fonction : Collecte, corrèle et analyse les logs en temps réel pour détecter les menaces.

- **IDS/IPS (Intrusion Detection System/Intrusion Prevention System)** :
  - Outils : Snort, Suricata.
  - Fonction : Surveille le trafic réseau pour détecter et bloquer les activités malveillantes.

- **Antivirus/EDR (Endpoint Detection and Response)** :
  - Outils : CrowdStrike, Windows Defender, McAfee.
  - Fonction : Protège les endpoints (postes de travail, serveurs) contre les logiciels malveillants.

---

#### **Exercices**

##### **Exercice 1 : Comparaison de deux outils SIEM**
1. **Comparez Splunk et ELK Stack** :
   - **Splunk** :
     - Avantages : Interface utilisateur intuitive, intégrations étendues, support professionnel.
     - Inconvénients : Coût élevé pour les grandes organisations.
   - **ELK Stack** :
     - Avantages : Open source, personnalisable, évolutif.
     - Inconvénients : Configuration complexe, nécessite des compétences techniques.
2. **Quel outil choisiriez-vous pour une petite entreprise ? Pour une grande entreprise ? Justifiez votre choix.**

##### **Exercice 2 : Fonctionnement d'un IDS comme Snort**
1. **Expliquez le fonctionnement de Snort** :
   - Snort est un IDS open source qui analyse le trafic réseau en temps réel.
   - Il utilise des règles pour détecter des activités suspectes (par exemple, des scans de ports, des tentatives d'exploitation de vulnérabilités).
   - Exemple de règle : `alert tcp any any -> 192.168.1.0/24 80 (msg:"Attempted HTTP access"; sid:1000001;)`.
2. **Donnez un exemple de règle Snort pour détecter une tentative de connexion SSH non autorisée.**

---

#### **Travaux Pratiques (TP)**

##### **TP 1 : Installation et configuration d'un SIEM (ELK Stack)**
**Objectif** : Installer et configurer un SIEM basé sur ELK Stack pour surveiller un réseau virtuel.

**Étapes** :
1. **Installez Elasticsearch, Logstash et Kibana** :
   - Sur un serveur Linux (par exemple, Ubuntu), installez les composants ELK Stack :
     ```bash
     # Installer Elasticsearch
     wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
     sudo apt-get install apt-transport-https
     echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
     sudo apt-get update && sudo apt-get install elasticsearch

     # Installer Logstash
     sudo apt-get install logstash

     # Installer Kibana
     sudo apt-get install kibana
     ```
   - Configurez Elasticsearch et Kibana pour démarrer au boot :
     ```bash
     sudo systemctl enable elasticsearch
     sudo systemctl enable kibana
     ```

2. **Configurez Logstash pour collecter les logs** :
   - Créez un fichier de configuration Logstash (`/etc/logstash/conf.d/logstash.conf`) :
     ```plaintext
     input {
       beats {
         port => 5044
       }
     }
     output {
       elasticsearch {
         hosts => ["localhost:9200"]
       }
     }
     ```

3. **Installez et configurez Filebeat** :
   - Filebeat est un agent léger qui envoie les logs à Logstash.
   - Installez Filebeat sur les machines à surveiller :
     ```bash
     sudo apt-get install filebeat
     ```
   - Configurez Filebeat pour envoyer les logs système à Logstash :
     ```bash
     sudo nano /etc/filebeat/filebeat.yml
     ```
     Modifiez la configuration :
     ```yaml
     output.logstash:
       hosts: ["localhost:5044"]
     ```

4. **Visualisez les logs dans Kibana** :
   - Accédez à Kibana via un navigateur web (`http://<adresse_ip>:5601`).
   - Créez un index pattern pour visualiser les logs collectés.

5. **Testez la surveillance** :
   - Générez des logs sur les machines surveillées (par exemple, accédez à un serveur web).
   - Vérifiez que les logs apparaissent dans Kibana.

---

#### **Travaux Dirigés (TD)**

##### **TD 1 : Analyse des logs avec ELK Stack**
**Objectif** : Utiliser ELK Stack pour analyser les logs d'un réseau virtuel et détecter des activités suspectes.

**Scénario** :
- Un serveur web est victime de tentatives d'accès non autorisées.

**Étapes** :
1. **Collectez les logs** :
   - Utilisez Filebeat pour envoyer les logs Apache ou Nginx à Logstash.
2. **Analysez les logs dans Kibana** :
   - Recherchez des tentatives d'accès répétées à des URLs sensibles.
   - Identifiez les adresses IP suspectes.
3. **Créez des visualisations** :
   - Utilisez Kibana pour créer des graphiques montrant les tentatives d'accès par IP.
4. **Générez un rapport** :
   - Documentez les activités suspectes et proposez des mesures de mitigation.

---

#### **Outils utilisés dans ce chapitre**
- **ELK Stack (Elasticsearch, Logstash, Kibana)** : Pour la collecte, l'analyse et la visualisation des logs.
- **Snort** : IDS open source pour la détection d'intrusions.
- **Filebeat** : Agent léger pour la collecte de logs.
- **VirtualBox/VMware** : Pour créer un réseau virtuel.

---

#### **Résumé du chapitre**
- La Blue Team utilise des méthodes comme l'analyse des logs, la chasse aux menaces et l'analyse forensique pour protéger les systèmes.
- Les outils comme les SIEM (Splunk, ELK Stack), les IDS/IPS (Snort, Suricata) et les antivirus (CrowdStrike) sont essentiels pour détecter et répondre aux menaces.
- Les exercices et TP permettent de mettre en pratique ces méthodes et outils dans un environnement simulé.
