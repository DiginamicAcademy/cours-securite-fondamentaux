[Sommaire](Readme.md) · [Chapitre suivant →](02-securite-proportionnee.md)

# Pourquoi sécuriser ? — Enjeux business et humains

> Une fromagerie vend du Comté en ligne. Ses données clients valent-elles les mêmes
> mesures que les codes d'accès d'une banque ? Avant d'ouvrir la boîte à outils,
> on apprend à **regarder ce qu'on protège**, et pourquoi.

**Durée :** ≈ 15 min (lecture ≈ 8 min + atelier 5 min + réflexion) · **Prérequis :** aucun

---

## Objectifs

À l'issue de ce chapitre, vous serez capable de :

- **Décrire** les conséquences d'un incident de sécurité sur une organisation.
- **Distinguer** les postes de coût d'un incident, au-delà de la seule réparation technique.
- **Identifier** les victimes d'un incident, au-delà de l'entreprise elle-même.
- **Expliquer** pourquoi la sécurité est un arbitrage et non une accumulation de mesures.

---

## I. Ce que coûte un incident

Début 2023, un hôpital des Yvelines est paralysé par un rançongiciel. Les systèmes
d'information sont hors service : les urgences sont détournées vers d'autres
établissements, des interventions sont reportées, les dossiers patients redeviennent
du papier pendant des semaines. Ce n'est pas une histoire de geeks — c'est une
histoire de lits, de personnes, de soins annulés.

L'année précédente, un autre établissement français subissait la même attaque :
mois de remise en état, rançon réclamée, milliers de patients redirigés. Et ça ne
concerne pas que les hôpitaux : une **TPE** (très petite entreprise) peut être
mise à genoux par une attaque partie d'un simple courriel piégé.

### Les postes de coût

Quand on parle du « coût » d'un incident, la réparation technique n'est qu'une
petite ligne. Les postes réels :

| Poste | Ce que ça recouvre |
| --- | --- |
| **Interruption d'activité** | production à l'arrêt, commandes perdues, clients qui partent ailleurs |
| **Réparation et remise en état** | investigation, nettoyage, reconstruction des systèmes, renforcement après coup |
| **Image et confiance** | réputation entamée, prospects qui hésitent, partenaires qui s'inquiètent |
| **Sanctions et amendes** | manquements aux obligations légales (voir le cadre juridique plus loin dans la journée) |
| **Contentieux** | plaintes de clients ou de partenaires, recours, expertises |

Un incident coûte rarement cher là où on l'attend. Le plus souvent, c'est
**l'activité arrêtée** qui plombe le bilan — pas la facture du prestataire
informatique.

