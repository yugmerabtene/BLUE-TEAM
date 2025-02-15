### Chapitre-07 : **Gestion des incidents de sécurité**

---

#### **Introduction**
La gestion des incidents de sécurité est un processus structuré pour identifier, contenir, éradiquer et récupérer après un incident de sécurité. Ce chapitre explore le cycle de gestion des incidents, les outils utilisés, et propose des exercices pratiques pour renforcer les compétences en réponse aux incidents.

---

### **Théorie**

#### **1. Cycle de gestion des incidents**
Le cycle de gestion des incidents est un cadre en six étapes pour gérer efficacement les incidents de sécurité. Chaque étape est cruciale pour minimiser les dommages et prévenir de futurs incidents.

##### **a. Préparation**
La préparation est la phase proactive où l'organisation se prépare à répondre aux incidents. Cela inclut :
- **Formation** : Former les employés et l'équipe de sécurité.
- **Plan de réponse** : Élaborer un plan de réponse aux incidents.
- **Outils** : Mettre en place des outils de détection et de réponse (SIEM, forensic tools).
- **Communication** : Définir les canaux de communication et les rôles.

##### **b. Identification**
L'identification consiste à détecter et analyser un incident potentiel. Cela inclut :
- **Surveillance** : Utiliser des outils de surveillance pour détecter les anomalies.
- **Analyse** : Examiner les logs, les alertes et les comportements suspects.
- **Documentation** : Enregistrer les détails de l'incident (date, heure, impact).

##### **c. Confinement**
Le confinement vise à limiter la propagation de l'incident. Cela inclut :
- **Isolation** : Isoler les systèmes affectés du réseau.
- **Contrôle d'accès** : Révoquer les accès compromis.
- **Communication** : Informer les parties prenantes.

##### **d. Éradication**
L'éradication consiste à supprimer la cause de l'incident. Cela inclut :
- **Suppression** : Supprimer les malwares, fermer les vulnérabilités.
- **Réinitialisation** : Réinitialiser les mots de passe compromis.
- **Vérification** : S'assurer que la menace est complètement éliminée.

##### **e. Récupération**
La récupération vise à restaurer les systèmes et les opérations normales. Cela inclut :
- **Restoration** : Restaurer les systèmes à partir de sauvegardes.
- **Test** : Tester les systèmes pour s'assurer qu'ils fonctionnent correctement.
- **Surveillance** : Surveiller les systèmes pour détecter toute activité suspecte.

##### **f. Leçons apprises**
Cette phase consiste à analyser l'incident et à améliorer les processus. Cela inclut :
- **Analyse** : Examiner ce qui a fonctionné et ce qui n'a pas fonctionné.
- **Documentation** : Documenter les leçons apprises.
- **Amélioration** : Mettre à jour les politiques, procédures et outils.

---

#### **2. Outils de gestion des incidents**
Les outils sont essentiels pour détecter, analyser et répondre aux incidents de sécurité.

##### **a. Ticketing (Jira)**
Jira est un outil de gestion de projets et de tickets utilisé pour suivre les incidents de sécurité. Il permet de :
- Créer des tickets pour chaque incident.
- Assigner des tâches à l'équipe de sécurité.
- Suivre l'état d'avancement des incidents.

##### **b. Forensic tools (Autopsy)**
Autopsy est un outil d'analyse forensique utilisé pour examiner les systèmes compromis. Il permet de :
- Analyser les fichiers et les logs.
- Récupérer des données supprimées.
- Générer des rapports détaillés.

---

### **Exercice**

#### **1. Analysez un cas réel d'incident de sécurité (par exemple, une fuite de données)**

**Cas : Fuite de données chez Equifax (2017)**
1. **Identification** :
   - Détection d'une vulnérabilité dans le système Apache Struts.
   - Fuite de données personnelles de 147 millions de personnes.

2. **Confinement** :
   - Isolation des systèmes affectés.
   - Fermeture de la vulnérabilité.

3. **Éradication** :
   - Suppression des accès non autorisés.
   - Mise à jour des systèmes.

4. **Récupération** :
   - Restauration des systèmes à partir de sauvegardes.
   - Notification des personnes affectées.

5. **Leçons apprises** :
   - Amélioration des processus de gestion des correctifs.
   - Renforcement des contrôles d'accès.

---

#### **2. Proposez un plan de réponse pour un ransomware**

**Plan de réponse pour un ransomware :**
1. **Préparation** :
   - Sauvegardes régulières des données.
   - Formation des employés sur les emails de phishing.

2. **Identification** :
   - Détection des fichiers cryptés et des messages de rançon.
   - Analyse des logs pour identifier l'origine de l'attaque.

3. **Confinement** :
   - Isolation des systèmes affectés.
   - Déconnexion du réseau.

4. **Éradication** :
   - Suppression du ransomware.
   - Fermeture des vulnérabilités exploitées.

5. **Récupération** :
   - Restauration des systèmes à partir de sauvegardes.
   - Vérification de l'intégrité des données.

6. **Leçons apprises** :
   - Mise à jour des politiques de sécurité.
   - Renforcement des contrôles d'accès et des sauvegardes.

---

### **TP : Simulation d'un incident de ransomware et suivi des étapes du cycle de gestion des incidents**

#### **Objectif**
Simuler un incident de ransomware et suivre les étapes du cycle de gestion des incidents pour répondre efficacement.

#### **Étapes**

1. **Préparation** :
   - Configurer un environnement de test avec des machines virtuelles.
   - Installer des outils de surveillance (SIEM, antivirus).

2. **Identification** :
   - Injecter un ransomware simulé dans l'environnement.
   - Détecter l'incident via les outils de surveillance.

3. **Confinement** :
   - Isoler les machines affectées du réseau.
   - Bloquer les communications suspectes.

4. **Éradication** :
   - Analyser le ransomware pour comprendre son fonctionnement.
   - Supprimer le ransomware des systèmes affectés.

5. **Récupération** :
   - Restaurer les systèmes à partir de sauvegardes.
   - Vérifier que les systèmes fonctionnent correctement.

6. **Leçons apprises** :
   - Documenter les étapes suivies et les résultats.
   - Identifier les améliorations à apporter aux politiques et procédures.

---
