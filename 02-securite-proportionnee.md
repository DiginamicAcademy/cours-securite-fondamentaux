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

[← Chapitre précédent](01-pourquoi-securiser.md) · [Sommaire](Readme.md) · [Chapitre suivant →](03-cid-et-vocabulaire.md)
