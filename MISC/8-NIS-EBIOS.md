### La Directive NIS (Network and Information Security)
- **Qu’est-ce que c’est ?**  
  La Directive NIS est une législation européenne adoptée en 2016 (Directive 2016/1148), remplacée depuis janvier 2023 par la **NIS2** (Directive 2022/2555). Elle vise à harmoniser et renforcer la cybersécurité au sein de l’Union européenne en établissant un niveau commun élevé de sécurité des réseaux et des systèmes d’information.
- **Objectifs** : 
  - Améliorer les capacités nationales en cybersécurité des États membres.
  - Renforcer la résilience des **opérateurs de services essentiels (OSE)** et des **fournisseurs de services numériques (FSN)** face aux cybermenaces.
  - Promouvoir la coopération entre les États membres via des réseaux comme les CSIRT (Computer Security Incident Response Teams).
- **Obligations principales** : 
  - Les OSE (ex. : énergie, santé, transports) et FSN (ex. : cloud, marketplaces) doivent mettre en place des mesures de sécurité adaptées aux risques.
  - Signalement obligatoire des incidents significatifs aux autorités compétentes (en France, l’ANSSI).
  - Respect des exigences transposées dans le droit national (en France, via la **loi CIIP** et le décret NIS de 2018).
- **Évolution avec NIS2** : 
  - Élargissement du scope (plus de secteurs couverts, incluant les entités "essentielles" et "importantes").
  - Sanctions plus strictes (jusqu’à 10M€ ou 2% du CA annuel mondial).
  - Accent sur la gestion des risques supply chain et la gouvernance.

- **Autorité en France** : L’**ANSSI** (Agence Nationale de la Sécurité des Systèmes d’Information) est le point de contact principal pour la mise en œuvre de NIS.

---

### EBIOS (Expression des Besoins et Identification des Objectifs de Sécurité)
- **Qu’est-ce que c’est ?**  
  EBIOS est une méthode française d’analyse et de gestion des risques en cybersécurité, développée par l’ANSSI. La version actuelle, **EBIOS Risk Manager** (2018), est conçue pour identifier, évaluer et traiter les risques liés aux systèmes d’information de manière structurée et collaborative.
- **Objectifs** : 
  - Comprendre les risques cybernétiques auxquels vous êtes exposé.
  - Définir des objectifs de sécurité adaptés à vos besoins et à votre contexte.
  - Produire un plan d’action pour réduire les risques à un niveau acceptable.
- **Méthodologie** : 
  1. **Cadrage et socle de sécurité** : Définir le périmètre et les enjeux.
  2. **Sources de risques** : Identifier les acteurs (attaquants, partenaires) et leurs intentions.
  3. **Scénarios stratégiques** : Construire des scénarios d’attaque probables.
  4. **Scénarios opérationnels** : Détail technique des menaces (ex. : via MITRE ATT&CK).
  5. **Traitement des risques** : Décider des mesures (acceptation, réduction, transfert).
- **Points forts** : 
  - Approche collaborative impliquant toutes les parties prenantes (techniques, métiers, direction).
  - Alignée sur les standards internationaux (ISO 27005) et adaptable à NIS.
  - Outil gratuit et soutenu par l’ANSSI.

---

### Comparaison et Complémentarité

| **Aspect**                | **Directive NIS**                          | **EBIOS Risk Manager**                    |
|---------------------------|--------------------------------------------|-------------------------------------------|
| **Nature**                | Cadre réglementaire européen              | Méthode d’analyse de risques              |
| **Objectif**              | Imposer des exigences de cybersécurité    | Fournir une démarche pour gérer les risques |
| **Portée**                | OSE, FSN, entités essentielles/importantes | Toute organisation (pas de restriction)   |
| **Obligation**            | Juridique (sanctions en cas de non-conformité) | Volontaire, mais recommandé par l’ANSSI   |
| **Focus**                 | Conformité et résilience opérationnelle   | Identification et traitement des risques  |
| **Application en France** | Supervisée par l’ANSSI                    | Développée et promue par l’ANSSI          |

- **Différences** : 
  - NIS est une obligation légale qui fixe des objectifs généraux de sécurité et de notification, sans préciser "comment" les atteindre. EBIOS, en revanche, est une méthode concrète pour répondre à ces exigences en analysant les risques de manière systématique.
  - NIS s’applique à des entités spécifiques définies par la loi, tandis qu’EBIOS peut être utilisé par n’importe quelle organisation, même hors cadre réglementaire.

- **Complémentarité** : 
  - Si vous êtes un OSE ou un FSN soumis à NIS, EBIOS vous aide à remplir vos obligations en identifiant les risques spécifiques à vos systèmes et en définissant des mesures de sécurité proportionnées (exigence clé de NIS/NIS2).
  - L’ANSSI recommande souvent EBIOS comme outil pour se conformer à NIS, car il permet de documenter vos choix de sécurité de manière traçable et justifiable face aux audits.

---

### Recommandation Pour Vous
- **Si vous êtes soumis à NIS** (par exemple, un OSE dans l’énergie ou un FSN comme un fournisseur cloud) : Utilisez **EBIOS Risk Manager** pour structurer votre démarche de conformité. Cela vous permettra de cartographier vos risques, de justifier vos mesures de sécurité auprès de l’ANSSI, et de répondre aux exigences de signalement d’incidents.
- **Si vous n’êtes pas soumis à NIS** : EBIOS reste pertinent pour renforcer votre cybersécurité de manière proactive, en alignement avec les bonnes pratiques françaises.

** Documentation : https://cyber.gouv.fr/sites/default/files/document/20240901_Guide-EBIOS-RM-V1.5.pdf