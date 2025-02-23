### **Comprendre le NIST - Rôles, Normes et Applications**

#### **Objectifs du cours**
- Découvrir le NIST dans sa globalité : histoire, mission et domaines d’expertise.
- Explorer ses contributions majeures en cybersécurité, métrologie et technologies émergentes.
- Approfondir les normes NIST les plus utilisées (série SP 800 et autres).
- Appliquer les concepts à travers un cas pratique.

### **Plan du cours**

1. **Introduction au NIST : Une vue d’ensemble**
   - Historique et mission.
   - Domaines d’expertise.

2. **Le NIST et la cybersécurité**
   - Publications clés (SP 800).
   - Le Cybersecurity Framework (CSF) en détail.
   - Comparaison avec d’autres cadres.

3. **Autres contributions du NIST**
   - Métrologie et standards physiques.
   - Technologies émergentes (IA, cryptographie post-quantique).

4. **Mise en œuvre des normes NIST**
   - Approche pratique pour adopter les recommandations.
   - Étude de cas sectorielle.

5. **Exercice pratique**
   - Scénario réaliste avec analyse.

6. **Conclusion et ressources**

---

### **1. Introduction au NIST : Une vue d’ensemble**

#### **Historique et mission**
- **Création** : Fondé en 1901 sous le nom de National Bureau of Standards (NBS), devenu NIST en 1988.
- **Mission** : Développer des normes, des technologies et des mesures pour stimuler l’innovation et la compétitivité aux États-Unis.
- **Évolution** : Initialement centré sur les standards physiques (ex. : poids, mesures), le NIST s’est adapté aux besoins modernes comme la cybersécurité et l’intelligence artificielle.

#### **Domaines d’expertise**
- **Métrologie** : Standards de mesure (temps, longueur, masse).
- **Cybersécurité** : Protection des systèmes d’information.
- **Technologies avancées** : Recherche sur l’IA, la 5G, la blockchain.
- **Industrie** : Collaboration avec le secteur privé pour des normes pratiques.

#### **Impact mondial**
- Bien que basé aux États-Unis (Gaithersburg, Maryland), les normes NIST sont adoptées internationalement, notamment en cybersécurité et cryptographie.

---

### **2. Le NIST et la cybersécurité**

#### **Publications clés (SP 800)**
- **SP 800-53 : Contrôles de sécurité et de confidentialité**
  - Plus de 900 contrôles pour sécuriser les systèmes fédéraux.
  - Révision 5 (2020) : Intègre la vie privée et les menaces modernes.
  - Exemple : AC-3 (contrôle d’accès basé sur les rôles).

- **SP 800-171 : Protection des informations non classifiées**
  - 110 exigences pour les sous-traitants travaillant avec le gouvernement américain.
  - Exemple : 3.5.3 (authentification multifacteur).

- **SP 800-37 : Risk Management Framework (RMF)**
  - Cadre pour gérer les risques en 7 étapes : Préparer, Catégoriser, Sélectionner, Implémenter, Évaluer, Autoriser, Surveiller.
  - Utilisé avec SP 800-53.

- **SP 800-63 : Identité numérique**
  - Recommandations sur les mots de passe et l’authentification (ex. : éviter les changements fréquents sauf en cas de compromission).

#### **Le Cybersecurity Framework (CSF) en détail**
- **Structure** :
  - **5 fonctions** : Identifier, Protéger, Détecter, Répondre, Récupérer.
  - **Core** : 23 catégories (ex. : gestion des risques) et 108 sous-catégories.
  - **Tiers** : 4 niveaux de maturité (Partiel à Adaptatif).
  - **Profiles** : État actuel vs cible.
- **Version actuelle** : 1.1 (2018), avec une version 2.0 en préparation pour 2024, élargissant son scope aux PME et aux technologies émergentes.
- **Exemple** : Une banque utilise "Detect" pour déployer un système de détection d’anomalies.