> 🧪 **Atelier rapide (5 min)**
>
> La fromagerie perd la base de ses commandes clients (noms, adresses, historique
> d'achats). Sans chercher la solution technique, listez les conséquences dans
> trois catégories : **financier**, **légal**, **humain**. Trois lignes par
> catégorie suffisent.

---

## II. Qui sont les victimes ?

On résume souvent un incident à « l'entreprise s'est fait pirater ». C'est
incomplet. Derrière une fuite de données, il y a :

- **Les clients** — dont les données personnelles circulent désormais sans contrôle :
  adresses, habitudes d'achat, parfois des données de paiement.
- **Les employés** — dont les identifiants peuvent être utilisés pour frapper
  ailleurs, ou qui subissent le stress d'un système à l'arrêt, la charge de la
  remise en état, parfois le chantage.
- **Les patients, les usagers** — quand le service touché est vital, l'impact se
  mesure en soins non rendus, pas en euros.
- **Les partenaires et fournisseurs** — un maillon faible compromet la chaîne :
  l'attaque passe souvent par un sous-traitant.

C'est pour cela que la sécurité n'est pas qu'une affaire de service informatique :
elle engage la continuité du service et la responsabilité légale de l'organisation.

---

## III. Sécuriser, c'est arbitrer

Si chaque incident coûte cher, pourquoi ne pas tout sécuriser au maximum ?
Parce que **la sécurité a aussi un coût** : argent, temps, confort des utilisateurs,
vitesse de développement.

On ne sécurise pas « par principe ». On sécurise **ce qui a de la valeur, à la
mesure de ce qui le menace** — et on laisse le reste tranquille. Protéger la page
vitrine d'un artisan menuisier comme un système bancaire serait un gaspillage ;
l'inverse serait une négligence.

Cette idée — la **sécurité proportionnée** — est le sujet du chapitre suivant. Retenez
déjà le réflexe : avant de choisir un outil, demandez-vous **ce que vous protégez,
pour qui, contre quoi**.

---

### Exercice 1 — Analyser un incident (15 min)

**Contexte.**

**DIGICHEESE** (la fromagerie du fil rouge) vend ses fromages en ligne. Un lundi matin,
Sophie, responsable des commandes, ouvre un courriel qui semble venir de son
fournisseur de cartons. Elle clique sur le lien, saisit ses identifiants sur une
page qui ressemble à s'y méprendre à l'extranet de la fromagerie.

Dans la semaine qui suit :

- des commandes clients disparaissent du suivi de livraison ;
- plusieurs clients reçoivent un courriel de « remboursement » contenant un lien
  de paiement suspect ;
- la direction découvre la situation grâce à un client qui signale l'arnaque.

**Partie 1 — Décrire l'incident.**

En deux ou trois phrases, racontez ce qui s'est passé : **par quel point d'entrée**
l'attaque est arrivée, et **ce que l'attaquant a pu obtenir**.

**Partie 2 — Identifier les actifs touchés.**

Listez les actifs concernés (données, systèmes, personnes). Classez-les en deux
catégories : ce qui est **compromis** (l'attaquant y a accédé) et ce qui est
**menacé** (impacté sans être forcément compromis).

**Partie 3 — Classer selon les piliers CID (Confidentialité, Intégrité, Disponibilité).**

Pour chaque pilier, dites s'il est affecté ou non, et justifiez en une phrase.
Un pilier non affecté doit être justifié lui aussi.

**Partie 4 — Estimer l'impact.**

En vous appuyant sur les postes de coût du chapitre (interruption, réparation,
image, sanctions, contentieux), listez les conséquences probables pour la
fromagerie. Classez-les par gravité, de la plus grave à la moins grave, et
expliquez votre classement en deux lignes.

**Avant d'ouvrir la correction**, vérifiez que :

- [ ] Ma description nomme le **point d'entrée** de l'attaque (et pas seulement ses conséquences).
- [ ] J'ai distingué actifs **compromis** et actifs **menacés**.
- [ ] J'ai donné un avis **justifié** pour les trois piliers CID, y compris ceux que je considère non affectés.
- [ ] Ma liste d'impact cite au moins **trois postes de coût** parmi ceux du chapitre.
- [ ] Mon classement de gravité s'appuie sur un **critère explicite** (argent, personnes, durée…).

*Pour aller plus loin (facultatif).*

Refaites le même exercice en supposant que l'attaquant n'a pas
envoyé de faux courriels aux clients, mais s'est contenté de revendre la base de
commandes. Qu'est-ce qui change dans votre classification ?

<details>
<summary>Voir la correction</summary>

Comparez d'abord votre travail aux **étapes** ci-dessous : la méthode compte autant que le résultat.

**Partie 1 — Décrire l'incident.**

**Éléments attendus :**

L'attaque est arrivée par un **courriel piégé** (hameçonnage) imitant un fournisseur.
Sophie a cliqué sur un lien et saisi ses identifiants sur un faux site : l'attaquant
a récupéré son compte d'accès à l'extranet. Avec cet accès, il a pu consulter les
commandes clients, puis s'en servir pour envoyer de faux courriels de
« remboursement » aux clients de la fromagerie.

**Ce qu'il faut retenir :** le point d'entrée est **humain et organisationnel**
(un courriel, un clic), pas une faille technique spectaculaire. La plupart des
incidents commencent ainsi.

**Partie 2 — Identifier les actifs touchés.**

**Compromis** (l'attaquant y a accédé) :

- le compte d'accès de Sophie à l'extranet ;
- la base des commandes clients (noms, adresses, historique d'achats) ;
- les coordonnées de contact des clients (utilisées pour les faux courriels).

**Menacés** (impactés sans accès direct avéré) :

- la confiance des clients envers la fromagerie ;
- le système de suivi de livraison (données devenues peu fiables) ;
- les comptes des autres employés (le même stratagème peut être rejoué).

**Partie 3 — Classer selon les piliers CID (Confidentialité, Intégrité, Disponibilité).**

| Pilier | Affecté ? | Justification |
| --- | --- | --- |
| **Confidentialité** | ✅ Oui | Les commandes clients ont été lues par un tiers non autorisé. |
| **Intégrité** | ✅ Oui | Des commandes ont disparu du suivi : les données ont été modifiées ou supprimées. |
| **Disponibilité** | ✅ Oui, partiellement | Le suivi de livraison est dégradé : les informations ne sont plus fiables ni accessibles normalement. |

**Erreurs fréquentes :** considérer que la disponibilité n'est touchée que si le
site tombe complètement. Une donnée devenue **inutilisable** parce qu'on ne lui
fait plus confiance est aussi un problème de disponibilité. Inversement, ne pas
justifier un pilier « non affecté » est une erreur : l'absence d'impact est un
diagnostic, pas un oubli.

**Partie 4 — Estimer l'impact.**

**Éléments attendus** (classement indicatif — l'important est le critère explicite) :

1. **Sanctions et contentieux** — des données personnelles ont fui : obligations
   légales en jeu, plaintes possibles des clients.
2. **Image et confiance** — les clients ont été directement contactés par
   l'attaquant : la confiance est atteinte là où elle est la plus fragile.
3. **Interruption d'activité** — le suivi de livraison est perturbé, le traitement
   des commandes ralenti.
4. **Réparation et remise en état** — investigation, réinitialisation des accès,
   sécurisation du compte compromis.

**Sur le classement :** deux critères se défendent — la **gravité pour les
personnes** (ici les clients, d'où les sanctions et l'image en tête) ou le
**coût financier direct** (où l'interruption d'activité peut passer devant). Ce
qui est attendu, c'est que le critère soit **dit** : un classement sans critère
affiché ne se discute pas.

**Points à retenir.**

- Le point d'entrée est souvent **humain** : un courriel, un clic, un identifiant.
- Un même incident touche **plusieurs piliers CID** à la fois — rarement un seul.
- L'impact se juge d'abord sur **les personnes et l'activité**, ensuite sur la technique.
- Un classement d'impact n'a de valeur que si son **critère est explicite**.

</details>

---

## IV. Aller plus loin

> ⏭️ **Facultatif — pas exigé pour finir la journée.**

- **ANSSI** (Agence nationale de la sécurité des systèmes d'information) : l'autorité
  française en matière de cybersécurité. Ses rapports d'activité et son « Panorama
  de la cybermenace » détaillent les tendances observées en France.
- **DBIR** (Data Breach Investigations Report, Verizon) : une étude annuelle de
  milliers d'incidents réels, utile pour comprendre les motifs d'attaque dominants.
- **CNIL** (Commission nationale de l'informatique et des libertés) : le cadre et
  les sanctions liés aux données personnelles en France.

---

## Points clés

- Un incident coûte d'abord par l'**interruption d'activité**, ensuite par la
  réparation technique.
- Les victimes dépassent l'entreprise : clients, employés, usagers, partenaires.
- La sécurité est un **arbitrage** : on protège proportionnellement à la valeur
  des actifs et à la menace.
- Avant tout outil : savoir **ce qu'on protège, pour qui, contre quoi**.

---

## 🧠 Vérifiez vos acquis

*Formatif, jamais noté. Répondez sans relire le chapitre. Les réponses se déplient juste après le séparateur : ce qui compte est de repérer où vous vacillez, pas de faire 5 sur 5.*

**1.** Un rançongiciel paralyse un hôpital : les systèmes sont hors service pendant des semaines, les urgences sont détournées. Quel poste de coût pèse le plus lourd, d'après le chapitre ?

- A. Le montant de la rançon versée à l'attaquant, seul poste de coût qui se chiffre précisément au moment de l'incident
- B. L'activité arrêtée : urgences détournées, interventions reportées, dossiers patients remis sur papier
- C. Le prix des outils de sécurité achetés pour l'année, et le nombre d'alertes qu'ils produisent par jour
- D. Le temps passé par l'équipe technique à corriger la faille qui a permis l'intrusion, une fois l'incident clos

**2.** L'attaque d'une entreprise est partie d'un sous-traitant. Pourquoi le chapitre place-t-il les partenaires et fournisseurs parmi les victimes ?

- A. L'authentification multi-facteurs (MFA) à chaque connexion, avec un code à saisir sur tous les postes
- B. Parce qu'un maillon faible compromet la chaîne : l'attaque passe souvent par un sous-traitant
- C. L'expiration des sessions au bout de quelques minutes d'inactivité, donc une reconnexion en plein travail
- D. Des mots de passe longs et uniques pour chaque service, avec un gestionnaire à apprivoiser

**3.** Si chaque incident coûte cher, pourquoi ne pas empiler toutes les mesures de sécurité disponibles ?

- A. Qu'il faut ajouter la MFA sur tous les comptes pour compenser la faiblesse révélée par le post-it
- B. Parce que la sécurité a elle aussi un coût : argent, temps, confort des utilisateurs, vitesse de développement
- C. Qu'il faut allonger encore la longueur minimale demandée, pour rendre plus résistants les mots de passe restants
- D. Qu'il faut une consigne de service pour retirer les notes et contrôler les postes de travail chaque mois

**4.** Avant de choisir un outil de sécurité, que faut-il se demander ?

- A. Pour que l'auditeur puisse retrouver la trace du choix et le reprocher plus tard à l'équipe qui l'a fait
- B. Ce qu'on protège, pour qui, contre quoi
- C. Parce que chaque ligne du budget doit être justifiée, y compris les mesures qui n'ont pas été achetées
- D. Pour pouvoir rouvrir le dossier au prochain projet, quand les outils et les contraintes auront changé

**5.** *Question ouverte (2-3 lignes).* La fromagerie perd la base de ses commandes clients (noms, adresses, historique d'achats), qui devient en plus inaccessible. Dites qui sont les victimes et quels postes de coût l'entreprise va payer.

---

<details>
<summary>Vérifier ses réponses</summary>

### Réponses

**1. B.** La réparation technique n'est qu'une petite ligne du bilan : c'est l'interruption d'activité qui plombe le résultat.
**Pourquoi :** le chapitre oppose explicitement la facture du prestataire informatique au coût de l'activité arrêtée, et l'exemple de l'hôpital se mesure en lits, en soins et en interventions reportées.

**2. B.** Les partenaires et les fournisseurs sont victimes parce que la chaîne est aussi solide que son maillon le plus faible.
**Pourquoi :** c'est pour cela que la sécurité n'est pas l'affaire du seul service informatique : elle engage la continuité du service et la responsabilité légale de l'organisation.

**3. B.** Sécuriser a un prix, en argent, en temps, en confort d'usage et en vitesse de développement : la sécurité est un arbitrage, pas une accumulation.
**Pourquoi :** on protège ce qui a de la valeur, à la mesure de ce qui le menace — protéger la page vitrine d'un artisan comme un système bancaire est un gaspillage, et l'inverse une négligence.

**4. B.** Le réflexe du chapitre passe avant toute question d'outil : ce qu'on protège, pour qui, contre quoi.
**Pourquoi :** la valeur des actifs et la menace déterminent le niveau de protection, et non l'inverse.

**5.** Attendu : les victimes sont les clients (données personnelles qui circulent sans contrôle) et les employés (identifiants réutilisables ailleurs, charge de la remise en état), et l'entreprise paie l'interruption d'activité, la réparation et remise en état, l'image et la confiance abîmées, éventuellement des sanctions et des contentieux.
**Pourquoi :** un incident dépasse presque toujours l'entreprise elle-même, et son coût se répartit sur plusieurs postes dont la réparation technique n'est pas le plus lourd.

</details>

---

[Sommaire](Readme.md) · [Chapitre suivant →](02-securite-proportionnee.md)
