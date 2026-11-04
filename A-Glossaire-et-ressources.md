# Glossaire et ressources

> **Nature :** annexe de référence · **Usage :** tout au cours

Cette page rassemble les acronymes et les termes techniques du cours, avec leurs
définitions, et les ressources de référence — à garder sous la main pendant la
journée.

---

## Acronymes

| Sigle | Signification | En clair |
| --- | --- | --- |
| **ANSSI** | Agence nationale de la sécurité des systèmes d'information | l'autorité française de cybersécurité : guides, recommandations, retours d'expérience |
| **API** | Application Programming Interface | un point d'entrée programmatique d'une application |
| **APT** | Advanced Persistent Threat | une menace persistante avancée : un acteur bien outillé, patient, souvent porté par un État |
| **ATT&CK** | Adversarial Tactics, Techniques & Common Knowledge | la base de connaissances des gestes des attaquants, maintenue par le MITRE |
| **BC03** | bloc de compétences 03 | le bloc de la certification RNCP40573 auquel ce cours est adossé |
| **C25** | (code de la) compétence du bloc BC03 | la compétence visée par ce cours |
| **CERT** | Computer Emergency Response Team | l'équipe qui publie les avis de sécurité : CERT-FR en France, CERT-EU pour l'Union européenne |
| **CID** | Confidentialité, Intégrité, Disponibilité | les trois piliers de la sécurité : qui a vu quoi, qu'est-ce qui a été modifié, qu'est-ce qui n'est plus accessible |
| **CNIL** | Commission nationale de l'informatique et des libertés | l'autorité française de contrôle des données personnelles |
| **CSF** | Cybersecurity Framework | le cadre de référence du NIST : identifier, protéger, détecter, répondre, restaurer |
| **CVE** | Common Vulnerabilities and Exposures | l'identifiant normalisé d'une faille connue, comme CVE-2021-44228 (Log4Shell) |
| **DBIR** | Data Breach Investigations Report | l'étude annuelle de Verizon sur des milliers d'incidents réels |
| **DPO** | délégué à la protection des données | la personne qui suit les obligations RGPD au quotidien |
| **EBIOS** | Expression des Besoins et Identification des Objectifs de sécurité | la méthode française d'analyse de risques, publiée par l'ANSSI |
| **EISI** | Expert en informatique et systèmes d'information | le titre visé par le programme de formation |
| **IA** | intelligence artificielle | |
| **IAM** | Identity and Access Management | la gestion des identités et des accès : provisionnement, revue des droits, suppression des comptes |
| **MFA** | Multi-Factor Authentication | l'authentification multi-facteurs : une seconde preuve d'identité, en plus du mot de passe |
| **MITRE** | (nom d'organisme, ce n'est pas un sigle) | l'organisme de recherche américain qui maintient la base ATT&CK |
| **NIST** | National Institute of Standards and Technology | l'organisme américain de référence en matière de normes et de recommandations |
| **PME** | petite et moyenne entreprise | |
| **PSH** | Personnes en Situation de Handicap | l'accessibilité rend un service utilisable par tous |
| **QCM** | questionnaire à choix multiples | un format d'évaluation où l'on coche la bonne réponse |
| **RGAA** | Référentiel général d'amélioration de l'accessibilité | le référentiel français d'accessibilité numérique |
| **RGPD** | Règlement général sur la protection des données | le texte européen qui encadre le traitement des données personnelles |
| **RM** | Risk Management (méthode de gestion des risques) | la version en vigueur de la méthode EBIOS : EBIOS RM |
| **RNCP** | Répertoire national des certifications professionnelles | le registre des certifications : RNCP40573 est la certification visée ici |
| **TD** | travaux dirigés | une série d'exercices, souvent en séquence découverte |
| **TPE** | très petite entreprise | |
| **TP** | travaux pratiques | une mise en pratique — ici, aucun TP n'est noté : la journée est courte |
| **URL** | Uniform Resource Locator | l'adresse d'une ressource sur le web |
| **USB** | Universal Serial Bus | le port de connexion des périphériques |
| **UX** | expérience utilisateur (User Experience) | le confort d'usage de ceux qui utilisent le système au quotidien |
| **W3C** | World Wide Web Consortium | l'organisme qui standardise le web, dont les règles d'accessibilité |
| **WCAG** | Web Content Accessibility Guidelines | les règles d'accessibilité du W3C, référence internationale |

---

## Termes techniques clés

