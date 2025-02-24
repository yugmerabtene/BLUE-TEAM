## **Constat et Rapport Forensic en France : Intégration des Normes NIS et Européennes**

En France, lorsqu’une analyse forensic révèle une adresse IP liée à une cyberattaque contre une entreprise, le constat et le rapport doivent non seulement respecter les exigences judiciaires nationales, mais aussi se conformer aux obligations européennes, notamment la Directive NIS (transposée en droit français par la Loi n° 2018-133 du 26 février 2018), le RGPD (Règlement Général sur la Protection des Données) et d'autres normes internationales telles que l'ISO/IEC 27001 (Gestion de la Sécurité de l'Information) et ISO/IEC 27037 (Gestion des preuves numériques). Voici une structure détaillée et optimisée :

---

### **1. Procédure en cas de cyberattaque : Étapes clés**

1. **Détection de l'incident**
   - Identification des signaux d’alerte (ralentissement du système, comportements anormaux, alertes SIEM, etc.).
   - Isolation des systèmes compromis pour limiter la propagation.
   
2. **Notification interne et activation du plan de réponse**
   - Alerter l’équipe de sécurité et la direction.
   - Activation du Plan de Reprise d’Activité (PRA) et/ou du Plan de Continuité d’Activité (PCA) si nécessaire.
   
3. **Désignation de l’expert habilité**
   - Expert en forensic qualifié (certifié ISO/IEC 27037, CHFI, GIAC GCFA, etc.).
   - Possibilité de recourir à un prestataire externe agréé par l’ANSSI.
   
4. **Collecte et préservation des preuves**
   - Acquisition des logs système, journaux d’événements, captures réseau (PCAP).
   - Hashage des fichiers pour garantir leur intégrité.
   - Documentation de la chaîne de conservation des preuves.
   
5. **Rédaction du rapport forensic**
   - Élaboration du constat initial (procès-verbal forensic).
   - Analyse approfondie et rédaction du rapport détaillé.
   
6. **Notification aux autorités compétentes**
   - **ANSSI** : en cas d’incident critique touchant un OSE ou FSN (sous 72 heures).
   - **CNIL** : si des données personnelles ont été compromises (sous 72 heures).
   - **Forces de l’ordre (Police/Gendarmerie)** : dépôt de plainte avec le rapport forensic.
   - **Coordination internationale** si l’attaque provient de l’étranger (Europol, Interpol, CSIRT européen).

7. **Mise en œuvre des mesures correctives**
   - Application des correctifs de sécurité.
   - Revue des politiques de cybersécurité et sensibilisation des employés.
   - Tests post-incident pour s’assurer que la menace est éradiquée.

---

### **2. Constat Initial (Procès-Verbal Forensic)**  
Le constat documente les premières constatations techniques et doit être préparé rapidement pour répondre aux obligations de notification NIS et RGPD.

#### **Structure :**
- **En-tête :**
  - Identification de l’auteur (nom, fonction, qualifications, société).
  - Date, heure et lieu de l’intervention.
  - Référence à la demande d’analyse (ex. : mandat interne ou réquisition judiciaire).

- **Contexte :**
  - Description de l’incident (ex. : intrusion réseau, ransomware, exfiltration de données).
  - Statut de l’entreprise (OSE ou FSN, si applicable).

- **Méthodologie :**
  - Outils forensic utilisés (ex. : EnCase, Autopsy, Volatility).
  - Préservation de l’intégrité des preuves (hash MD5/SHA, documentation).

- **Résultats :**
  - Adresse IP identifiée.
  - Preuves associées (captures réseau, fichiers malveillants, logs).
  - Évaluation préliminaire de l’impact.

- **Conclusion :**
  - Synthèse des éléments constatés.
  - Signature de l’expert et, si possible, d’un huissier pour renforcer la recevabilité.

---

### **3. Rapport Forensic Détaillé**  
Destiné aux autorités compétentes (ANSSI, CNIL, forces de l’ordre) et intégrant les obligations NIS, RGPD et ISO 27037.

#### **Structure :**
- **Page de garde :**
  - Titre : "Rapport d’Analyse Forensic – Incident de Cybersécurité".
  - Nom de l’entreprise, date de l’incident, date du rapport.
  - Coordonnées de l’expert.

- **Introduction :**
  - Contexte de l’incident et impact.
  - Objectifs de l’analyse.
  - Références aux obligations légales (NIS, RGPD, ISO/IEC 27037).

- **Méthodologie :**
  - Équipements analysés.
  - Outils conformes aux normes.
  - Étapes de collecte, analyse et corrélation des preuves.

- **Résultats de l’analyse :**
  - **Chronologie (Timeline) :** Événements horodatés.
  - **Adresse IP :** Détails techniques et localisation indicative.
  - **Preuves :** Captures réseau, fichiers malveillants, logs système.
  - **Impact NIS et RGPD :** Analyse des perturbations et données compromises.

- **Conclusion :**
  - Résumé des preuves.
  - Actions recommandées (notification ANSSI, CNIL, dépôt de plainte).

- **Annexes :**
  - Captures d’écran, fichiers numériques, documentation de la chaîne de contrôle.

---

### **4. Transmission aux Autorités Compétentes**
- **ANSSI** : Notification obligatoire sous 72h pour les OSE et FSN.
- **CNIL** : Notification en cas de violation de données personnelles.
- **Forces de l’ordre** : Dépôt de plainte auprès de la BEFTI ou Section Cyber.
- **Coordination européenne** : Signalement via CSIRT ou Europol si nécessaire.

---

### **5. Exigences Normatives Applicables**
- **Directive NIS et loi française (2018-133)** : Sécurité des OSE et FSN.
- **RGPD (Règlement 2016/679/UE)** : Gestion des données personnelles.
- **ISO/IEC 27001** : Management de la Sécurité de l’Information.
- **ISO/IEC 27035** : Gestion des incidents de sécurité.
- **ISO/IEC 27037** : Collecte et analyse des preuves numériques.
- **ENISA Best Practices** : Guide européen des bonnes pratiques en cybersécurité.
