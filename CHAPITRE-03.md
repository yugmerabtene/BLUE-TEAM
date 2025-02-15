### **Chapitre 3 : Rôles et responsabilités de la Blue Team**

---

#### **Théorie**

##### **1. Rôles clés dans une Blue Team**
Une Blue Team est composée de plusieurs rôles spécialisés, chacun ayant des responsabilités spécifiques pour assurer la sécurité des systèmes et des données. Voici les rôles clés :

- **Analyste SOC (Security Operations Center)** :
  - Responsable de la surveillance continue des systèmes et des réseaux.
  - Analyse les alertes de sécurité et les logs pour détecter les activités suspectes.
  - Travaille en étroite collaboration avec les autres membres de l'équipe pour répondre aux incidents.

- **Ingénieur en sécurité** :
  - Conçoit et met en œuvre des solutions de sécurité (pare-feu, IDS/IPS, chiffrement).
  - Effectue des tests de vulnérabilités et des audits de sécurité.
  - Assure la maintenance et la mise à jour des outils de sécurité.

- **Gestionnaire d'incidents** :
  - Coordonne la réponse aux incidents de sécurité.
  - Élabore et met à jour les plans de réponse aux incidents.
  - Communique avec les parties prenantes (direction, équipes techniques, juridique).

##### **2. Responsabilités de la Blue Team**
Les responsabilités principales de la Blue Team incluent :
- **Surveillance** : Surveillance continue des systèmes et des réseaux pour détecter les menaces.
- **Analyse des logs** : Examen des logs système et réseau pour identifier les activités suspectes.
- **Réponse aux incidents** : Réaction rapide et efficace en cas de violation de sécurité.
- **Formation des utilisateurs** : Sensibilisation des employés aux bonnes pratiques de sécurité (par exemple, éviter les attaques de phishing).

---

#### **Exercices**

##### **Exercice 1 : Organigramme d'une Blue Team**
1. **Créez un organigramme d'une Blue Team typique** :
   - Incluez les rôles suivants : Analyste SOC, Ingénieur en sécurité, Gestionnaire d'incidents.
   - Ajoutez les responsabilités associées à chaque rôle.
   - Indiquez les relations hiérarchiques et les interactions entre les rôles.

##### **Exercice 2 : Compétences techniques et non techniques**
1. **Identifiez les compétences nécessaires pour chaque rôle** :
   - **Analyste SOC** :
     - Techniques : Connaissance des SIEM (Splunk, ELK), analyse des logs, utilisation d'outils de surveillance.
     - Non techniques : Esprit d'analyse, capacité à travailler sous pression.
   - **Ingénieur en sécurité** :
     - Techniques : Configuration de pare-feu, gestion des IDS/IPS, tests de pénétration.
     - Non techniques : Résolution de problèmes, communication technique.
   - **Gestionnaire d'incidents** :
     - Techniques : Connaissance des procédures de réponse aux incidents, gestion des outils de forensic.
     - Non techniques : Leadership, gestion du stress, communication claire.

---

#### **Travaux Pratiques (TP)**

##### **TP 1 : Simulation d'un incident de sécurité**
**Objectif** : Simuler un incident de sécurité et attribuer des rôles à chaque membre de l'équipe pour y répondre.

**Scénario** :
- Une entreprise est victime d'une attaque de ransomware. Plusieurs fichiers critiques ont été chiffrés, et les attaquants demandent une rançon.

**Étapes** :
1. **Attribution des rôles** :
   - **Analyste SOC** : Surveille les logs pour identifier l'origine de l'attaque.
   - **Ingénieur en sécurité** : Isole les systèmes infectés et met en place des mesures de protection.
   - **Gestionnaire d'incidents** : Coordonne la réponse et communique avec la direction.

2. **Réponse à l'incident** :
   - **Analyste SOC** :
     - Analyse les logs pour identifier le point d'entrée de l'attaque.
     - Utilise un SIEM (par exemple, Splunk) pour détecter les activités suspectes.
   - **Ingénieur en sécurité** :
     - Isole les systèmes infectés du réseau pour empêcher la propagation.
     - Met à jour les règles du pare-feu et des IDS/IPS pour bloquer les communications malveillantes.
   - **Gestionnaire d'incidents** :
     - Documente l'incident et les mesures prises.
     - Communique avec la direction pour informer des impacts et des actions en cours.

3. **Restauration** :
   - Restaurez les systèmes à partir de sauvegardes.
   - Testez les systèmes pour vous assurer qu'ils fonctionnent correctement.

4. **Rapport** :
   - Rédigez un rapport détaillant les étapes suivies, les mesures prises et les recommandations pour éviter de futurs incidents.

---

#### **Outils utilisés dans ce chapitre**
- **SIEM (Splunk, ELK Stack)** : Pour la surveillance et l'analyse des logs.
- **Pare-feu (pfSense)** : Pour isoler les systèmes infectés.
- **Outils de forensic (Autopsy, FTK)** : Pour analyser les systèmes compromis.
- **Communication (Slack, Microsoft Teams)** : Pour coordonner la réponse aux incidents.

---

#### **Résumé du chapitre**
- La Blue Team est composée de rôles clés comme l'Analyste SOC, l'Ingénieur en sécurité et le Gestionnaire d'incidents.
- Chaque rôle a des responsabilités spécifiques, allant de la surveillance à la réponse aux incidents.
- Les compétences techniques et non techniques sont essentielles pour remplir ces rôles efficacement.
- Les exercices et TP permettent de simuler des scénarios réels et de comprendre les interactions entre les différents rôles.
