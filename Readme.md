<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/Logo-diginamic-color-blk.png">
    <img src="assets/Logo-diginamic-color.svg" alt="Diginamic Formation" width="358">
  </picture>
</p>

# Les fondamentaux de la cybersécurité et de la sécurité informatique

> Cours d'**autoformation** · **RNCP40573** Expert en informatique et systèmes d'information · **brique transversale de sécurité**, adossée au bloc **BC03** (compétence C25)
> 1 journée(s) · supports **rédigés par IA**, relus et validés.

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
| 01 | [Pourquoi sécuriser ? — Enjeux business et humains](01-pourquoi-securiser.md) | 45 min |
| 02 | [Sécurité proportionnée — risque, coût et confort d'usage](02-securite-proportionnee.md) | 55 min |
| 03 | [CID et vocabulaire du risque — les mots pour parler du risque](03-cid-et-vocabulaire.md) | 60 min |
| 04 | [Le paysage de la cybersécurité — qui attaque, comment, et à quelle vitesse](04-paysage-cyber.md) | 60 min |
| 05 | [Modèles de défense — la sécurité en couches](05-modeles-de-securite.md) | 50 min |
| 06 | [Cadre juridique introductif — le RGPD comme contrainte technique](06-cadre-juridique-intro.md) | 55 min |

**Travaux pratiques** — chaque énoncé se fait juste après le chapitre
correspondant, puis se corrige soi-même :

| | Sujet | Durée |
| --- | --- | --- |
| 🟢 | [Analyser un incident](tp/01-analyser-incident.md) · [corrigé](tp/corrige/01-analyser-incident.md) | 20 min |
| 🟡 | [Arbitrer des mesures de sécurité](tp/02-arbitrer-mesures.md) · [corrigé](tp/corrige/02-arbitrer-mesures.md) | 35 min |
| 🟡 | [Construire une matrice menace → vulnérabilité → risque](tp/03-vocabulaire-risque.md) · [corrigé](tp/corrige/03-vocabulaire-risque.md) | 35 min |
| 🔵 | [Cartographier les zones de confiance d'une plateforme data](tp/04-cartographier-si.md) · [corrigé](tp/corrige/04-cartographier-si.md) | 45 min |
| 🔴 | [Identifier les obligations RGPD sur un cas type](tp/05-defi-rgpd.md) · [corrigé](tp/corrige/05-defi-rgpd.md) | libre |

---

## ✅ Checkpoints de fin de journée

À cocher avant de passer à la journée suivante. En cas de doute : ne pas
avancer, revenir au concept concerné, refaire l'exercice.

### Jour 1 — chapitres 01 à 06

- [ ] J'ai lu les chapitres 01 à 06 et les points clés sont clairs.
- [ ] J'ai fait au moins les exercices 🟢 et 🟡 (partie principale), et vérifié mes réponses dans `tp/corrige/`. Les extensions « Pour aller plus loin » sont facultatives.
- [ ] J'ai répondu au QCM formatif, lorsqu'il est disponible, et identifié mes notions à revoir.
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