- **Actif** — ce qui a de la valeur pour l'organisation et mérite d'être protégé : des données, un système, une personne.
- **Avis d'arbitrage** — le court document qui dit ce qu'on met en place, ce qu'on écarte, et pourquoi.
- **Cloisonnement** — découper un système en zones pour qu'une compromission reste locale.
- **Correctif (patch)** — la modification qui supprime une faille connue.
- **Course patch / exploit** — la course entre le défenseur qui applique le correctif et l'attaquant qui écrit l'exploit.
- **Criticité** — ce que vaut un système à protéger, combinant valeur des données, exposition et impact métier.
- **Defense in depth (défense en profondeur)** — empiler des mesures indépendantes, pour qu'une défaillance isolée ne compromette pas le tout.
- **Donnée personnelle** — toute donnée qui identifie une personne, directement ou indirectement : nom, adresse e-mail, adresse IP, historique d'achats.
- **Exposition** — qui peut atteindre un système ou une donnée : tout Internet, le réseau interne, une seule équipe.
- **Fenêtre d'exposition** — la durée entre la publication d'un correctif et son application, pendant laquelle le système reste exposé.
- **Hameçonnage (phishing)** — le message qui piège la victime pour voler ses identifiants ou l'amener à payer.
- **Impact** — la conséquence concrète si un risque se réalise : activité arrêtée, données fuitées, clients touchés.
- **Kill chain (chaîne d'attaque)** — les cinq étapes d'une attaque : reconnaissance, intrusion, exploitation, persistance, exfiltration. Couper une seule étape fait échouer le reste.
- **Menace** — ce qui peut causer un dommage : un attaquant, un logiciel, une erreur humaine.
- **Moindre privilège (least privilege)** — chaque acteur ne dispose que du strict nécessaire, et rien de plus.
- **Rançongiciel (ransomware)** — le logiciel qui chiffre les données, puis réclame une rançon.
- **Responsable de traitement** — celui qui décide des finalités d'un traitement de données personnelles.
- **Risque** — ce qui peut arriver quand une menace rencontre une vulnérabilité ; on le juge sur sa probabilité et sa gravité.
- **Sous-traitant** — celui qui traite des données personnelles pour le compte d'un responsable de traitement : hébergeur, prestataire d'envoi, éditeur.
- **Surface d'attaque** — l'ensemble de ce qu'un attaquant peut atteindre, toucher ou interroger.
- **Violation de données personnelles** — un accès, une perte, une altération ou une divulgation non autorisée de données personnelles.
- **Vulnérabilité** — la faiblesse qu'une menace peut exploiter : un défaut de code, une configuration oubliée, un mot de passe partagé.
- **Zero Trust (zéro confiance)** — la confiance n'est plus déduite de la position : elle est prouvée à chaque requête, pour une durée et un périmètre limités.
- **Zones de confiance** — un regroupement de composants qui se font confiance, délimité par des frontières justifiées.

---

## Ressources utiles

### Cadres, méthodes et référentiels

- **ANSSI** — <https://cyber.gouv.fr/> — guides, recommandations et retours d'expérience en français.
- **Panorama de la cybermenace** (ANSSI) — <https://cyber.gouv.fr/nous-connaitre/publications/panoramas-de-la-cybermenace/> — les tendances observées en France, chaque année.
- **EBIOS RM** (ANSSI) — <https://cyber.gouv.fr/securisation/analyse-des-risques/methode-ebios-rm/> — la méthode française d'analyse de risques, de bout en bout.
- **NIST Cybersecurity Framework** — <https://www.nist.gov/cyberframework> — le cadre qui organise la sécurité en fonctions, pour situer sa maturité.
- **MITRE ATT&CK** — <https://attack.mitre.org/> — les tactiques et techniques des attaquants, décrites par comportements observables.

### Données personnelles

- **CNIL** — <https://www.cnil.fr/> — l'autorité française de contrôle : fiches pratiques, sanctions, accompagnement.
- **Le RGPD, présenté par la CNIL** — <https://www.cnil.fr/fr/reglement-europeen-protection-donnees> — le texte et ses obligations, traduits en cas concrets.

### Avis de sécurité et études

- **CERT-FR** — <https://cert.cyber.gouv.fr/> — les avis et alertes de sécurité en France.
- **DBIR** (Verizon) — <https://www.verizon.com/business/resources/reports/dbir/> — l'étude annuelle de milliers d'incidents réels.

### Accessibilité

- **RGAA** — <https://accessibilite.numerique.gouv.fr/> — le référentiel français d'accessibilité numérique.
- **WCAG** (W3C) — <https://www.w3.org/WAI/standards-guidelines/wcag/> — les règles d'accessibilité, référence internationale.

---

## Dans ce cours

- Les exercices, le TD et l'exercice d'intégration de fin de journée : le dossier `tp/`, avec leurs corrigés dans `tp/corrige/`.
