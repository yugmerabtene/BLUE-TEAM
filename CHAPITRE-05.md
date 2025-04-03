### **Chapitre 5 : Gestion de la sécurité**

---

#### **Théorie**

##### **1. Gestion des risques**
La gestion des risques est un processus essentiel pour identifier, évaluer et traiter les risques qui pourraient affecter la sécurité des systèmes et des données. Voici les étapes clés :

- **Identification des risques** :
  - Identifier les actifs critiques (données, systèmes, applications).
  - Lister les menaces potentielles (cyberattaques, erreurs humaines, catastrophes naturelles).
  - Exemple : Une base de données client est un actif critique, et une fuite de données est une menace.

- **Évaluation des risques** :
  - Évaluer la probabilité et l'impact de chaque risque.
  - Utiliser une matrice de risque pour prioriser les risques (faible, moyen, élevé).
  - Exemple : Une attaque de ransomware a une probabilité élevée et un impact élevé sur une entreprise.

- **Traitement des risques** :
  - Choisir une stratégie pour chaque risque :
    - **Éviter** : Éliminer le risque (par exemple, ne pas stocker de données sensibles).
    - **Réduire** : Mettre en place des contrôles de sécurité (pare-feu, chiffrement).
    - **Transférer** : Souscrire une assurance cyber.
    - **Accepter** : Accepter le risque si le coût de mitigation est trop élevé.

##### **2. Cadres de sécurité**
Les cadres de sécurité fournissent des lignes directrices pour gérer la sécurité de manière structurée. Voici deux cadres couramment utilisés :

- **ISO 27001** :
  - Norme internationale pour la gestion de la sécurité de l'information.
  - Basée sur le cycle PDCA (Plan-Do-Check-Act).
  - Exige la mise en place d'un système de gestion de la sécurité de l'information (SMSI).

- **NIST Cybersecurity Framework** :
  - Cadre développé par le National Institute of Standards and Technology (NIST).
  - Composé de cinq fonctions : Identifier, Protéger, Détecter, Répondre, Récupérer.
  - Utilisé pour améliorer la posture de sécurité des organisations.

---

#### **Exercices**

##### **Exercice 1 : Application du cadre NIST**
1. **Appliquez le cadre NIST à un scénario d'entreprise fictif** :
   - Scénario : Une entreprise de commerce électronique stocke les données de ses clients dans le cloud.
   - Étapes :
     - **Identifier** : Lister les actifs (données clients, serveurs cloud) et les menaces (fuites de données, attaques DDoS).
     - **Protéger** : Mettre en place des contrôles de sécurité (chiffrement, authentification à deux facteurs).
     - **Détecter** : Surveiller les logs pour détecter les activités suspectes.
     - **Répondre** : Élaborer un plan de réponse aux incidents.
     - **Récupérer** : Restaurer les systèmes et les données après un incident.

##### **Exercice 2 : Risques liés à une infrastructure cloud**
1. **Identifiez les risques liés à une infrastructure cloud** :
   - **Fuites de données** : Accès non autorisé aux données sensibles.
   - **Pannes de service** : Indisponibilité des services cloud.
   - **Configuration incorrecte** : Mauvaise configuration des services cloud (par exemple, des buckets S3 publics).
2. **Proposez des mesures pour atténuer ces risques**.

---

#### **Travaux Pratiques (TP)**

##### **TP 1 : Analyse de risque et mesures de mitigation**
**Objectif** : Réaliser une analyse de risque pour un scénario donné et proposer des mesures de mitigation.

**Scénario** :
- Une entreprise utilise un serveur web hébergé sur AWS pour son site e-commerce. Le serveur stocke les informations de paiement des clients.

**Étapes** :
1. **Identification des risques** :
   - Liste des actifs : Serveur web, base de données clients, informations de paiement.
   - Liste des menaces : Attaques DDoS, fuites de données, erreurs de configuration.

2. **Évaluation des risques** :
   - Utilisez une matrice de risque pour évaluer la probabilité et l'impact de chaque menace.
   - Exemple :
     - Attaque DDoS : Probabilité élevée, impact élevé.
     - Fuite de données : Probabilité moyenne, impact élevé.

3. **Traitement des risques** :
   - **Attaque DDoS** :
     - Mesure de mitigation : Utiliser un service de protection DDoS (par exemple, AWS Shield).
   - **Fuite de données** :
     - Mesure de mitigation : Chiffrer les données sensibles, mettre en place des contrôles d'accès stricts.

4. **Rédaction du rapport** :
   - Documentez les risques identifiés, leur évaluation et les mesures de mitigation proposées.

---

#### **Travaux Dirigés (TD)**

##### **TD 1 : Mise en œuvre d'un SMSI basé sur ISO 27001**
**Objectif** : Appliquer les principes de l'ISO 27001 pour mettre en place un système de gestion de la sécurité de l'information (SMSI) https://cdn.standards.iteh.ai/samples/82875/ca15850b2c6448ccb7b90b4498213646/ISO-IEC-27001-2022.pdf.  

**Étapes** :
1. **Plan (Plan)** :
   - Définir la portée du SMSI (par exemple, sécurité des données clients).
   - Identifier les parties prenantes et leurs responsabilités.

2. **Do (Faire)** :
   - Mettre en place des contrôles de sécurité (par exemple, politique de mot de passe, chiffrement des données).
   - Former les employés aux bonnes pratiques de sécurité.

3. **Check (Vérifier)** :
   - Surveiller et mesurer l'efficacité des contrôles.
   - Effectuer des audits internes pour identifier les écarts.

4. **Act (Agir)** :
   - Améliorer continuellement le SMSI en fonction des résultats des audits.
   - Mettre à jour les politiques et procédures de sécurité.

---

#### **Outils utilisés dans ce chapitre**
- **Matrice de risque** : Pour évaluer et prioriser les risques.
- **AWS Shield** : Pour la protection contre les attaques DDoS.
- **Chiffrement (AES, RSA)** : Pour protéger les données sensibles.
- **ISO 27001 Documentation Toolkit** : Pour mettre en place un SMSI.

---

#### **Résumé du chapitre**
- La gestion des risques est un processus clé pour protéger les systèmes et les données.
- Les cadres de sécurité comme ISO 27001 et NIST fournissent des lignes directrices pour une gestion structurée de la sécurité.
- Les exercices et TP permettent de mettre en pratique ces concepts dans des scénarios réels, renforçant ainsi les compétences en gestion des risques.
