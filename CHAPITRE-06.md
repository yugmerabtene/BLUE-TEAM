### CHAPITRE-06 Cours complet sur le chapitre : **Politiques de sécurité et procédures de la Blue Team**

---

#### **Introduction**
La Blue Team est une équipe de défense en cybersécurité chargée de protéger les systèmes, les réseaux et les données d'une organisation contre les menaces internes et externes. Pour assurer une défense efficace, la Blue Team s'appuie sur des politiques de sécurité et des procédures bien définies. Ce chapitre aborde les politiques et procédures clés, ainsi que leur mise en œuvre pratique.

---

### **Théorie**

#### **1. Politiques de sécurité**
Les politiques de sécurité sont des documents formels qui définissent les règles et les directives pour protéger les actifs informationnels d'une organisation. Elles servent de cadre pour guider les comportements et les actions des employés, ainsi que pour assurer la conformité aux réglementations.

##### **a. Acceptable Use Policy (AUP)**
L'AUP définit ce qui est acceptable et ce qui ne l'est pas en matière d'utilisation des ressources informatiques de l'organisation (ordinateurs, réseaux, logiciels, etc.). Elle vise à prévenir les abus et à protéger l'organisation contre les risques liés à une mauvaise utilisation.

**Points clés d'une AUP :**
- Utilisation autorisée des ressources (ex : professionnelle uniquement).
- Interdiction d'accéder à des contenus illégaux ou inappropriés.
- Obligation de respecter les lois sur la propriété intellectuelle.
- Interdiction de partager des informations sensibles sans autorisation.
- Sanctions en cas de non-respect (avertissement, suspension, licenciement).

##### **b. Politique de mot de passe**
Une politique de mot de passe définit les règles pour créer, gérer et protéger les mots de passe. Elle est essentielle pour empêcher les accès non autorisés.

**Éléments d'une politique de mot de passe :**
- Longueur minimale (ex : 12 caractères).
- Complexité requise (majuscules, minuscules, chiffres, caractères spéciaux).
- Durée de validité (ex : changement tous les 90 jours).
- Historique des mots de passe (ex : interdiction de réutiliser les 5 derniers mots de passe).
- Verrouillage du compte après un nombre d'échecs (ex : 5 tentatives).
- Interdiction d'utiliser des mots de passe faibles (ex : "123456", "password").

---

#### **2. Procédures de sécurité**
Les procédures de sécurité sont des étapes détaillées pour répondre à des situations spécifiques, comme un incident de sécurité ou la gestion des correctifs.

##### **a. Réponse aux incidents**
La réponse aux incidents est un processus structuré pour identifier, contenir, éradiquer et récupérer après un incident de sécurité. Elle vise à minimiser les dommages et à restaurer les opérations normales.

**Étapes clés :**
1. **Préparation** : Former l'équipe, définir les rôles, et préparer les outils.
2. **Identification** : Détecter et analyser l'incident (ex : phishing, malware).
3. **Containment** : Isoler les systèmes affectés pour empêcher la propagation.
4. **Éradication** : Supprimer la cause de l'incident (ex : supprimer un malware).
5. **Récupération** : Restaurer les systèmes et vérifier leur intégrité.
6. **Post-incident** : Analyser l'incident, documenter les leçons apprises, et mettre à jour les procédures.

##### **b. Gestion des correctifs**
La gestion des correctifs consiste à identifier, tester, et appliquer des mises à jour pour corriger les vulnérabilités logicielles. Elle est cruciale pour prévenir les exploits.

**Étapes clés :**
1. **Identification** : Scanner les systèmes pour détecter les vulnérabilités.
2. **Évaluation** : Prioriser les correctifs en fonction des risques.
3. **Test** : Tester les correctifs dans un environnement de test avant déploiement.
4. **Déploiement** : Appliquer les correctifs sur les systèmes de production.
5. **Vérification** : Confirmer que les correctifs ont été appliqués avec succès.

---

### **Exercice**

#### **1. Rédigez une politique de mot de passe pour une entreprise**

**Politique de mot de passe pour l'entreprise XYZ :**
1. **Longueur minimale** : 12 caractères.
2. **Complexité** : Doit inclure au moins une majuscule, une minuscule, un chiffre et un caractère spécial.
3. **Durée de validité** : Les mots de passe doivent être changés tous les 90 jours.
4. **Historique** : Les 5 derniers mots de passe ne peuvent pas être réutilisés.
5. **Verrouillage du compte** : Le compte est verrouillé après 5 tentatives infructueuses.
6. **Interdiction** : Les mots de passe courants (ex : "password", "123456") sont interdits.
7. **Stockage** : Les mots de passe ne doivent pas être écrits ou partagés.
8. **Authentification à deux facteurs (2FA)** : Obligatoire pour les accès sensibles.

---

#### **2. Créez une procédure de réponse à un incident de phishing**

**Procédure de réponse à un incident de phishing :**
1. **Identification** :
   - Un employé signale un email suspect.
   - L'équipe de sécurité vérifie l'email (en-têtes, liens, pièces jointes).

2. **Containment** :
   - Bloquer l'expéditeur malveillant.
   - Supprimer l'email des boîtes de réception concernées.
   - Isoler les systèmes compromis.

3. **Éradication** :
   - Analyser les liens et pièces jointes pour détecter des malwares.
   - Réinitialiser les mots de passe des comptes compromis.

4. **Récupération** :
   - Restaurer les systèmes affectés à partir de sauvegardes.
   - Informer les employés de l'incident et fournir des conseils de prévention.

5. **Post-incident** :
   - Documenter l'incident et les actions prises.
   - Former les employés à reconnaître les emails de phishing.
   - Mettre à jour les filtres anti-spam et les politiques de sécurité.

---

### **TP : Mise en œuvre d'une politique de mot de passe sur un domaine Active Directory**

#### **Objectif**
Configurer une politique de mot de passe sur un domaine Active Directory pour renforcer la sécurité des comptes utilisateurs.

#### **Étapes**

1. **Ouvrir l'outil de gestion des stratégies de groupe (GPO) :**
   - Lancer "Gestion des stratégies de groupe" depuis le serveur Windows.

2. **Créer une nouvelle stratégie de groupe :**
   - Cliquer droit sur "Objets de stratégie de groupe" > "Nouveau".
   - Nommer la stratégie (ex : "Politique de mot de passe").

3. **Configurer la politique de mot de passe :**
   - Cliquer droit sur la nouvelle stratégie > "Modifier".
   - Naviguer vers : **Configuration ordinateur > Stratégies > Paramètres Windows > Paramètres de sécurité > Stratégies de comptes > Stratégie de mot de passe**.
   - Configurer les paramètres suivants :
     - **Longueur minimale du mot de passe** : 12 caractères.
     - **Complexité du mot de passe** : Activée.
     - **Durée de validité maximale** : 90 jours.
     - **Historique des mots de passe** : 5 mots de passe mémorisés.
     - **Verrouillage du compte** : 5 tentatives infructueuses, durée de verrouillage : 30 minutes.

4. **Appliquer la stratégie au domaine :**
   - Lier la stratégie au domaine ou à l'unité d'organisation (OU) concernée.

5. **Tester la politique :**
   - Créer un compte utilisateur et essayer de définir un mot de passe non conforme.
   - Vérifier que la politique est appliquée.

---
