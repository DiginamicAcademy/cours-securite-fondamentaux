<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/Logo-diginamic-color-blk.png">
    <img src="assets/Logo-diginamic-color.svg" alt="Diginamic Formation" width="358">
  </picture>
</p>

# Les fondamentaux de la cybersécurité et de la sécurité informatique

> Cours d'**autoformation** · **RNCP40573** Expert en informatique et systèmes d'information · **brique transversale de sécurité**, adossée au bloc **BC03** (compétence C25)
> 1 journée · supports **rédigés par IA**, relus et validés.

---

## Pourquoi ce cours

On ne protège jamais tout : on protège **ce qui a de la valeur, à la mesure de
ce qui le menace**. Avant la boîte à outils, ce cours donne les réflexes de
départ — regarder ce qu'on protège, mesurer ce qu'un incident coûte réellement,
et arbitrer les mesures de sécurité au lieu de les accumuler.

Le fil rouge est **DIGICHEESE** (la fromagerie du fil rouge) : une fromagerie qui
vend du Comté en ligne, et dont les données clients ne valent pas les mêmes
mesures que les codes d'accès d'une banque. Chaque notion est appliquée à ce cas,
puis comparée à d'autres systèmes.

---

## À l'issue de ce cours

Vous serez capable de :

- **Décrire** les conséquences d'un incident de sécurité sur une organisation.
- **Distinguer** les postes de coût d'un incident, au-delà de la seule réparation technique.
- **Identifier** les victimes d'un incident, au-delà de l'entreprise elle-même.
- **Expliquer** pourquoi la sécurité est un arbitrage et non une accumulation de mesures.
- **Évaluer** la criticité d'un système à partir de trois critères : valeur des données, exposition, impact métier.
- **Confronter** le coût d'une mesure de sécurité au risque qu'elle réduit.
- **Arbitrer** entre plusieurs mesures possibles, et dire ce que vous acceptez de ne pas faire.
- **Rédiger** un avis d'arbitrage court et argumenté.

---

## Sommaire

| # | Chapitre | Durée de lecture |
| --- | --- | --- |
| 01 | [Pourquoi sécuriser ? — Enjeux business et humains](01-pourquoi-securiser.md) | 15 min |
| 02 | [Sécurité proportionnée — risque, coût et confort d'usage](02-securite-proportionnee.md) | 20 min |
| 03 | [CID et vocabulaire du risque — les mots pour parler du risque](03-cid-et-vocabulaire.md) | 20 min |
| 04 | [Le paysage de la cybersécurité — qui attaque, comment, et à quelle vitesse](04-paysage-cyber.md) | 20 min |
| 05 | [Modèles de défense — la sécurité en couches](05-modeles-de-securite.md) | 20 min |
| 06 | [Cadre juridique introductif — le RGPD comme contrainte technique](06-cadre-juridique-intro.md) | 25 min |
| A | [Glossaire et ressources](A-Glossaire-et-ressources.md) | annexe, à consulter |

Les six chapitres totalisent **≈ 120 min** de travail, ateliers compris.

**Travaux pratiques** — les cinq premiers se font dans le chapitre qui enseigne
la notion qu'ils appliquent, puis se corrigent en autonomie. L'exercice d'intégration
clôt la journée :

| | Sujet | Durée |
| --- | --- | --- |
| 🟢 | Analyser un incident — dans le chapitre 01 (corrigé dépliable) | 15 min |
| 🟡 | Arbitrer des mesures de sécurité — dans le chapitre 02 (corrigé dépliable) | 30 min |
| 🟡 | Construire une matrice menace → vulnérabilité → risque — dans le chapitre 03 (corrigé dépliable) | 25 min |
| 🔵 | Cartographier les zones de confiance d'une plateforme data — dans le chapitre 05 (corrigé dépliable) | 30 min |
| 🔴 | Identifier les obligations RGPD sur un cas type — dans le chapitre 06 (corrigé dépliable, facultatif) | 30 min · facultatif |
| 🔵 | [Exercice d'intégration — sécuriser le lancement d'une boutique en ligne](tp/INTEGRATION-J1.md) | 75 min |

---

## ✅ Checkpoints de fin de parcours

À cocher à la fin de la journée. Ce cours se suit en autoformation et il n'y a
pas de journée suivante : ces cases ne verrouillent rien, elles vous indiquent
où revenir. En cas de doute : ne pas avancer, revenir au concept concerné et
consolider en refaisant les TP.

### Chapitres 01 à 06

- [ ] J'ai lu les chapitres 01 à 06 et les points clés sont clairs.
- [ ] J'ai fait au moins les exercices 🟢 et 🟡 (partie principale), et déplié la correction « Voir la correction » de chaque exercice, à la fin du chapitre qui le porte. Les extensions « Pour aller plus loin » sont facultatives.
- [ ] Je sais expliquer, avec mes mots, les 2-3 idées principales de la journée.
- [ ] Je peux appliquer ces idées à un cas simple (un extrait de code, une config, un flux).

---

## Aller plus loin

*Ces approfondissements sont facultatifs : ils ne sont jamais exigés pour
terminer la journée.*

- **ANSSI (Agence nationale de la sécurité des systèmes d'information)** : l'autorité française en matière de cybersécurité. Ses rapports d'activité et son « [Panorama de la cybermenace](https://cyber.gouv.fr/nous-connaitre/publications/panoramas-de-la-cybermenace/) » détaillent les tendances observées en France.
- **DBIR ([Data Breach Investigations Report, Verizon](https://www.verizon.com/business/resources/reports/dbir/))** : une étude annuelle de milliers d'incidents réels, utile pour comprendre les motifs d'attaque dominants.
- **CNIL ([Commission nationale de l'informatique et des libertés](https://www.cnil.fr/))** : le cadre et les sanctions liés aux données personnelles en France.
- **EBIOS ([Expression des Besoins et Identification des Objectifs de sécurité](https://cyber.gouv.fr/securisation/analyse-des-risques/methode-ebios-rm/))**, dans sa version **RM (méthode de gestion des risques)** : la méthode française de l'ANSSI pour analyser les risques de bout en bout.
