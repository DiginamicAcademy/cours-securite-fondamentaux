[← Chapitre précédent](01-pourquoi-securiser.md) · [Sommaire](Readme.md) · [Chapitre suivant →](03-cid-et-vocabulaire.md)

# Sécurité proportionnée — risque, coût et confort d'usage

> On ne met pas le même verrou sur une cabane de jardin que sur un coffre-fort.
> Une page vitrine d'artisan et le système d'une banque n'appellent pas les mêmes
> mesures. Avant d'ouvrir la boîte à outils, apprenez à **mesurer ce que vous
> protégez** — et le prix de chaque verrou.

**Durée :** ≈ 20 min (lecture ≈ 10 min + atelier 8 min + réflexion) · **Prérequis :** [Pourquoi sécuriser ?](01-pourquoi-securiser.md)

---

## Objectifs

À l'issue de ce chapitre, vous serez capable de :

- **Évaluer** la criticité d'un système à partir de trois critères : valeur des données, exposition, impact métier.
- **Confronter** le coût d'une mesure de sécurité au risque qu'elle réduit.
- **Arbitrer** entre plusieurs mesures possibles, et dire ce que vous acceptez de ne pas faire.
- **Rédiger** un avis d'arbitrage court et argumenté.

---

## I. Tous les systèmes ne se valent pas

Quatre systèmes, quatre mondes :

| Système | Ce qu'il contient | Qui y accède | Si ça tombe |
| --- | --- | --- | --- |
| **Le système d'une banque** | comptes, opérations, identités | des millions de clients, en ligne à toute heure | l'épargne est bloquée, la confiance casse, le régulateur s'en mêle |
| **L'extranet de la fromagerie** | commandes, adresses, historique d'achats | les clients et l'équipe des commandes | les commandes s'arrêtent, les clients partent (voir le chapitre précédent) |
| **Le site vitrine d'un artisan menuisier** | quelques pages, des photos, des coordonnées | tout le monde, en lecture seule | un site à remettre en ligne |
| **L'outil interne de gestion des congés** | noms et dates d'absence | les salariés, depuis le réseau interne | quelques jours de saisie sur papier |

Trois questions suffisent à situer un système :

1. **Valeur des données** — que vaut ce qu'on y trouve, et pour qui ? Une adresse
   de livraison ne vaut pas un numéro de carte bancaire.
2. **Exposition** — qui peut y accéder ? Tout Internet, le réseau interne, une
   seule équipe ?
3. **Impact métier** — si le système est compromis ou indisponible, l'activité
   continue-t-elle ?

La **criticité** naît de la combinaison des trois. Une donnée très sensible
enfermée dans un réseau fermé n'appelle pas les mêmes mesures qu'une donnée
moyenne ouverte à tout Internet — et un site consulté par le monde entier peut
rester sans enjeu s'il ne contient rien de sensible.

> 🧪 **Atelier rapide (8 min)**
>
> Classez les quatre systèmes du tableau sur une échelle de 1 (faible) à 5
> (critique) pour chacun des trois critères : valeur des données, exposition,
> impact si compromis. Pas de bonne réponse à deviner : l'essentiel est de
> **dire votre raisonnement** pour chaque note.

---

## II. Le coût des mesures et l'impact sur l'usage

Aucune mesure n'est gratuite. Chacune se paie en argent, en temps
d'administration — et surtout en **confort d'usage** (UX, expérience utilisateur)
pour ceux qui l'utilisent au quotidien.

| Mesure | Ce qu'elle apporte | Ce qu'elle coûte à l'utilisateur |
| --- | --- | --- |
| **MFA (authentification multi-facteurs)** | un mot de passe volé ne suffit plus | une étape de plus à chaque connexion |
| **Expiration de session** | une session oubliée ne reste pas ouverte | une reconnexion en plein travail |
| **Mots de passe longs et uniques** | pas de réutilisation entre les sites | un gestionnaire à apprivoiser, des mots de passe qu'on ne retient pas |
| **Chiffrement des sauvegardes** | une sauvegarde volée reste illisible | aucun |
| **Journalisation des accès** | on sait qui a consulté quoi | aucun |

