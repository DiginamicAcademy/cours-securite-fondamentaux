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

*Formatif, jamais noté. Répondez sans relire le chapitre, puis cochez. Les réponses sont juste après le séparateur : ce qui compte est de repérer où vous vacillez, pas de faire 5 sur 5.*

**1.** Un rançongiciel paralyse un hôpital : les systèmes sont hors service pendant des semaines, les urgences sont détournées. Quel poste de coût pèse le plus lourd, d'après le chapitre ?

- A. La facture du prestataire qui reconstruit les systèmes
- B. L'activité arrêtée : urgences détournées, interventions reportées, dossiers patients remis sur papier
- C. L'amende prononcée pour les manquements légaux
- D. Le rachat du matériel remplacé pendant l'incident

- [ ] ✓ je savais

**2.** L'attaque d'une entreprise est partie d'un sous-traitant. Pourquoi le chapitre place-t-il les partenaires et fournisseurs parmi les victimes ?

- A. Parce qu'ils paient la rançon à la place de l'entreprise attaquée
- B. Parce qu'un maillon faible compromet la chaîne : l'attaque passe souvent par un sous-traitant
- C. Parce qu'ils portent légalement la sécurité de leur client
- D. Parce qu'ils subissent la même panne de matériel

- [ ] ✓ je savais

**3.** Si chaque incident coûte cher, pourquoi ne pas empiler toutes les mesures de sécurité disponibles ?

- A. Parce que les outils du marché ne savent pas protéger une TPE
- B. Parce que la sécurité a elle aussi un coût : argent, temps, confort des utilisateurs, vitesse de développement
- C. Parce qu'accumuler les mesures est interdit par le cadre juridique
- D. Parce qu'une seule mesure bien choisie suffit toujours

- [ ] ✓ je savais

**4.** Avant de choisir un outil de sécurité, que faut-il se demander ?

- A. Combien d'alertes l'outil est capable de produire par jour
- B. Ce qu'on protège, pour qui, contre quoi
- C. Quels concurrents l'utilisent déjà
- D. Si l'outil est référencé par un cadre international

- [ ] ✓ je savais

**5.** *Question ouverte (2-3 lignes).* La fromagerie perd la base de ses commandes clients (noms, adresses, historique d'achats), qui devient en plus inaccessible. Dites qui sont les victimes et quels postes de coût l'entreprise va payer.

- [ ] ✓ je savais

---

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

---

[Sommaire](Readme.md) · [Chapitre suivant →](02-securite-proportionnee.md)
