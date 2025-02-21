### LAB-05 : Gestion des Incidents avec un IRP (Incident Response Plan)

**Objectifs du Lab :**  
1. Définir et créer un Incident Response Plan (IRP).  
2. Simuler un incident de sécurité.  
3. Appliquer l'IRP et évaluer son efficacité.  

---

## I. Préparation  

### A. Environnement de test  
- Mettre en place un environnement de test sécurisé (réseau fictif avec des systèmes vulnérables pour la simulation).  
- Utiliser des machines virtuelles pour la simulation d’incidents.  

### B. Outils à utiliser  
- **SIEM** (Security Information and Event Management) : Suricata ou ELK Stack.  
- **Analyse de logs** : Wazuh ou Splunk.  
- **Scanner de vulnérabilité** : Nessus ou OpenVAS.  
- **Communication** : Discord, Slack ou Microsoft Teams (fictif ou réel).  

---

## II. Définition de l'IRP (Incident Response Plan)

1. **Rôles et Responsabilités**  
   Définir clairement les rôles suivants :  
   - Incident Commander : Dirige la réponse.  
   - Analystes de Sécurité : Analyzent les données et identifient la source de l'incident.  
   - Équipe de Communication : Gère les communications internes et externes.  
   - Responsable IT : Assure la continuité des systèmes critiques.  

2. **Procédures de Communication**  
   - Canal interne : Slack privé ou mailing list interne.  
   - Communication externe : Communiqué de presse ou e-mails prédéfinis pour les clients, selon la gravité.  

3. **Outils et Ressources**  
   - SIEM pour la surveillance continue.  
   - Playbooks pour chaque type d'incident (ex : attaque par phishing, ransomware).  

4. **Checklists pour la réponse aux incidents**  
   Exemple de checklist :  
   - Identification de l’incident.  
   - Classification selon la gravité.  
   - Containment (confinement du système infecté).  
   - Eradication (nettoyage).  
   - Récupération.  
   - Rapport post-incident.  

5. **Plan de Continuité**  
   - Mise en place de sauvegardes automatiques.  
   - Redirection du trafic vers des serveurs de secours.  

---

## III. Simulation d’un Incident  
1. **Type d’incident simulé :** Ransomware détecté sur un poste utilisateur.  
2. **Étapes de simulation :**  
   a. Détection d'un fichier malveillant sur le réseau.  
   b. SIEM génère une alerte critique.  
   c. Équipe de sécurité suit l'IRP.  

---

## IV. Application de l'IRP  

1. **Identification et notification**  
   - Analyste reçoit l’alerte via le SIEM.  
   - Incident Commander notifie l’équipe et initie le plan.  

2. **Confinement**  
   - Déconnecter la machine infectée du réseau.  
   - Isoler le système compromis.  

3. **Eradication et nettoyage**  
   - Supprimer les fichiers infectés.  
   - Effectuer une analyse complète des systèmes adjacents.  

4. **Récupération**  
   - Restaurer les données à partir des sauvegardes.  
   - Vérifier l’intégrité des systèmes avant de les remettre en production.  

5. **Rapport post-incident**  
   - Rédiger un rapport complet des actions entreprises.  
   - Revoir l’IRP et identifier des améliorations potentielles.  

---

## V. Évaluation et Amélioration  
1. **Questions d'évaluation :**  
   - L'alerte a-t-elle été détectée à temps ?  
   - La communication interne a-t-elle été efficace ?  
   - Le confinement a-t-il été rapide ?  
   - Des étapes ont-elles été oubliées ?  

2. **Améliorations proposées :**  
   - Mise à jour des procédures selon les retours d'expérience.  
   - Ajout d'outils ou de ressources supplémentaires.  
   - Formation régulière des équipes sur les nouveaux types de menaces.  

