
# ** Comprendre et Installer un Honeypot en Cybersécurité**  

## **1. Introduction aux Honeypots**  

### **1.1 Définition d’un Honeypot**  
Un **honeypot** est un système informatique conçu pour attirer et piéger les cyberattaquants en simulant des vulnérabilités. Il permet d'analyser leurs comportements et de renforcer la sécurité des réseaux.  

### **1.2 Objectifs d’un Honeypot**  
- **Détection des attaques** : Identifier les attaques avant qu'elles ne touchent les vrais systèmes.  
- **Analyse des méthodes des attaquants** : Comprendre les techniques utilisées par les cybercriminels.  
- **Leurres pour détourner les attaques** : Réduire les risques pour les systèmes réels.  

### **1.3 Types de Honeypots**  
1. **Low-Interaction** : Simule uniquement certains services (ex : ports ouverts, bannières falsifiées). Peu de risque, mais moins réaliste.  
2. **High-Interaction** : Un vrai système avec des vulnérabilités simulées. Plus réaliste, mais risque élevé si mal isolé.  
3. **Honeynets** : Réseaux complets de honeypots permettant d'analyser des attaques à grande échelle.  

---

## **2. Outils Populaires pour les Honeypots**  
- **Cowrie** : Simule un serveur SSH/Telnet vulnérable.  
- **Dionaea** : Capture les malwares et imite des services comme SMB, FTP.  
- **Kippo** : Simule des connexions SSH avec enregistrement des sessions attaquantes.  
- **Honeyd** : Crée des machines virtuelles pour imiter un réseau complet.  

---

## **3. Tutoriel : Installer un Honeypot sur une Machine Linux**  

### **3.1 Prérequis**  
- Une machine **Linux** (Ubuntu/Debian recommandé).  
- Un accès root ou sudo.  
- Un réseau isolé ou un environnement sécurisé (machine virtuelle, VPS, Raspberry Pi).  

---

### **3.2 Installation de Cowrie (Honeypot SSH/Telnet)**  

**Cowrie** est l'un des honeypots les plus populaires pour capturer les attaques SSH et Telnet.  

#### **3.2.1 Mise à jour du système**  
```bash
sudo apt update && sudo apt upgrade -y
```

#### **3.2.2 Installation des dépendances**  
```bash
sudo apt install -y python3 python3-pip virtualenv git
```

#### **3.2.3 Téléchargement de Cowrie**  
```bash
cd /opt
sudo git clone https://github.com/cowrie/cowrie.git
cd cowrie
```

#### **3.2.4 Configuration de l’environnement Python**  
```bash
sudo useradd -m -s /bin/bash cowrie
sudo chown -R cowrie:cowrie /opt/cowrie
sudo -u cowrie -H bash -c "cd /opt/cowrie && virtualenv cowrie-env && source cowrie-env/bin/activate && pip install --upgrade pip && pip install -r requirements.txt"
```

#### **3.2.5 Configuration de Cowrie**  
Copiez le fichier de configuration par défaut :  
```bash
cd /opt/cowrie
cp cowrie.cfg.dist cowrie.cfg
nano cowrie.cfg
```
Modifiez les paramètres suivants :  
- **Port SSH/Telnet** (par défaut 2222 pour éviter les conflits avec le vrai SSH).  
- **Logging** pour capturer les sessions des attaquants.  

---

### **3.3 Lancer et Activer Cowrie**  

#### **3.3.1 Démarrer Cowrie**  
```bash
sudo -u cowrie -H bash -c "cd /opt/cowrie && source cowrie-env/bin/activate && bin/cowrie start"
```

#### **3.3.2 Vérifier que Cowrie fonctionne**  
```bash
sudo tail -f /opt/cowrie/log/cowrie.log
```

#### **3.3.3 Activer Cowrie au démarrage**  
Ajoutez ce script à **systemd** :  
```bash
sudo nano /etc/systemd/system/cowrie.service
```
Ajoutez :  
```ini
[Unit]
Description=Cowrie Honeypot
After=network.target

[Service]
Type=simple
User=cowrie
ExecStart=/opt/cowrie/bin/cowrie start
ExecStop=/opt/cowrie/bin/cowrie stop
Restart=always

[Install]
WantedBy=multi-user.target
```

Rechargez et activez le service :  
```bash
sudo systemctl daemon-reload
sudo systemctl enable cowrie
sudo systemctl start cowrie
```

---

### **3.4 Vérification et Analyse des Attaques**  
1. **Vérifier les connexions suspectes** :  
   ```bash
   sudo cat /opt/cowrie/log/cowrie.log | grep "login attempt"
   ```
2. **Observer les logs en temps réel** :  
   ```bash
   sudo tail -f /opt/cowrie/log/cowrie.log
   ```
3. **Capturer les fichiers envoyés par les attaquants** :  
   ```bash
   ls /opt/cowrie/downloads/
   ```

---

### **3.5 Sécurisation du Honeypot**  
Un honeypot peut être **dangereux** s’il est compromis. Voici des **bonnes pratiques** :  
- **Exécuter Cowrie dans une machine virtuelle** ou un environnement isolé.  
- **Ne pas exécuter en tant que root** pour limiter les risques.  
- **Surveiller régulièrement les logs** pour éviter une compromission.  
- **Utiliser un pare-feu** pour contrôler l’accès :  
  ```bash
  sudo ufw allow 2222/tcp
  ```

---

## **4. Visualisation et Analyse des Données**  
Pour analyser les attaques plus facilement, vous pouvez envoyer les logs de Cowrie vers **ELK (Elasticsearch, Logstash, Kibana)** ou **Splunk**.

### **4.1 Installation de Kibana pour visualiser les attaques**
1. **Ajoutez le dépôt Elasticsearch :**  
   ```bash
   wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
   echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-7.x.list
   sudo apt update
   ```
2. **Installez Kibana et Elasticsearch**  
   ```bash
   sudo apt install -y elasticsearch kibana
   ```
3. **Démarrez les services**  
   ```bash
   sudo systemctl start elasticsearch
   sudo systemctl enable elasticsearch
   sudo systemctl start kibana
   sudo systemctl enable kibana
   ```

---

## **5. Conclusion**  
Un honeypot est un **outil puissant** pour détecter et analyser les attaques informatiques. Avec **Cowrie**, vous pouvez capturer des attaques SSH et Telnet, et avec des outils comme **Kibana**, vous pouvez analyser les données efficacement.  

🔹 **Avantages d’un Honeypot**  
✅ Détection précoce des menaces.  
✅ Analyse approfondie des techniques des hackers.  
✅ Protection des infrastructures critiques.  

🔹 **Inconvénients et Précautions**  
⚠️ Un honeypot mal configuré peut être une porte d’entrée pour les attaquants.  
⚠️ Toujours l’installer sur un réseau **isolé** ou une **machine virtuelle**.  
