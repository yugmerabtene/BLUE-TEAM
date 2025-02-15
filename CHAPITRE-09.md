### Chapitre-09 **Défense des réseaux**

---

#### **Introduction**
La défense des réseaux est un aspect crucial de la cybersécurité. Elle consiste à protéger les infrastructures réseau contre les attaques, les intrusions et les accès non autorisés. Ce chapitre aborde les techniques et outils essentiels pour sécuriser un réseau, notamment les pare-feu, la segmentation, les VPN, ainsi que les méthodes de surveillance comme NetFlow et l'analyse de paquets avec Wireshark.

---

### **Partie Théorique**

#### **1. Techniques de défense des réseaux**

##### **1.1 Pare-feu (Firewall)**
Un pare-feu est un système de sécurité qui contrôle les flux de données entrant et sortant d'un réseau en fonction de règles prédéfinies. Il agit comme une barrière entre un réseau interne fiable et un réseau externe non fiable (comme Internet).

- **Types de pare-feu** :
  - **Pare-feu réseau** : Protège un réseau entier.
  - **Pare-feu applicatif** : Filtre le trafic au niveau des applications.
  - **Pare-feu personnel** : Installé sur un ordinateur individuel.

- **Fonctionnalités** :
  - Filtrage de paquets.
  - Inspection stateful (suivi des connexions).
  - Prévention des intrusions (IDS/IPS intégrés).

##### **1.2 Segmentation réseau**
La segmentation consiste à diviser un réseau en sous-réseaux (ou segments) pour limiter la propagation des attaques et améliorer la gestion du trafic.

- **Avantages** :
  - Isolation des zones critiques (ex : serveurs, bases de données).
  - Réduction de la surface d'attaque.
  - Meilleure performance réseau.

- **Techniques** :
  - VLAN (Virtual LAN).
  - Sous-réseaux IP.

##### **1.3 VPN (Réseau Privé Virtuel)**
Un VPN permet de créer une connexion sécurisée et cryptée entre deux points sur un réseau public (comme Internet). Il est utilisé pour protéger la confidentialité et l'intégrité des données.

- **Types de VPN** :
  - **VPN d'accès distant** : Pour les utilisateurs distants.
  - **VPN site à site** : Pour connecter deux réseaux distants.

- **Protocoles courants** :
  - IPsec.
  - OpenVPN.
  - SSL/TLS.

---

#### **2. Surveillance réseau**

##### **2.1 NetFlow**
NetFlow est un protocole développé par Cisco pour collecter et analyser le trafic réseau. Il permet de surveiller les flux de données et de détecter des anomalies.

- **Utilisations** :
  - Analyse du trafic réseau.
  - Détection d'activités suspectes.
  - Planification de la capacité réseau.

##### **2.2 Analyse de paquets avec Wireshark**
Wireshark est un outil open-source d'analyse de paquets. Il permet de capturer et d'inspecter le trafic réseau en temps réel.

- **Fonctionnalités** :
  - Capture de paquets.
  - Filtrage et analyse détaillée.
  - Détection de problèmes réseau (ex : latence, erreurs).

- **Cas d'utilisation** :
  - Dépannage réseau.
  - Investigation de sécurité.
  - Analyse des protocoles.

---

### **Partie Pratique**

#### **Exercice 1 : Configuration d'un VPN sur un routeur**
**Objectif** : Configurer un VPN site à site entre deux routeurs pour sécuriser les communications.

**Étapes** :
1. Accéder à l'interface de configuration du routeur (via SSH ou console).
2. Configurer les paramètres IPsec :
   - Définir les clés pré-partagées.
   - Configurer les politiques de sécurité.
3. Activer le VPN sur les interfaces concernées.
4. Tester la connectivité entre les deux réseaux.

**Outils** :
- Routeurs compatibles VPN (ex : Cisco, MikroTik).
- Logiciel de gestion de routeur (ex : Cisco IOS).

---

#### **Exercice 2 : Analyse d'un fichier PCAP avec Wireshark**
**Objectif** : Analyser un fichier PCAP pour identifier des activités suspectes ou des problèmes réseau.

**Étapes** :
1. Ouvrir Wireshark et charger le fichier PCAP.
2. Utiliser les filtres pour isoler des paquets spécifiques (ex : `tcp.port == 80`).
3. Inspecter les en-têtes des paquets pour comprendre le trafic.
4. Identifier des anomalies (ex : paquets malformés, trafic non autorisé).

**Exemple de filtres** :
- `ip.src == 192.168.1.1` : Affiche le trafic provenant d'une IP spécifique.
- `http` : Filtre le trafic HTTP.

---

### **Travaux Pratiques (TP)**

#### **TP : Mise en place d'un pare-feu et surveillance du trafic réseau**
**Objectif** : Installer et configurer un pare-feu, puis surveiller le trafic réseau pour détecter des activités suspectes.

**Étapes** :
1. **Installation du pare-feu** :
   - Choisir un pare-feu logiciel (ex : pfSense, iptables) ou matériel.
   - Configurer les règles de filtrage (ex : autoriser le trafic HTTP, bloquer les ports non utilisés).

2. **Surveillance du trafic** :
   - Utiliser NetFlow pour collecter des données sur le trafic.
   - Analyser les logs du pare-feu pour détecter des tentatives d'intrusion.

3. **Test et validation** :
   - Simuler des attaques (ex : scan de ports) pour vérifier l'efficacité du pare-feu.
   - Ajuster les règles en fonction des résultats.

**Outils** :
- Pare-feu : pfSense, iptables, Cisco ASA.
- Surveillance : NetFlow, Wireshark.
