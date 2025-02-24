### Préambule : Pourquoi Suricata et ModSecurity ?
Avant de plonger dans la procédure, comprenons l’utilité de ces outils et pourquoi ils se complètent bien pour sécuriser un serveur web :

- **Suricata (IDS/IPS)** :
  - **Rôle** : Suricata est un système de détection (IDS) et de prévention (IPS) des intrusions au niveau réseau. Il analyse tout le trafic qui passe par une interface réseau (pas seulement HTTP) et détecte des comportements suspects comme des scans de ports, des exploits réseau, ou des malwares.
  - **Utilité** : En mode IDS, il alerte sur les menaces ; en mode IPS, il bloque activement les paquets malveillants avant qu’ils n’atteignent ton serveur. C’est une première ligne de défense contre les attaques réseau.
  - **Exemple** : Il peut bloquer une tentative de connexion SSH brute force ou un exploit ciblant une vulnérabilité réseau.

- **ModSecurity (WAF)** :
  - **Rôle** : ModSecurity est un pare-feu applicatif web (WAF) qui s’intègre à ton serveur web (Apache, Nginx, etc.). Il inspecte spécifiquement les requêtes HTTP/HTTPS pour protéger ton application web.
  - **Utilité** : Il bloque les attaques au niveau applicatif, comme les injections SQL, les scripts intersites (XSS), ou les tentatives d’exploitation de failles dans ton code. C’est une défense ciblée pour ton site ou application.
  - **Exemple** : Il peut arrêter une requête malveillante comme `GET /page.php?id=1; DROP TABLE users`.

- **Complémentarité** : Suricata agit comme un bouclier réseau global, tandis que ModSecurity protège spécifiquement ton application web. Ensemble, ils couvrent les menaces réseau et applicatives, offrant une défense en profondeur.

---

### Procédure d’installation et configuration

#### Hypothèses
- **Serveur web** : Une machine avec Apache ou Nginx, où ModSecurity sera installé.
- **Serveur IDS/IPS** : Une machine séparée (ou la même si ressources suffisantes) pour Suricata.
- **Système** : Ubuntu/Debian (ajuste si tu utilises une autre distribution).
- **Réseau** : Le serveur IDS/IPS est en amont ou reçoit une copie du trafic (miroir SPAN).

---

### 1. Installer et configurer Suricata (IDS/IPS)
#### Étape 1 : Installation
Sur le serveur dédié à Suricata :
```bash
sudo apt update
sudo apt install suricata -y
```

#### Étape 2 : Mettre à jour les règles
Suricata utilise des règles pour détecter les menaces. Télécharge les règles communautaires (Emerging Threats) :
```bash
sudo suricata-update
```
Cela place les règles dans `/var/lib/suricata/rules/`.

#### Étape 3 : Configurer Suricata
Édite le fichier de configuration principal :
```bash
sudo nano /etc/suricata/suricata.yaml
```
Modifie ces sections clés :
- **Interface réseau** : Indique l’interface à surveiller (ex. `eth0`) :
  ```yaml
  af-packet:
    - interface: eth0
      threads: auto
      cluster-type: cluster_flow
      cluster-id: 99
  ```
- **Mode IPS (optionnel)** : Si tu veux bloquer le trafic (et pas juste alerter), utilise `nfqueue` :
  ```yaml
  nfqueue:
    - queue-num: 0
  ```
- **Règles actives** : Vérifie que les règles sont incluses :
  ```yaml
  rule-files:
    - /var/lib/suricata/rules/*.rules
  ```

#### Étape 4 : Configurer le réseau pour l’IPS (si mode actif)
Pour que Suricata bloque le trafic, intègre-le à `iptables` :
```bash
sudo iptables -I FORWARD -j NFQUEUE --queue-num 0
sudo iptables -I INPUT -j NFQUEUE --queue-num 0
```
Puis lance Suricata en mode IPS :
```bash
sudo suricata -c /etc/suricata/suricata.yaml -q 0
```
(Si mode IDS seulement, utilise `-i eth0` à la place de `-q 0`.)

#### Étape 5 : Tester Suricata
- Vérifie qu’il fonctionne :
  ```bash
  sudo tail -f /var/log/suricata/fast.log
  ```
- Génère du trafic suspect (ex. : `nmap -sS ton_ip`) et regarde si des alertes apparaissent.

#### Étape 6 : Lancer au démarrage
Active le service :
```bash
sudo systemctl enable suricata
sudo systemctl start suricata
```

---

### 2. Installer et configurer ModSecurity (WAF)
#### Étape 1 : Installation sur le serveur web
Pour Apache :
```bash
sudo apt update
sudo apt install libapache2-mod-security2 -y
```
Pour Nginx, il faut compiler Nginx avec le module ModSecurity (plus complexe, dis-moi si tu utilises Nginx).

#### Étape 2 : Activer ModSecurity
- Copie le fichier de configuration par défaut :
  ```bash
  sudo cp /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf
  ```
- Édite `/etc/modsecurity/modsecurity.conf` :
  ```bash
  sudo nano /etc/modsecurity/modsecurity.conf
  ```
  Change `SecRuleEngine DetectionOnly` en :
  ```bash
  SecRuleEngine On
  ```
  Cela active le mode blocage.

#### Étape 3 : Ajouter les règles OWASP
Télécharge le Core Rule Set (CRS) d’OWASP :
```bash
sudo git clone https://github.com/coreruleset/coreruleset /usr/local/modsecurity/crs
sudo mv /usr/local/modsecurity/crs/crs-setup.conf.example /usr/local/modsecurity/crs/crs-setup.conf
```
Ajoute les règles au fichier de configuration d’Apache :
```bash
sudo nano /etc/apache2/mods-enabled/security2.conf
```
Ajoute ceci avant la balise `</IfModule>` :
```apache
IncludeOptional /usr/local/modsecurity/crs/crs-setup.conf
IncludeOptional /usr/local/modsecurity/crs/rules/*.conf
```

#### Étape 4 : Redémarrer Apache
```bash
sudo systemctl restart apache2
```

#### Étape 5 : Tester ModSecurity
- Vérifie les logs :
  ```bash
  sudo tail -f /var/log/apache2/modsec_audit.log
  ```
- Teste une attaque (ex. : `curl "http://ton_serveur/?id=1; DROP TABLE users"`) et confirme qu’elle est bloquée (erreur 403).

---

### 3. Intégration et tests finaux
- **Réseau** : Assure-toi que le trafic passe d’abord par le serveur Suricata (IPS) avant d’atteindre le serveur web avec ModSecurity.
- **Simulation** :
  - Attaque réseau : Lance un scan `nmap` ou un outil comme `hping3` pour tester Suricata.
  - Attaque web : Utilise `curl` ou un outil comme `sqlmap` pour tester ModSecurity.
- **Ajustements** : Si trop de faux positifs, ajuste les règles dans `suricata.yaml` ou désactive certaines règles OWASP dans `/usr/local/modsecurity/crs/rules/`.
