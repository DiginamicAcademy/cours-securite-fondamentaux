[← Chapitre précédent](03-cid-et-vocabulaire.md) · [Sommaire](Readme.md) · [Chapitre suivant →](05-modeles-de-securite.md)

# Le paysage de la cybersécurité — qui attaque, comment, et à quelle vitesse

> Un lycéen qui lance des attaques par curiosité, ou un groupe financé par un
> État qui travaille sur des mois. Deux menaces très différentes, deux défenses
> très différentes. Avant de se protéger, il faut savoir **qui l'on cherche à
> tenir éloigné** — et à quelle vitesse le jeu se joue.

**Durée :** ≈ 20 min (lecture ≈ 12 min + atelier 5 min + réflexion) · **Prérequis :** [Vocabulaire du risque](03-cid-et-vocabulaire.md)

<!-- MODE TD : 🟢 découverte (accroche + §I, les acteurs) → ✅ correction (atelier d'attribution, §I) → 📘 cours (§II la kill chain, §III la course patch / exploit) → 🔵 application (reconstitution de kill chain — pas de TP dédié pour ce chapitre) -->

---

## Objectifs

À l'issue de ce chapitre, vous serez capable de :

- **Associer** chaque type d'acteur malveillant à ses motivations et à ses moyens.
- **Décrire** les étapes d'une attaque avec la kill chain simplifiée.
- **Relier** chaque étape de la kill chain à une mesure de défense.
- **Analyser** pourquoi la vitesse de réaction décide de l'avantage entre attaquants et défenseurs.

---

## I. Les acteurs

Derrière le mot « pirate », il y a des réalités très différentes. Ce qui les
sépare : la **motivation** (pourquoi), les **moyens** (avec quoi), et le
**temps** qu'ils peuvent y consacrer.

| Acteur | Motivation | Moyens | Cibles typiques |
| --- | --- | --- | --- |
| **Le curieux** (script kiddie) | se prouver quelque chose, s'amuser | outils téléchargés, scans automatisés | sites peu protégés, défiguration |
| **Le cybercriminel** | l'argent | rançongiciels, revente de données, hameçonnage de masse | entreprises, hôpitaux, collectivités |
| **L'hacktiviste** | une idéologie, une protestation | défiguration, fuite de documents | organisations politiques, médias |
| **L'espion industriel** | un avantage commercial | campagnes ciblées, moissonnage prolongé | laboratoires, industriels, brevets |
| **L'APT (Advanced Persistent Threat)** | une stratégie d'État | moyens étendus, patience, outils sur mesure | infrastructures critiques, administrations |

Deux remarques utiles pour la suite :

- Les moyens montent vite avec la motivation. Un outil de curieux est bruyant et
  grossier ; une APT (Advanced Persistent Threat) prépare son intrusion pendant
  des mois et sait rester invisible.
- **L'attribution est difficile.** Savoir qu'une attaque a eu lieu est une chose ;
  savoir qui la pilote en est une autre, et les faux indices sont monnaie
  courante. On défend d'abord contre des **méthodes**, pas contre des noms.

> 🧪 **Atelier rapide (5 min)**
>
> Associez chaque scénario à l'acteur le plus probable, et justifiez en une
> ligne : (a) des cartes bancaires revendues sur un forum ; (b) des documents
> internes publiés pour protester ; (c) le site d'une mairie défiguré avec un
> outil téléchargé ; (d) les plans d'un prototype disparus après une campagne
> d'e-mails ciblée. Terminez en disant ce qui rend votre attribution
> **incertaine**.

---

## II. La kill chain simplifiée

Le terme **kill chain** (« chaîne d'attaque ») vient du vocabulaire militaire :
une opération réussie enchaîne des étapes, et couper une seule d'entre elles
suffit à faire échouer le reste. En version simplifiée, une attaque informatique
comporte cinq étapes :

![La kill chain simplifiée : reconnaissance, intrusion, exploitation, persistance, exfiltration](assets/kill-chain-simplifiee.svg)

| Étape | Ce que fait l'attaquant | Où se défendre |
| --- | --- | --- |
| **Reconnaissance** | observer : site web, profils professionnels, adresses e-mail publiées, dépôts de code | réduire ce qui est exposé, sensibiliser aux publications |
| **Intrusion** | entrer : hameçonnage, identifiants volés, faille publique non corrigée | authentification multi-facteurs, correctifs, filtrage |
| **Exploitation** | agir : exécuter du code, élever ses privilèges, atteindre d'autres systèmes | cloisonnement, moindre privilège, journalisation |
| **Persistance** | rester : créer un compte, planifier une tâche, installer une porte dérobée | revue des comptes, surveillance des changements |
| **Exfiltration** | sortir : copier les données vers l'extérieur, souvent en petites quantités | contrôle des flux sortants, chiffrement, détection des volumes anormaux |

Deux enseignements se dégagent de cette chaîne :

1. **La reconnaissance n'est pas anodine.** Une annonce de recrutement qui détaille
   la stack technique, un dépôt Git public, un profil professionnel complet : tout
   cela alimente l'étape suivante. La première étape se défend en réduisant ce
   qu'on publie.
2. **Chaque étape est une occasion de couper.** Une intrusion sans exploitation
   reste sans effet ; une exploitation sans persistance se voit plus vite. La
   défense n'a pas à gagner partout — elle doit gagner **une fois** sur la chaîne.

> [!TIP]
> Pour analyser un incident passé, reconstituez sa kill chain étape par étape, en
> remontant depuis l'impact. À chaque étape, demandez quelle mesure aurait coupé
> la chaîne ici : c'est votre liste de mesures à prioriser.

---

## III. La course patch / exploit

Quand une faille est publiée, deux courses s'engagent : le défenseur qui
**applique le correctif**, l'attaquant qui **écrit l'exploit**. Et la deuxième
course va plus vite.

L'exemple de **WannaCry** (mai 2017) reste la leçon la plus nette : la faille
utilisée avait été corrigée par l'éditeur dès mars 2017. En deux mois, un ver
automatisé l'a exploitée pour paralyser des hôpitaux, des entreprises et des
administrations dans le monde — celles qui n'avaient pas encore appliqué le
correctif. Le problème n'était pas la technique : c'était le **délai**.

Le même scénario s'est rejoué avec **Log4Shell** (décembre 2021), une faille
dans une bibliothèque de journalisation très répandue, identifiée
CVE-2021-44228 dans la nomenclature CVE (Common Vulnerabilities and Exposures) :
exploitée dans le monde entier quelques heures après sa publication, alors que
les correctifs mettaient des semaines à se déployer.

D'où trois réflexes :

- **Le temps de réaction compte plus que la perfection.** Un correctif appliqué
  en quelques heures vaut mieux qu'une protection idéale jamais déployée.
- **La fenêtre d'exposition se mesure.** Entre la publication d'un correctif et
  son application, le système est exposé : cette durée est un indicateur de
  sécurité à part entière.
- ⚠️ **À ARBITRER** — **L'IA (intelligence artificielle) accélère les deux
  camps.** Elle aide à générer des exploits, à tester des variantes et à
  automatiser les scans ; elle aide aussi à trier les alertes, à détecter les
  anomalies et à rédiger les correctifs. L'avantage reste au camp qui exécute le
  plus vite. *Digression dispensable : suppression envisageable.*

> [!DANGER]
> « Nous n'avons rien d'intéressant à voler » n'est pas une défense. Les
> attaques automatisées ne choisissent pas leur cible en fonction de son
> intérêt : elles choisissent ce qui est joignable et non corrigé.

---

## IV. Aller plus loin

> ⏭️ **Facultatif — pas exigé pour finir la journée.**

- **MITRE ATT&CK** — la base de référence des tactiques et techniques adverses.
  Le sigle se décompose en ATT (Adversarial Tactics, Techniques) et CK (Common
  Knowledge) ; il est maintenu par MITRE (organisme de recherche américain à but
  non lucratif). On y décrit les attaques par **comportements observables**, ce
  qui permet de comparer un incident à des méthodes déjà répertoriées.
- **ANSSI (Agence nationale de la sécurité des systèmes d'information)** et
  **DBIR (Data Breach Investigations Report, Verizon)** — le « Panorama de la
  cybermenace » de la première décrit chaque année les acteurs actifs en France ;
  le second sert à vérifier si les motifs d'attaque que vous redoutez sont ceux
  qui dominent réellement. Ressources déjà citées au
  [chapitre 1](01-pourquoi-securiser.md).

---

## Points clés

- Les acteurs se distinguent par leur **motivation**, leurs **moyens** et leur
  **temps** — deux défenses très différentes pour deux menaces très différentes.
- La **kill chain** simplifiée enchaîne reconnaissance, intrusion, exploitation,
  persistance et exfiltration : couper une seule étape fait échouer l'attaque.
- La **course patch / exploit** se joue sur la vitesse : un correctif appliqué
  vite vaut mieux qu'une protection parfaite jamais déployée.
- L'attribution d'une attaque est difficile : on défend contre des **méthodes**,
  pas contre des noms.

---

[← Chapitre précédent](03-cid-et-vocabulaire.md) · [Sommaire](Readme.md) · [Chapitre suivant →](05-modeles-de-securite.md)