Le prix se paie aussi **en sécurité**, quand la mesure est mal calibrée : des mots
de passe trop complexes finissent sur un post-it collé à l'écran, des sessions
qui expirent trop vite multiplient les mots de passe réutilisés, une
authentification multi-facteurs imposée partout finit par être contournée par
habitude. Une mesure que les utilisateurs contournent ne protège plus rien : elle
donne seulement l'impression de protéger.

C'est pour cela que **sécurité, disponibilité et confort d'usage se négocient**.
Le bon niveau n'est pas le maximum : c'est celui que les gens acceptent
d'appliquer, là où le risque le justifie.

---

## III. L'avis d'arbitrage

Pour trancher, on croise deux questions : **quel risque la mesure réduit-elle ?**
et **combien coûte-t-elle à mettre en œuvre ?**

| | Effort faible | Effort élevé |
| --- | --- | --- |
| **Risque élevé** | à faire tout de suite | à planifier et à budgéter |
| **Risque faible** | à faire quand l'occasion se présente | à écarter, en le motivant |

Le résultat s'écrit dans un **avis d'arbitrage** court, que quiconque peut
relire plus tard :

1. **Contexte** — quel système, quelle préoccupation.
2. **Mesures envisagées** — et ce qu'elles coûtent.
3. **Recommandation** — ce qu'on met en place, et pourquoi.
4. **Ce qu'on écarte** — et le risque résiduel qu'on accepte.

Ce dernier point est le plus important. **Ce qu'on accepte de ne pas faire est un
choix** : il se motive, il se date, il se relit. Une mesure écartée sans raison
est un oubli ; une mesure écartée avec raison est une décision. Entre « on n'y a
pas pensé » et « on a choisi de ne pas le faire, voilà pourquoi », il y a toute la
différence entre subir un incident et l'avoir anticipé.

---

### Exercice 1 — Arbitrer des mesures de sécurité (30 min)

**Contexte.**

Après l'incident raconté dans le chapitre précédent, la direction de la fromagerie
**DIGICHEESE** (la fromagerie du fil rouge) décide de revoir sa sécurité. Le cabinet qui l'accompagne
refuse de vendre « tout le catalogue » : il pose d'abord une question — qu'est-ce
qui mérite quoi ?

Quatre systèmes sont sur la table :

1. **Le système d'information d'une banque** — comptes et opérations de nombreux
   clients, accessible en ligne à toute heure.
2. **L'extranet de la fromagerie** — commandes, adresses, historique d'achats ;
   accessible en ligne aux clients et à l'équipe.
3. **Le site vitrine d'un artisan menuisier** — quelques pages statiques, des
   photos, des coordonnées ; en lecture seule pour tout le monde.
4. **L'outil interne de gestion des congés de la fromagerie** — noms et dates
   d'absence ; accessible uniquement depuis le réseau interne.

Le cabinet vous demande un avis d'arbitrage.

**Partie 1 — Évaluer la criticité.**

Pour chaque système, notez de 1 (faible) à 5 (critique) les trois critères du
chapitre : **valeur des données**, **exposition**, **impact si compromis**.
Justifiez chaque note en une ligne. Classez ensuite les quatre systèmes du plus
critique au moins critique.

**Partie 2 — Choisir les mesures.**

Le cabinet propose le menu de mesures suivant, avec son coût pour l'utilisateur :

| Mesure | Coût pour l'utilisateur |
| --- | --- |
| **MFA (authentification multi-facteurs)** à chaque connexion | une étape de plus, un code à saisir |
| **Expiration de session** courte | une reconnexion en plein travail |
| **Mots de passe longs et uniques**, gestionnaire fourni | un outil à apprivoiser |
| **Chiffrement des sauvegardes** | aucun |
| **Journalisation des accès** (qui a consulté quoi) | aucun |
| **Sensibilisation de l'équipe** (hameçonnage, bons réflexes) | du temps de formation |

Pour chaque système, retenez **au moins deux mesures** du menu et justifiez votre
choix en rapprochant la mesure de la criticité établie en partie 1.

