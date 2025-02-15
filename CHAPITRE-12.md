### CHAPITRE 12 : Gestion de la sécurité des périphériques

---

## 1. **Théorie**

La gestion de la sécurité des périphériques est un aspect crucial de l’administration des systèmes et réseaux. Avec l’augmentation des périphériques mobiles et des objets connectés (IoT), il est essentiel de mettre en place des stratégies efficaces pour protéger ces éléments contre les cybermenaces.

### 1.1. **Techniques de sécurité**

#### a) **MDM (Mobile Device Management)**
Le Mobile Device Management est une solution logicielle permettant de gérer, sécuriser et surveiller les appareils mobiles dans un réseau. Il offre des fonctionnalités telles que :
- Le déploiement de politiques de sécurité.
- Le chiffrement des données.
- La gestion des applications installées.
- Le verrouillage ou l’effacement des appareils en cas de perte ou de vol.

#### b) **Mise à jour des firmwares**
Le firmware est un logiciel embarqué qui contrôle le matériel d’un appareil. La mise à jour régulière du firmware est essentielle pour corriger les vulnérabilités de sécurité connues. Cela permet :
- De protéger contre les attaques exploitant des failles du firmware.
- D'améliorer les performances et la compatibilité de l’appareil.

#### c) **Contrôle d’accès**
Le contrôle d’accès vise à limiter l'accès aux périphériques selon des règles définies. Cela inclut :
- L’utilisation de listes de contrôle d’accès (ACL).
- L’authentification multi-facteurs (MFA).
- La segmentation réseau pour isoler les périphériques sensibles.

---

### 1.2. **Surveillance**

#### Détection des périphériques non autorisés
Une gestion proactive inclut la surveillance et la détection de tout appareil non autorisé connecté au réseau. Les solutions incluent :
- L’utilisation d’outils de surveillance comme **Nmap**, **Wireshark**, ou des systèmes de détection d’intrusion (IDS).
- La configuration d'alertes pour les connexions suspectes.
- Le blocage automatique des périphériques inconnus à l’aide de solutions comme **802.1X**.

---

## 2. **Exercice**

1. **Configurer un MDM pour gérer des appareils mobiles :**
   - Choisissez une solution MDM (ex. : Microsoft Intune, VMware Workspace ONE, Jamf).
   - Configurez des politiques pour restreindre les applications, forcer le chiffrement des données et imposer des mises à jour régulières.
   - Testez le verrouillage à distance d’un appareil.

2. **Identifier les risques liés aux périphériques IoT :**
   - Faites une liste des risques (ex. : attaques DDoS, prise de contrôle à distance, manque de chiffrement).
   - Proposez des solutions pour minimiser ces risques (ex. : mise à jour régulière, isolation réseau, authentification forte).

---

## 3. **Travaux Pratiques (TP)**

**Sujet : Sécuriser un réseau IoT avec des règles de pare-feu.**

### Étapes :
1. **Scénario** : Vous gérez un réseau comportant plusieurs objets connectés (caméras IP, thermostats intelligents, etc.). Vous devez protéger ces appareils contre des attaques externes.
2. **Préparation** :
   - Configurez un pare-feu (ex. : pfSense, Cisco ASA).
   - Identifiez les adresses IP des appareils IoT.
3. **Configuration** :
   - Bloquez tout trafic entrant vers les périphériques IoT, sauf depuis des adresses IP autorisées.
   - Autorisez uniquement les communications sortantes nécessaires (par exemple, vers des serveurs de mise à jour).
   - Configurez des règles de journalisation pour surveiller les tentatives de connexion.
4. **Test** :
   - Essayez de vous connecter à un appareil IoT depuis une adresse non autorisée.
   - Vérifiez que les alertes et journaux du pare-feu enregistrent les tentatives bloquées.

---

## 4. **Résumé et conseils pratiques**

- La gestion des périphériques doit être proactive : utilisez des outils de gestion comme les MDM pour les mobiles et surveillez régulièrement votre réseau.
- Maintenez tous les appareils à jour, y compris leurs firmwares.
- Appliquez des politiques strictes de contrôle d’accès et isolez les appareils IoT dans des sous-réseaux dédiés.
- Testez régulièrement la sécurité de votre réseau avec des audits ou des simulations d’attaques.
