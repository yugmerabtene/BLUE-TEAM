### Chapitre-08 : **Analyse des menaces et vulnérabilités**

---

#### **Introduction**
L'analyse des menaces et des vulnérabilités est une étape essentielle pour comprendre les risques auxquels une organisation est exposée. Ce chapitre explore les concepts clés tels que les menaces (APT, malware, phishing), les vulnérabilités (CVE, CVSS), et les outils de scanning (Nessus, OpenVAS). Des exercices pratiques et un TP sont proposés pour appliquer ces concepts.

---

### **Théorie**

#### **1. Menaces**
Les menaces sont des actions ou des événements potentiels qui peuvent causer des dommages aux systèmes, aux réseaux ou aux données d'une organisation. Voici trois types de menaces courantes :

##### **a. APT (Advanced Persistent Threat)**
- **Définition** : Une APT est une attaque sophistiquée et ciblée menée par des acteurs malveillants hautement qualifiés (ex : États-nations, groupes criminels organisés).
- **Objectif** : Voler des données sensibles ou espionner une organisation sur une longue période.
- **Exemple** : L'attaque APT "Stuxnet" contre les installations nucléaires iraniennes.

##### **b. Malware**
- **Définition** : Un logiciel malveillant conçu pour endommager, exploiter ou infiltrer un système.
- **Types** : Virus, vers, ransomware, spyware, etc.
- **Exemple** : Le ransomware "WannaCry" qui a crypté les données de milliers d'organisations en 2017.

##### **c. Phishing**
- **Définition** : Une technique d'ingénierie sociale visant à tromper les utilisateurs pour qu'ils divulguent des informations sensibles (ex : mots de passe, numéros de carte de crédit).
- **Méthodes** : Emails frauduleux, sites web falsifiés.
- **Exemple** : Un email semblant provenir d'une banque demandant de réinitialiser un mot de passe.

---

#### **2. Vulnérabilités**
Les vulnérabilités sont des faiblesses dans un système qui peuvent être exploitées par des menaces pour causer des dommages.

##### **a. CVE (Common Vulnerabilities and Exposures)**
- **Définition** : Une base de données publique qui répertorie les vulnérabilités connues avec un identifiant unique (ex : CVE-2021-34527).
- **Utilité** : Permet de standardiser la référence aux vulnérabilités.

##### **b. CVSS (Common Vulnerability Scoring System)**
- **Définition** : Un système de notation qui évalue la gravité d'une vulnérabilité sur une échelle de 0 à 10.
- **Critères** : Base score (impact, exploitabilité), Temporal score (état actuel), Environmental score (contexte spécifique).

##### **c. Scanning de vulnérabilités**
Le scanning consiste à identifier les vulnérabilités dans un système à l'aide d'outils spécialisés.

- **Nessus** : Un outil de scanning de vulnérabilités largement utilisé pour détecter les faiblesses dans les systèmes et les réseaux.
- **OpenVAS** : Un outil open source pour le scanning de vulnérabilités, similaire à Nessus.

---

### **Exercice**

#### **1. Recherchez une CVE récente et expliquez son impact**

**Exemple : CVE-2023-12345**
1. **Description** : Une vulnérabilité critique dans Apache Struts permettant l'exécution de code à distance.
2. **Impact** :
   - **Gravité CVSS** : 9.8 (Critique).
   - **Conséquences** : Un attaquant peut exécuter du code arbitraire sur le serveur affecté, conduisant à une prise de contrôle complète.
3. **Correctif** : Appliquer la mise à jour fournie par Apache.

---

#### **2. Utilisez un scanner de vulnérabilités pour analyser un système**

**Étapes pour utiliser OpenVAS :**
1. **Installation** : Installer OpenVAS sur une machine dédiée.
2. **Configuration** : Configurer les cibles (adresses IP des systèmes à scanner).
3. **Scanning** : Lancer un scan complet des vulnérabilités.
4. **Analyse** : Examiner les résultats pour identifier les vulnérabilités critiques.
5. **Rapport** : Générer un rapport détaillé des vulnérabilités détectées.

---

### **TP : Analyse d'un système avec OpenVAS et proposition de correctifs**

#### **Objectif**
Analyser un système avec OpenVAS pour identifier les vulnérabilités et proposer des correctifs appropriés.

#### **Étapes**

1. **Préparation** :
   - Installer OpenVAS sur une machine de test.
   - Configurer une machine virtuelle comme cible (ex : une machine Windows 10 non mise à jour).

2. **Scanning** :
   - Lancer un scan complet de la machine cible avec OpenVAS.
   - Utiliser les paramètres par défaut pour une analyse approfondie.

3. **Analyse des résultats** :
   - Identifier les vulnérabilités critiques (ex : CVE-2023-12345).
   - Examiner les détails de chaque vulnérabilité (description, impact, CVSS score).

4. **Proposition de correctifs** :
   - **Correctif 1** : Appliquer les mises à jour de sécurité pour les logiciels vulnérables.
   - **Correctif 2** : Configurer un pare-feu pour bloquer les ports inutiles.
   - **Correctif 3** : Renforcer les politiques de mot de passe pour prévenir les accès non autorisés.

5. **Rapport final** :
   - Documenter les vulnérabilités détectées.
   - Proposer un plan d'action pour corriger les vulnérabilités.
   - Inclure des recommandations pour améliorer la sécurité globale du système.

---
