### **Chapitre-01 : Introduction à la Blue Team**

---

#### **Théorie**

##### **1. Définition de la Blue Team**
La **Blue Team** est une équipe de sécurité dont la mission principale est de défendre les systèmes d'information, les réseaux et les données d'une organisation contre les cybermenaces. Elle se concentre sur la prévention, la détection et la réponse aux attaques. La Blue Team travaille en étroite collaboration avec la **Red Team** (équipe offensive qui simule des attaques) et la **Purple Team** (qui assure la coordination et l'amélioration continue entre les deux équipes).

##### **2. Objectifs de la Blue Team**
- **Protéger les actifs** : Sécuriser les infrastructures critiques, les données sensibles et les applications.
- **Détecter les menaces** : Identifier les activités suspectes ou malveillantes grâce à une surveillance continue.
- **Répondre aux incidents** : Réagir rapidement et efficacement en cas de violation de sécurité.
- **Maintenir la résilience** : Assurer la continuité des opérations après un incident et améliorer les défenses.

##### **3. Différence entre Blue Team, Red Team et Purple Team**
- **Blue Team** : Défensive, se concentre sur la protection et la réponse.
- **Red Team** : Offensive, simule des attaques pour tester les défenses.
- **Purple Team** : Collaborative, facilite l'échange d'informations entre la Blue et la Red Team pour améliorer la sécurité globale.

---

#### **Exercices**

##### **Exercice 1 : Comparaison des rôles**
1. **Recherchez et comparez les rôles de la Blue Team, Red Team et Purple Team** :
   - Blue Team : Surveillance, analyse des logs, réponse aux incidents.
   - Red Team : Tests d'intrusion, exploitation des vulnérabilités.
   - Purple Team : Coordination, amélioration des processus de sécurité.
2. **Identifiez les compétences clés nécessaires pour chaque équipe**.

##### **Exercice 2 : Exemples d'organisations**
1. **Identifiez trois exemples d'organisations utilisant des Blue Teams** :
   - Secteur bancaire : Banques pour protéger les transactions financières.
   - Secteur de la santé : Hôpitaux pour sécuriser les données médicales.
   - Secteur public : Gouvernements pour défendre les infrastructures critiques.

---

#### **Travaux Pratiques (TP)**

##### **TP 1 : Mise en place d'un environnement de test**
**Objectif** : Créer un environnement de test pour simuler un réseau d'entreprise et s'entraîner aux techniques de défense.

**Étapes** :
1. **Installez VirtualBox ou VMware** :
   - Téléchargez et installez VirtualBox (https://www.virtualbox.org/) ou VMware Workstation Player (https://www.vmware.com/).
2. **Configurez un réseau virtuel** :
   - Créez trois machines virtuelles (VM) :
     - Une VM pour un serveur Windows (par exemple, Windows Server 2019).
     - Une VM pour un client Windows 10.
     - Une VM pour un serveur Linux (par exemple, Ubuntu Server).
   - Configurez un réseau interne dans VirtualBox/VMware pour connecter les machines.
3. **Installez les outils de base** :
   - Sur le serveur Linux, installez des outils de surveillance comme Wireshark et tcpdump.
   - Sur le serveur Windows, installez un antivirus (par exemple, Windows Defender ou ClamAV).
4. **Testez la connectivité** :
   - Vérifiez que les machines peuvent communiquer entre elles via le réseau interne.
   - Utilisez `ping` pour tester la connectivité.

---

#### **Travaux Dirigés (TD)**

##### **TD 1 : Simulation d'un scénario de défense**
**Objectif** : Comprendre le rôle de la Blue Team dans un scénario réel.

**Scénario** :
- Une entreprise fictive est victime d'une tentative de phishing. Un employé a cliqué sur un lien malveillant, et un malware a été téléchargé sur son poste de travail.

**Étapes** :
1. **Analyse des logs** :
   - Utilisez les logs du pare-feu et des serveurs pour identifier l'origine de l'attaque.
2. **Containement** :
   - Isolez la machine infectée du réseau pour empêcher la propagation du malware.
3. **Investigation** :
   - Utilisez des outils comme Wireshark pour analyser le trafic réseau et identifier le malware.
4. **Réponse** :
   - Supprimez le malware et restaurez le système à partir d'une sauvegarde.
5. **Rapport** :
   - Rédigez un rapport détaillant les étapes suivies et les mesures prises pour prévenir de futures attaques.

---

#### **Outils utilisés dans ce chapitre**
- **VirtualBox/VMware** : Pour créer un environnement de test.
- **Wireshark** : Pour analyser le trafic réseau.
- **Windows Defender/ClamAV** : Pour la détection de malware.
- **Tcpdump** : Pour capturer les paquets réseau sur Linux.

---

#### **Résumé du chapitre**
- La Blue Team est essentielle pour protéger les systèmes d'information contre les cybermenaces.
- Elle travaille en collaboration avec la Red Team et la Purple Team pour améliorer la sécurité.
- Les exercices et TP permettent de comprendre les rôles et responsabilités de la Blue Team et de s'entraîner dans un environnement simulé.
