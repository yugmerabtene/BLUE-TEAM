### 1. MITRE ATT&CK
- **Description** : Une base de connaissances détaillant les tactiques, techniques et procédures (TTPs) utilisées par les attaquants, organisée en une matrice avec des catégories comme "Initial Access", "Persistence", "Exfiltration", etc.
- **Détails** : Couvre les attaques sur les entreprises, le cloud, les mobiles et les systèmes industriels (ICS). Basé sur des observations réelles, il est constamment mis à jour.
- **Forces** : Granularité élevée, orienté sur les comportements adverses, utilisable pour la détection, la chasse aux menaces et la réponse aux incidents.
- **Différences** : Contrairement à d'autres, il ne se concentre pas sur une séquence d’attaque ou une méthodologie de défense, mais sur un catalogue exhaustif de techniques. Plus technique que stratégique.
- **Usage** : SOC, chasse aux menaces, simulation d’attaques (red teaming).

---

### 2. Cyber Kill Chain (Lockheed Martin)
- **Description** : Modèle en 7 étapes chronologiques d’une cyberattaque : Reconnaissance, Weaponization, Delivery, Exploitation, Installation, Command & Control, Actions on Objectives.
- **Détails** : Développé pour anticiper et bloquer les attaques à chaque étape, avec une vision linéaire des intrusions.
- **Forces** : Simplicité, focus sur la prévention et la disruption précoce.
- **Différences** : Plus séquentiel et moins détaillé sur les TTPs que MITRE ATT&CK. Moins adapté aux attaques non linéaires ou persistantes (APT).
- **Usage** : Défense proactive, formation des équipes de sécurité.

---

### 3. Unified Kill Chain
- **Description** : Une extension du Cyber Kill Chain avec 18 étapes, intégrant des boucles et des phases post-compromission pour refléter la complexité des attaques modernes.
- **Détails** : Combine des éléments du Kill Chain et d’ATT&CK, comme la préparation, l’exploitation initiale, la persistance et l’expansion.
- **Forces** : Plus flexible et réaliste que le Kill Chain original, adapté aux attaques itératives.
- **Différences** : Moins granulaire qu’ATT&CK, mais offre une structure narrative plus complète que le Kill Chain classique.
- **Usage** : Modélisation d’attaques complexes, analyse forensique.

---

### 4. Diamond Model of Intrusion Analysis
- **Description** : Modèle analytique basé sur quatre éléments interconnectés : Adversaire, Infrastructure, Capacités, Victime.
- **Détails** : Met l’accent sur les relations entre ces éléments pour mapper une intrusion et attribuer les attaques.
- **Forces** : Idéal pour le renseignement sur les menaces (threat intelligence) et l’attribution.
- **Différences** : Moins axé sur les techniques (comme ATT&CK) ou les étapes (comme Kill Chain), mais sur la dynamique et le contexte de l’attaque.
- **Usage** : Analyse stratégique, profiling des attaquants.

---

### 5. NIST Cybersecurity Framework (NIST CSF)
- **Description** : Cadre basé sur 5 fonctions : Identifier, Protéger, Détecter, Répondre, Récupérer. Il fournit des lignes directrices pour gérer les risques cybernétiques.
- **Détails** : Organisé en catégories (ex. : gestion des identités) et sous-catégories avec des références aux normes comme ISO 27001.
- **Forces** : Approche holistique et organisationnelle, alignée sur la conformité.
- **Différences** : Moins technique qu’ATT&CK, plus axé sur la gouvernance et les processus que sur les TTPs spécifiques.
- **Usage** : Gestion des risques, audits, conformité réglementaire.

---

### 6. STRIDE (Microsoft)
- **Description** : Modèle de menace basé sur 6 catégories : Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege.
- **Détails** : Utilisé pour identifier les menaces potentielles dans un système ou une application en développement.
- **Forces** : Simple, orienté sur les impacts et les vulnérabilités plutôt que sur les comportements des attaquants.
- **Différences** : Contrairement à ATT&CK ou Kill Chain, il n’est pas basé sur des attaques réelles, mais sur une analyse théorique des risques.
- **Usage** : Threat modeling, sécurité des logiciels.

---

### 7. DREAD (Microsoft)
- **Description** : Méthodologie d’évaluation des risques basée sur 5 critères : Damage, Reproducibility, Exploitability, Affected Users, Discoverability.
- **Détails** : Fournit un score pour prioriser les menaces identifiées (souvent utilisé avec STRIDE).
- **Forces** : Quantitative, aide à hiérarchiser les réponses aux menaces.
- **Différences** : Complémentaire à STRIDE, mais pas un modèle d’attaque comme ATT&CK ou Kill Chain ; il évalue plutôt les conséquences.
- **Usage** : Gestion des vulnérabilités, priorisation des correctifs.

---

### 8. PASTA (Process for Attack Simulation and Threat Analysis)
- **Description** : Méthodologie en 7 étapes pour simuler des attaques et analyser les menaces du point de vue des attaquants et des défenseurs.
- **Détails** : Inclut l’analyse des objectifs métier, la modélisation des menaces et l’évaluation des risques.
- **Forces** : Orienté sur les applications et les risques métier, avec une approche collaborative.
- **Différences** : Plus méthodologique qu’ATT&CK (qui est un catalogue) et plus spécifique aux actifs métier que Kill Chain.
- **Usage** : Développement sécurisé, analyse des risques spécifiques.

---

### 9. OCTAVE (Operationally Critical Threat, Asset, and Vulnerability Evaluation)
- **Description** : Cadre axé sur l’évaluation des risques en trois phases : identification des actifs, analyse des menaces, définition des stratégies de mitigation.
- **Détails** : Développé par CERT, il est centré sur les besoins organisationnels.
- **Forces** : Prend en compte les aspects humains et opérationnels, pas seulement techniques.
- **Différences** : Moins détaillé sur les TTPs qu’ATT&CK, plus orienté sur la gestion des risques que sur l’analyse des attaques.
- **Usage** : Petites et moyennes entreprises, audits de sécurité.

---

### 10. Open Source Security Testing Methodology Manual (OSSTMM)
- **Description** : Cadre pour tester la sécurité des systèmes, réseaux et processus, avec une approche basée sur les contrôles et les vecteurs d’attaque.
- **Détails** : Mesure l’efficacité des défenses en termes de visibilité, accès et confiance.
- **Forces** : Approche empirique et mesurable, pas seulement théorique.
- **Différences** : Moins axé sur les TTPs adverses (comme ATT&CK) et plus sur l’évaluation des défenses existantes.
- **Usage** : Tests de pénétration, audits de sécurité.

---

### Comparaison Globale
- **Granularité technique** : ATT&CK excelle avec ses TTPs détaillés, suivi par Unified Kill Chain. NIST CSF et OCTAVE sont plus abstraits.
- **Séquence vs Catalogue** : Kill Chain et Unified Kill Chain sont séquentiels, ATT&CK est un catalogue non linéaire.
- **Focus** : Diamond Model (attribution), STRIDE/DREAD (développement), NIST CSF/OCTAVE (gouvernance), PASTA (risques métier).
- **Usage** : ATT&CK et Kill Chain pour les SOC, NIST pour la conformité, STRIDE/PASTA pour les développeurs, Diamond pour l’intelligence.
