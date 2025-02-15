### **Introduction à la Blue Team**
#### **Théorie**
- Définition de la Blue Team : La Blue Team est une équipe de sécurité chargée de défendre les systèmes d'information contre les attaques. Elle travaille en collaboration avec la Red Team (attaque) et la Purple Team (coordination).
- Objectifs : Protéger les actifs, détecter les menaces, répondre aux incidents et maintenir la résilience.
- Différence entre Blue Team, Red Team et Purple Team.

#### **Exercice**
1. Recherchez et comparez les rôles de la Blue Team, Red Team et Purple Team dans une organisation.
2. Identifiez trois exemples d'organisations utilisant des Blue Teams.

#### **TP**
- Mettez en place un environnement de test (lab) avec des outils comme VirtualBox ou VMware pour simuler un réseau d'entreprise.

---

### **Concepts fondamentaux de la Blue Team**
#### **Théorie**
- Principes de base : Confidentialité, intégrité, disponibilité (CIA).
- Modèles de sécurité : Défense en profondeur, moindre privilège, segmentation.
- Cycle de vie de la sécurité : Prévention, détection, réponse, récupération.

#### **Exercice**
1. Expliquez en détail le modèle de défense en profondeur.
2. Donnez un exemple concret d'application du principe de moindre privilège.

#### **TP**
- Configurez un pare-feu (pfSense) et appliquez des règles de segmentation réseau.

---

### **Rôles et responsabilités de la Blue Team**
#### **Théorie**
- Rôles clés : Analyste SOC, ingénieur en sécurité, gestionnaire d'incidents.
- Responsabilités : Surveillance, analyse des logs, réponse aux incidents, formation des utilisateurs.

#### **Exercice**
1. Créez un organigramme d'une Blue Team typique avec les rôles et responsabilités.
2. Identifiez les compétences techniques et non techniques nécessaires pour chaque rôle.

#### **TP**
- Simulez un incident de sécurité et attribuez des rôles à chaque membre de l'équipe pour y répondre.

---

### **Méthodes et outils utilisés par la Blue Team**
#### **Théorie**
- Méthodes : Analyse des logs, chasse aux menaces (threat hunting), analyse forensique.
- Outils : SIEM (Splunk, ELK), IDS/IPS (Snort, Suricata), antivirus (CrowdStrike).

#### **Exercice**
1. Comparez deux outils SIEM (par exemple, Splunk vs ELK Stack).
2. Expliquez le fonctionnement d'un IDS comme Snort.

#### **TP**
- Installez et configurez un SIEM (ELK Stack) pour surveiller un réseau virtuel.

---

### **Gestion de la sécurité**
#### **Théorie**
- Gestion des risques : Identification, évaluation, traitement des risques.
- Cadres de sécurité : ISO 27001, NIST Cybersecurity Framework.

#### **Exercice**
1. Appliquez le cadre NIST à un scénario d'entreprise fictif.
2. Identifiez les risques liés à une infrastructure cloud.

#### **TP**
- Réalisez une analyse de risque pour un scénario donné et proposez des mesures de mitigation.

---

### **Politiques de sécurité et procédures de la Blue Team**
#### **Théorie**
- Politiques : Acceptable Use Policy (AUP), politique de mot de passe.
- Procédures : Réponse aux incidents, gestion des correctifs.

#### **Exercice**
1. Rédigez une politique de mot de passe pour une entreprise.
2. Créez une procédure de réponse à un incident de phishing.

#### **TP**
- Mettez en œuvre une politique de mot de passe sur un domaine Active Directory.

---

### **Gestion des incidents de sécurité**
#### **Théorie**
- Cycle de gestion des incidents : Préparation, identification, confinement, éradication, récupération, leçons apprises.
- Outils : Ticketing (Jira), forensic tools (Autopsy).

#### **Exercice**
1. Analysez un cas réel d'incident de sécurité (par exemple, une fuite de données).
2. Proposez un plan de réponse pour un ransomware.

#### **TP**
- Simulez un incident de ransomware et suivez les étapes du cycle de gestion des incidents.

---

### **Analyse des menaces et vulnérabilités**
#### **Théorie**
- Menaces : APT, malware, phishing.
- Vulnérabilités : CVE, CVSS, scanning (Nessus, OpenVAS).

#### **Exercice**
1. Recherchez une CVE récente et expliquez son impact.
2. Utilisez un scanner de vulnérabilités pour analyser un système.

#### **TP**
- Analysez un système avec OpenVAS et proposez des correctifs.

---

### **Défense des réseaux**
#### **Théorie**
- Techniques : Pare-feu, segmentation, VPN.
- Surveillance : NetFlow, analyse de paquets (Wireshark).

#### **Exercice**
1. Configurez un VPN sur un routeur.
2. Analysez un fichier PCAP avec Wireshark.

#### **TP**
- Mettez en place un pare-feu et surveillez le trafic réseau.

---

### **Défense des applications**
#### **Théorie**
- Techniques : WAF, validation des entrées, chiffrement.
- Surveillance : Logs d'application, analyse des comportements.

#### **Exercice**
1. Configurez un WAF (ModSecurity) pour une application web.
2. Identifiez les vulnérabilités OWASP Top 10 dans une application.

#### **TP**
- Sécurisez une application web avec un WAF et testez-la avec OWASP ZAP.

---

### **Gestion de la sécurité des données**
#### **Théorie**
- Techniques : Chiffrement (AES, RSA), DLP, sauvegarde.
- Surveillance : Détection d'anomalies, classification des données.

#### **Exercice**
1. Chiffrez un fichier avec AES.
2. Configurez une solution DLP pour surveiller les données sensibles.

#### **TP**
- Mettez en place un système de sauvegarde chiffrée avec VeraCrypt.

---

### **Gestion de la sécurité des périphériques**
#### **Théorie**
- Techniques : MDM, mise à jour des firmwares, contrôle d'accès.
- Surveillance : Détection des périphériques non autorisés.

#### **Exercice**
1. Configurez un MDM pour gérer des appareils mobiles.
2. Identifiez les risques liés aux périphériques IoT.

#### **TP**
- Sécurisez un réseau IoT avec des règles de pare-feu.

---

### **Conformité et gouvernance**
#### **Théorie**
- Règlementations : GDPR, HIPAA, PCI-DSS.
- Gouvernance : Politiques, audits, reporting.

#### **Exercice**
1. Comparez GDPR et HIPAA.
2. Rédigez un rapport d'audit de sécurité fictif.

#### **TP**
- Réalisez un audit de conformité pour un scénario donné.

---

### **Pratiques de rapport et de présentation de la sécurité**
#### **Théorie**
- Rapports : Structure, clarté, visualisation des données.
- Présentation : Adaptation au public, gestion des questions.

#### **Exercice**
1. Créez un rapport d'incident de sécurité.
2. Présentez un plan de sécurité à un public non technique.

#### **TP**
- Présentez un rapport de sécurité à vos collègues et recueillez des feedbacks.