#### **Comparaison avec d’autres cadres**
- **NIST CSF vs ISO 27001** :
  - NIST : Gratuit, fonctionnel, flexible.
  - ISO : Certifiable, structuré, payant.
- **NIST vs CIS Controls** :
  - NIST : Plus large, stratégique.
  - CIS : Plus technique, orienté outils.

---

### **3. Autres contributions du NIST**

#### **Métrologie et standards physiques**
- **Temps** : Horloge atomique NIST-F2, référence mondiale pour le temps (UTC).
- **Mesures** : Étalons pour la masse, la longueur, l’électricité.
- **Exemple** : Calibration des instruments industriels.

#### **Technologies émergentes**
- **Cryptographie** :
  - Standards comme AES (Advanced Encryption Standard) et SHA-3.
  - Recherche sur la cryptographie post-quantique (face aux ordinateurs quantiques).
- **Intelligence artificielle** :
  - Lignes directrices pour des IA fiables (SP 800-204).
- **5G et IoT** :
  - Recommandations pour sécuriser les réseaux (SP 800-187).

#### **Collaboration industrielle**
- Programmes comme le **Manufacturing Extension Partnership (MEP)** pour aider les PME à adopter des technologies sécurisées.

---

### **4. Mise en œuvre des normes NIST**

#### **Approche pratique**
1. **Choix de la norme** :
   - SP 800-53 pour les systèmes fédéraux.
   - CSF pour une approche flexible.
   - SP 800-171 pour les sous-traitants.

2. **Évaluation des besoins** :
   - Identifier les actifs (ex. : serveurs, données clients).
   - Évaluer les risques (menaces comme phishing, vulnérabilités comme logiciels obsolètes).

3. **Planification** :
   - Sélectionner les contrôles adaptés (ex. : SP 800-53 AC-7 pour limiter les tentatives de connexion).
   - Définir des priorités (ex. : MFA avant audits).

4. **Implémentation** :
   - Déployer des outils (ex. : SIEM pour la détection).
   - Former le personnel.

5. **Surveillance et amélioration** :
   - Audits réguliers.
   - Ajustements basés sur les incidents.

#### **Étude de cas sectorielle : Défense**
- **Contexte** : Une entreprise sous-traitante pour le Département de la Défense.
- **Norme** : SP 800-171.
- **Actions** :
  - Identifier : Liste des données CUI (plans techniques).
  - Protéger : Cryptage AES-256.
  - Détecter : Surveillance des accès.
  - Répondre : Plan d’isolation en cas de brèche.
  - Récupérer : Sauvegardes hors site.

---

### **5. Exercice pratique**

#### **Scénario : Une université**
- **Contexte** : Gestion des données étudiantes et recherches sensibles.
- **Objectif** : Appliquer le NIST CSF.

1. **Identifier** :
   - Actifs : Bases de données étudiants, serveurs de recherche.
   - Risques : Cyberattaques ciblées (ex. : ransomware).

2. **Protéger** :
   - Mesures : MFA pour les comptes, pare-feu réseau.

3. **Détecter** :
   - Outils : Logs analysés via un SIEM.

4. **Répondre** :
   - Plan : Notifier les autorités, isoler les systèmes.

5. **Récupérer** :
   - Actions : Restaurer les données, améliorer les défenses.

**Questions** :
- Quelle fonction prioriseriez-vous si les fonds sont limités ?
- Quels contrôles de SP 800-53 ajouteriez-vous ?

---

### **6. Conclusion et ressources**

- **Résumé** : Le NIST est un pilier des normes modernes, de la cybersécurité à la métrologie. Ses cadres comme le CSF et SP 800-53 offrent des solutions pratiques et évolutives.
- **Ressources** :
  - [www.nist.gov](https://www.nist.gov) : Téléchargements gratuits des SP 800.
  - CSF Tools : Templates sur le site NIST.
  - Communautés : Groupes LinkedIn ou X sur la cybersécurité NIST.

---