**Partie 3 — Ce qu'on accepte de ne pas faire.**

Pour chaque système, nommez **au moins une mesure du menu que vous écartez**, et
motivez : quel risque reste-t-il, et pourquoi est-il acceptable ici ? Si vous
estimez qu'aucune mesure n'est écartable pour un système, dites-le et expliquez
pourquoi : c'est un arbitrage comme les autres.

**Partie 4 — Rédiger l'avis d'arbitrage.**

En une dizaine de lignes maximum, rédigez l'avis pour **l'extranet de la
fromagerie**, en suivant la trame du chapitre : contexte, mesures retenues,
mesures écartées, recommandation.

**Avant d'ouvrir la correction**, vérifiez que :

- [ ] J'ai noté les trois critères pour les **quatre** systèmes, et justifié chaque note.
- [ ] Mon classement de criticité est **explicite** : je peux le défendre à l'oral.
- [ ] Chaque système a **au moins deux mesures** retenues, reliées à sa criticité.
- [ ] J'ai nommé **au moins une mesure écartée** par système, avec le risque résiduel accepté.
- [ ] Mon avis d'arbitrage dit ce qu'on fait **et** ce qu'on ne fait pas, avec une raison.

*Pour aller plus loin (facultatif).*

Le cabinet suggère d'ajouter la MFA partout, « ça ne coûte rien ».
Reprenez votre avis : qu'auriez-vous répondu, et sur quels systèmes cette mesure
vous semble-t-elle justifiée ou excessive ?

<details>
<summary>Voir la correction</summary>

Comparez d'abord votre travail aux **étapes** ci-dessous : la méthode compte autant que le résultat.

**Partie 1 — Évaluer la criticité.**

**Éléments attendus** (notes indicatives sur l'échelle de 1 à 5 donnée dans
l'énoncé — l'important est la justification de chaque note) :

| Système | Valeur des données | Exposition | Impact si compromis | Rang |
| --- | --- | --- | --- | --- |
| **Banque** | 5 | 5 | 5 | le plus critique |
| **Extranet de la fromagerie** | 4 | 4 | 4 | élevé |
| **Outil interne de congés** | 2 | 1 | 2 | faible à moyen |
| **Site vitrine** | 1 | 5 | 1 | le moins critique |

**Justifications types :**

- **Banque** — des identités et de l'argent, accessibles du monde entier, et une
  activité qui ne peut pas s'arrêter.
