
![timeseries-prometheus](https://github.com/user-attachments/assets/d0c2fc93-66d8-4080-9703-cbeb0c0e47c8)

## **1. Prérequis**
- Une machine Linux (Ubuntu/Debian recommandé) pour installer **Grafana** et **Morpheus**.
- Un serveur web sous Linux (Apache/Nginx).
- Un serveur FTP sous Windows Server 2019 (IIS FTP ou FileZilla Server).
- Un accès administrateur à toutes les machines.
- Accès à Internet pour installer les packages nécessaires.

---

## **2. Installation de Grafana sur la machine Linux**
Grafana est un outil de visualisation de données qui va nous permettre de surveiller nos serveurs.

### **2.1 Mise à jour du système**
```bash
sudo apt update && sudo apt upgrade -y
```

### **2.2 Installation de Grafana**
Ajout du dépôt Grafana :
```bash
sudo apt install -y software-properties-common
sudo add-apt-repository "deb https://packages.grafana.com/oss/deb stable main"
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
```
Installation de Grafana :
```bash
sudo apt update
sudo apt install grafana -y
```

### **2.3 Démarrage et activation du service**
```bash
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

### **2.4 Accès à Grafana**
Grafana fonctionne sur le port **3000**. Ouvrez un navigateur et accédez à :
```
http://<IP_DE_LA_MACHINE>:3000
```
Identifiants par défaut :
- **User** : admin
- **Password** : admin (à changer immédiatement)

---

## **3. Installation de Prometheus pour la collecte des métriques**
Grafana utilise **Prometheus** pour récupérer les métriques des serveurs.

### **3.1 Téléchargement et installation**
```bash
cd /usr/local/bin
wget https://github.com/prometheus/prometheus/releases/latest/download/prometheus-linux-amd64.tar.gz
tar -xvzf prometheus-linux-amd64.tar.gz
cd prometheus-*
```

### **3.2 Création d'un fichier de configuration**
```bash
sudo nano /etc/prometheus/prometheus.yml
```
Ajoutez :
```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: "linux-server"
    static_configs:
      - targets: ["<IP_SERVEUR_LINUX>:9100"]

  - job_name: "windows-server"
    static_configs:
      - targets: ["<IP_WINDOWS_SERVER>:9182"]
```

### **3.3 Création du service systemd**
```bash
sudo nano /etc/systemd/system/prometheus.service
```
Ajoutez :
```ini
[Unit]
Description=Prometheus
After=network.target

[Service]
User=root
ExecStart=/usr/local/bin/prometheus --config.file=/etc/prometheus/prometheus.yml
Restart=always

[Install]
WantedBy=multi-user.target
```

Rechargez les services :
```bash
sudo systemctl daemon-reload
sudo systemctl enable prometheus
sudo systemctl start prometheus
```

---

## **4. Installation des Exporters pour la collecte des métriques**
### **4.1 Installation de Node Exporter (Linux)**
Sur le **serveur web Linux** :
```bash
cd /usr/local/bin
wget https://github.com/prometheus/node_exporter/releases/latest/download/node_exporter-linux-amd64.tar.gz
tar -xvzf node_exporter-linux-amd64.tar.gz
./node_exporter &
```

Vérifiez avec :
```bash
curl http://localhost:9100/metrics
```

### **4.2 Installation de Windows Exporter (Windows Server 2019)**
Sur **Windows Server 2019** :
1. Téléchargez **Windows Exporter** depuis [GitHub](https://github.com/prometheus-community/windows_exporter/releases).
2. Installez-le avec :
   ```powershell
   windows_exporter.exe --install
   ```
3. Vérifiez qu’il fonctionne :
   ```powershell
   curl http://localhost:9182/metrics
   ```

---

## **5. Installation et configuration de Morpheus**
Morpheus est une plateforme de gestion cloud qui peut collecter et analyser les métriques.

### **5.1 Installation de Docker**
Morpheus peut être installé avec Docker :
```bash
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
```

### **5.2 Installation de Morpheus**
Téléchargez et installez Morpheus avec Docker :
```bash
docker run -d --name morpheus -p 80:80 -p 443:443 morpheushub/morpheus
```

### **5.3 Accès à Morpheus**
Ouvrez un navigateur et accédez à :
```
http://<IP_DE_LA_MACHINE>
```
Suivez les instructions pour finaliser l’installation.

---

## **6. Configuration de Grafana pour afficher les métriques**
1. **Ajout de Prometheus comme source de données** :
   - Dans Grafana, allez dans **Configuration → Data Sources**.
   - Cliquez sur **Add Data Source**.
   - Sélectionnez **Prometheus**.
   - Entrez l’URL de Prometheus : `http://localhost:9090`.
   - Cliquez sur **Save & Test**.

2. **Création de tableaux de bord** :
   - Allez dans **Dashboards** et cliquez sur **Import**.
   - Utilisez l’ID **1860** pour un dashboard Linux et **2129** pour Windows.

---

## **7. Vérification**
- Allez sur **Grafana** et vérifiez que les données de vos serveurs apparaissent.
- Testez l’accès aux métriques en allant sur :
  ```
  http://<IP_DE_LA_MACHINE>:9090
  ```
- Vérifiez que les exporters sont bien actifs sur chaque machine.