- **Extranet de la fromagerie** — des données personnelles réelles (adresses,
  habitudes d'achats), exposées en ligne, et une activité de vente qui s'arrête si
  le système tombe : l'incident du chapitre précédent l'a montré.
- **Outil interne de congés** — des données peu sensibles (noms, dates d'absence),
  fermées au réseau interne, impact limité à quelques jours de saisie sur papier.
- **Site vitrine** — aucune donnée saisie par l'utilisateur, exposition maximale
  mais rien à voler, impact = remettre le site en ligne.

**Erreurs fréquentes :** noter l'exposition du site vitrine au maximum et en
conclure qu'il est critique. L'exposition n'est qu'un des trois critères : sans
donnée sensible et sans impact métier, un site très exposé reste peu critique.
L'inverse existe aussi : sous-estimer l'outil interne parce qu'il est « juste »
interne — une fuite de données de salariés est une fuite de données.

**Partie 2 — Choisir les mesures.**

**Éléments attendus :**

| Système | Mesures retenues | Pourquoi |
| --- | --- | --- |
| **Banque** | tout le menu | criticité maximale : chaque coût d'usage se justifie |
| **Extranet de la fromagerie** | MFA (authentification multi-facteurs) pour l'équipe, journalisation des accès, chiffrement des sauvegardes, sensibilisation | données personnelles et activité de vente ; la sensibilisation répond au point d'entrée de l'incident — un courriel |
| **Outil interne de congés** | journalisation des accès, sensibilisation | les mesures sans coût d'usage d'abord ; la MFA serait disproportionnée |
| **Site vitrine** | chiffrement des sauvegardes, journalisation des accès | ce qui ne coûte rien à l'utilisateur se généralise ; le reste serait du gaspillage |

**Le principe à retenir :** les mesures **sans coût d'usage** (chiffrement des
sauvegardes, journalisation) se déploient partout sans discussion. Les mesures
**qui coûtent du confort** (MFA, expiration de session, mots de passe exigeants)
se réservent aux systèmes dont la criticité les justifie.

**Partie 3 — Ce qu'on accepte de ne pas faire.**

**Éléments attendus** (d'autres arbitrages se défendent s'ils sont motivés) :

- **Site vitrine** — on écarte la MFA et l'expiration de session. Risque résiduel
 : une prise de contrôle de l'hébergement. Acceptable : rien de sensible à
  voler, et le site se remet en ligne.
- **Outil interne de congés** — on écarte la MFA et les mots de passe longs et
  uniques. Risque résiduel : un compte interne détourné. Acceptable : le réseau
  est fermé et l'impact se limite à des dates d'absence.
- **Extranet de la fromagerie** — on peut écarter l'expiration de session courte
  côté client. Risque résiduel : une session client restée ouverte. Acceptable si
  l'équipe est protégée par la MFA et que les commandes se relisent avant
  traitement.
- **Banque** — si vous estimez que rien n'est écartable, dire et motiver ce choix
  est une réponse valable : « tout garder » est un arbitrage quand il est expliqué.

**Erreurs fréquentes :** écarter une mesure sans nommer le risque qui reste (un
« non » sans conséquence n'est pas un arbitrage), ou tout déployer partout par
principe — ce qui ramène au « tout le catalogue » que le cabinet refusait.

**Partie 4 — Rédiger l'avis d'arbitrage.**

**Éléments attendus :** les quatre temps de la trame sont présents (contexte,
mesures retenues, mesures écartées, recommandation), et les mesures écartées
portent un risque résiduel assumé. Exemple :

> **Contexte** — l'extranet de la fromagerie porte les commandes clients ;
> l'incident précédent est parti d'un courriel piégé.
>
> **Mesures retenues** — MFA pour l'équipe, journalisation des accès, chiffrement
> des sauvegardes, sensibilisation au hameçonnage.
>
> **Mesures écartées** — expiration de session courte côté client : elle nuit à
> l'achat en ligne sans réduire le risque réel.
>
> **Recommandation** — déployer les mesures retenues, et réexaminer l'arbitrage si
> des données de paiement venaient à être stockées.

**Points à retenir.**

- La criticité se juge sur **trois critères** : valeur des données, exposition,
  impact métier.
- Les mesures sans coût d'usage se généralisent ; celles qui coûtent du confort se
  méritent.
- Écarter une mesure est un choix : il se motive, il se date, il se documente.
- Un bon avis d'arbitrage dit aussi **ce qu'on ne fait pas**.

</details>

---

## IV. Aller plus loin

> ⏭️ **Facultatif — pas exigé pour finir la journée.**

- **EBIOS** (Expression des Besoins et Identification des Objectifs de
  sécurité), dans sa version **RM** (méthode de gestion des risques) : la méthode française de l'**ANSSI**
  (Agence nationale de la sécurité des systèmes d'information) pour analyser les
  risques de bout en bout. Ce chapitre en emprunte l'esprit : partir des actifs et
  des scénarios, pas de la liste d'outils.
- **Les matrices de risque** des grands cadres internationaux :
  même logique que l'item EBIOS, vocabulaires différents.

---

## Points clés

- La criticité se juge sur trois critères : **valeur des données**, **exposition**,
  **impact métier**.
- Toute mesure a un coût — argent, temps, confort d'usage — et parfois un coût en
  sécurité quand elle est contournée.
- Les mesures sans coût d'usage (journalisation, chiffrement des sauvegardes) se
  généralisent ; celles qui coûtent du confort se réservent aux systèmes qui le
  méritent.
- Arbitrer, c'est choisir quoi faire **et** quoi ne pas faire — et l'écrire.

---

## 🧠 Vérifiez vos acquis

*Formatif, jamais noté. Répondez sans relire le chapitre. Les réponses se déplient juste après le séparateur : ce qui compte est de repérer où vous vacillez, pas de faire 5 sur 5.*

**1.** Quelles sont les trois questions qui suffisent à situer la criticité d'un système ?

- A. Valeur des données, exposition, impact métier
- B. Coût de la mesure, nombre d'utilisateurs, ancienneté du système
- C. Confidentialité, intégrité, disponibilité
- D. Menace, vulnérabilité, impact

**2.** Parmi ces mesures, laquelle ne coûte rien à l'utilisateur au quotidien ?

- A. L'authentification multi-facteurs (MFA)
- B. L'expiration des sessions
- C. Le chiffrement des sauvegardes
- D. Des mots de passe longs et uniques

**3.** Des mots de passe trop complexes exigés finissent notés sur des post-it collés aux écrans. Qu'est-ce que le chapitre en conclut ?

- A. Qu'il faut ajouter la MFA pour compenser la faiblesse que révèle le post-it collé à l'écran
- B. Qu'une mesure que les utilisateurs contournent ne protège plus rien : elle donne seulement l'impression de protéger
- C. Qu'il faut allonger encore la longueur minimale demandée, pour durcir les mots de passe qui restent
- D. Qu'il faut passer une consigne pour retirer les notes et contrôler les postes de travail chaque mois

**4.** Dans un avis d'arbitrage, pourquoi écrire ce que l'on écarte ?

- A. Pour que l'auditeur puisse retrouver le choix et le reprocher plus tard à qui l'a fait
- B. Parce qu'une mesure écartée avec une raison est une décision, alors qu'une mesure écartée sans raison est un oubli
- C. Parce que chaque ligne du budget doit être justifiée, même celles des mesures non achetées
- D. Pour pouvoir rouvrir le dossier au prochain projet, quand les contraintes auront changé

**5.** *Question ouverte (2-3 lignes).* On vous demande d'imposer la MFA partout dans la fromagerie. Rédigez les deux dernières rubriques de l'avis d'arbitrage : la recommandation, puis ce que vous écartez avec le risque résiduel accepté.

---

<details>
<summary>Vérifier ses réponses</summary>

### Réponses

**1. A.** Valeur des données, exposition, impact métier : la criticité naît de la combinaison des trois.
**Pourquoi :** une donnée très sensible enfermée dans un réseau fermé et une donnée moyenne ouverte à tout Internet ne demandent pas les mêmes mesures — un site consulté par le monde entier peut rester sans enjeu s'il ne contient rien de sensible.

**2. C.** Le chiffrement des sauvegardes n'a aucun coût d'usage, comme la journalisation des accès.
**Pourquoi :** ce sont les mesures sans coût d'usage qui se généralisent ; celles qui coûtent du confort se réservent aux systèmes qui le méritent.

**3. B.** Le prix d'une mesure se paie aussi en sécurité quand elle est mal calibrée : post-it, mots de passe réutilisés, MFA contournée par habitude.
**Pourquoi :** le bon niveau n'est pas le maximum, c'est celui que les gens acceptent d'appliquer, là où le risque le justifie.

**4. B.** Ce qu'on accepte de ne pas faire est un choix : il se motive, il se date, il se relit.
**Pourquoi :** entre « on n'y a pas pensé » et « on a choisi de ne pas le faire, voilà pourquoi », il y a toute la différence entre subir un incident et l'avoir anticipé.

**5.** Attendu : une recommandation bornée et motivée (par exemple la MFA sur les comptes qui touchent aux données clients et à l'administration, pas sur tous les postes) ; puis ce qui est écarté et pourquoi, avec le risque résiduel que l'on accepte d'assumer.
**Pourquoi :** arbitrer, c'est choisir quoi faire **et** quoi ne pas faire — et l'écrire, pour que la décision soit relisible plus tard.

</details>

---

[← Chapitre précédent](01-pourquoi-securiser.md) · [Sommaire](Readme.md) · [Chapitre suivant →](03-cid-et-vocabulaire.md)
