---
marp: true
theme: default
style: |
  section {background-color: #121114}
  h1,h2,h3 {color: #8393f0}
  p,ul,li,td,th {color: #ccc}
  section table {font-size: 0.85em}
  section table td {background-color: #121114}
  section table th {background-color: #272133; font-weight: bolder}
  pre {background-color: #17151a; color: #ccc}
  blockquote {border: 2px green solid; border-left-width: 15px; padding: 0.5em 15px;font-style: italic }
paginate: true
header: "Les fondamentaux de la cybersécurité et de la sécurité informatique"
footer: "![height:20px](https://raw.githubusercontent.com/DiginamicInternal/PublicAssets/refs/heads/main/Logo-diginamic-color-blk.png)"
RNCPBloc: [RNCP40573BC03]
---

# Les fondamentaux de la cybersécurité et de la sécurité informatique

## Journée 1 — programme Sécurité EISI (Expert en informatique et systèmes d'information)

**RNCP40573** · **brique transversale de sécurité**, adossée au bloc **BC03** (compétence C25)

<!-- Diapositive d'ouverture. Cette journée pose le socle : vocabulaire, enjeux et
     réflexes communs à tout le reste du parcours. -->

---

## Le fil rouge — DIGICHEESE

**DIGICHEESE** (la fromagerie du fil rouge) vend du Comté en ligne.

> Ses données clients valent-elles les mêmes mesures que les codes d'accès
> d'une banque ?

- Avant d'ouvrir la boîte à outils : **regarder ce qu'on protège**, et pourquoi.
- Toute la journée suit ce cas — et le compare à d'autres systèmes.

---

## 🎯 Objectifs — comprendre les enjeux

À l'issue de cette journée, vous saurez :

1. **Décrire** les conséquences d'un incident de sécurité sur une organisation
2. **Distinguer** les postes de coût d'un incident, au-delà de la seule réparation technique
3. **Identifier** les victimes d'un incident, au-delà de l'entreprise elle-même
4. **Expliquer** pourquoi la sécurité est un arbitrage et non une accumulation de mesures

---

## 🎯 Objectifs — arbitrer les mesures

5. **Évaluer** la criticité d'un système : valeur des données, exposition, impact métier
6. **Confronter** le coût d'une mesure de sécurité au risque qu'elle réduit
7. **Arbitrer** entre plusieurs mesures possibles, et dire ce que vous acceptez de ne pas faire
8. **Rédiger** un avis d'arbitrage court et argumenté

---

## Le parcours

| # | Étape | Durée |
| --- | --- | --- |
| 01 | Pourquoi sécuriser ? — enjeux business et humains | 45 min |
| TP | Analyser un incident 🟢 | 20 min |
| 02 | Sécurité proportionnée — risque, coût et confort | 55 min |
| TP | Arbitrer des mesures de sécurité 🟡 | 35 min |

Chaque bloc : un cours, puis un exercice à faire immédiatement.
Les corrigés sont dans `tp/corrige/`.

---

## Le périmètre de la journée

- On couvre la **sécurité logicielle** : le code, les configurations, les
  identités, les données et les échanges.
- **La sécurité physique est hors périmètre** : entrer dans un local, brancher
  une clé USB (Universal Serial Bus) sur un serveur, dérober une machine.
- Une menace physique peut contourner toute défense logicielle : on la signale
  quand elle borne une solution.

> Exemple : le chiffrement au repos protège un disque dérobé — pas quelqu'un qui
> tape sur le clavier d'une machine déjà allumée et déverrouillée.

---

## 1. Pourquoi sécuriser ?

### Enjeux business et humains

---

## Ce que coûte un incident

- Début 2023 : un hôpital des Yvelines est paralysé par un **rançongiciel**.
  - les urgences sont détournées, des interventions sont reportées ;
  - les dossiers patients redeviennent du papier pendant des semaines.
- L'année précédente, un autre établissement français : plusieurs mois de
  remise en état, des milliers de patients redirigés.
- Une **TPE** (très petite entreprise) peut être mise à genoux par une attaque
  partie d'un simple courriel piégé.

> Ce n'est pas une histoire de geeks — c'est une histoire de lits, de personnes,
> de soins annulés.

---

## Les postes de coût

| Poste | Ce que ça recouvre |
| --- | --- |
| **Interruption d'activité** | production à l'arrêt, commandes perdues, clients qui partent ailleurs |
| **Réparation et remise en état** | investigation, nettoyage, reconstruction des systèmes |
| **Image et confiance** | réputation entamée, prospects qui hésitent, partenaires qui s'inquiètent |
| **Sanctions et amendes** | manquements aux obligations légales |
| **Contentieux** | plaintes de clients ou de partenaires, recours, expertises |

> Un incident coûte rarement cher là où on l'attend : c'est **l'activité arrêtée**
> qui plombe le bilan, pas la facture du prestataire informatique.

---

## 🧪 Atelier rapide — 5 min

La fromagerie perd la base de ses commandes clients (noms, adresses,
historique d'achats).

Sans chercher la solution technique, listez les conséquences dans trois
catégories :

- **financier**
- **légal**
- **humain**

Trois lignes par catégorie suffisent.

---

## Qui sont les victimes ?

Derrière une fuite de données, il y a :

- **Les clients** — dont les données personnelles circulent sans contrôle :
  adresses, habitudes d'achat, parfois des données de paiement.
- **Les employés** — identifiants réutilisables ailleurs, stress d'un système
  à l'arrêt, charge de la remise en état.
- **Les patients, les usagers** — quand le service est vital, l'impact se
  mesure en soins non rendus, pas en euros.
- **Les partenaires et fournisseurs** — l'attaque passe souvent par un
  sous-traitant.

> La sécurité engage la continuité du service et la responsabilité légale de
> l'organisation.

---

## Sécuriser, c'est arbitrer

- La sécurité a aussi un **coût** : argent, temps, confort des utilisateurs,
  vitesse de développement.
- On ne sécurise pas « par principe » : on sécurise **ce qui a de la valeur, à
  la mesure de ce qui le menace** — et on laisse le reste tranquille.
- Protéger la page vitrine d'un artisan menuisier comme un système bancaire :
  gaspillage. L'inverse : négligence.

> Avant de choisir un outil : **ce que vous protégez, pour qui, contre quoi**.

---

## 🧪 TP — Analyser un incident · 🟢 20 min

**DIGICHEESE** : Sophie, responsable des commandes, saisit ses identifiants sur
une fausse page d'extranet. Dans la semaine : des commandes disparaissent, des
clients reçoivent un faux courriel de remboursement.

1. Décrire l'incident : **point d'entrée** et ce que l'attaquant a obtenu
2. Identifier les actifs touchés — **compromis** vs **menacés**
3. Classer selon les piliers **CID (Confidentialité, Intégrité, Disponibilité)**
4. Estimer l'impact : postes de coût, classement par gravité

> Auto-évaluation en fin d'énoncé, corrigé dans `tp/corrige/`.

---

## 2. Sécurité proportionnée

### Risque, coût et confort d'usage

---

## Tous les systèmes ne se valent pas

| Système | Ce qu'il contient | Qui y accède | Si ça tombe |
| --- | --- | --- | --- |
| **Le système d'une banque** | comptes, opérations, identités | des millions de clients, en ligne à toute heure | l'épargne est bloquée, la confiance casse |
| **L'extranet de la fromagerie** | commandes, adresses, historique d'achats | les clients et l'équipe des commandes | les commandes s'arrêtent, les clients partent |
| **Le site vitrine d'un artisan** | quelques pages, photos, coordonnées | tout le monde, en lecture seule | un site à remettre en ligne |
| **L'outil interne de gestion des congés** | noms et dates d'absence | les salariés, depuis le réseau interne | quelques jours de saisie sur papier |

---

## Trois questions suffisent

1. **Valeur des données** — que vaut ce qu'on y trouve, et pour qui ? Une
   adresse de livraison ne vaut pas un numéro de carte bancaire.
2. **Exposition** — qui peut y accéder ? Tout Internet, le réseau interne, une
   seule équipe ?
3. **Impact métier** — si le système est compromis ou indisponible, l'activité
   continue-t-elle ?

> La **criticité** naît de la combinaison des trois.

---

## 🧪 Atelier rapide — 8 min

Classez les quatre systèmes du tableau sur une échelle de 1 (faible) à 5
(critique) pour chacun des trois critères :

- valeur des données
- exposition
- impact si compromis

> Pas de bonne réponse à deviner : l'essentiel est de **dire votre raisonnement**
> pour chaque note.

---

## Le coût des mesures

| Mesure | Ce qu'elle apporte | Ce qu'elle coûte à l'utilisateur |
| --- | --- | --- |
| **MFA (authentification multi-facteurs)** | un mot de passe volé ne suffit plus | une étape de plus à chaque connexion |
| **Expiration de session** | une session oubliée ne reste pas ouverte | une reconnexion en plein travail |
| **Mots de passe longs et uniques** | pas de réutilisation entre les sites | un gestionnaire à apprivoiser |
| **Chiffrement des sauvegardes** | une sauvegarde volée reste illisible | aucun |
| **Journalisation des accès** | on sait qui a consulté quoi | aucun |

---

## Quand la mesure se retourne

Le prix se paie aussi **en sécurité**, quand la mesure est mal calibrée :

- des mots de passe trop complexes finissent sur un post-it collé à l'écran ;
- des sessions qui expirent trop vite multiplient les mots de passe réutilisés ;
- une **MFA** imposée partout finit par être contournée par habitude.

> Une mesure que les utilisateurs contournent ne protège plus rien : elle donne
> seulement l'impression de protéger.

---

## Sécurité, disponibilité, confort d'usage

- Aucune mesure n'est gratuite : argent, temps d'administration, et surtout
  **confort d'usage** — **UX (expérience utilisateur)** pour ceux qui l'utilisent
  au quotidien.
- Le bon niveau n'est pas le maximum : c'est celui que les gens acceptent
  d'appliquer, là où le risque le justifie.
- Les mesures sans coût d'usage (journalisation, chiffrement des sauvegardes) se
  généralisent ; celles qui coûtent du confort se réservent aux systèmes qui le
  méritent.

---

## L'avis d'arbitrage

Pour trancher, on croise deux questions : **quel risque la mesure
réduit-elle ?** et **combien coûte-t-elle à mettre en œuvre ?**

| | Effort faible | Effort élevé |
| --- | --- | --- |
| **Risque élevé** | à faire tout de suite | à planifier et à budgéter |
| **Risque faible** | à faire quand l'occasion se présente | à écarter, en le motivant |

---

## La trame de l'avis d'arbitrage

1. **Contexte** — quel système, quelle préoccupation.
2. **Mesures envisagées** — et ce qu'elles coûtent.
3. **Recommandation** — ce qu'on met en place, et pourquoi.
4. **Ce qu'on écarte** — et le risque résiduel qu'on accepte.

> Ce qu'on accepte de ne pas faire est un **choix** : il se motive, il se date,
> il se relit. Une mesure écartée avec raison est une décision.

---

## 🧪 TP — Arbitrer des mesures · 🟡 35 min

Quatre systèmes sur la table : la banque, l'extranet **DIGICHEESE**, le site
vitrine, l'outil interne de gestion des congés.

1. Évaluer la criticité : trois critères, notes de 1 à 5 justifiées
2. Choisir **au moins deux mesures** par système, reliées à la criticité
3. Nommer **au moins une mesure écartée** — et le risque résiduel accepté
4. Rédiger l'avis d'arbitrage de l'extranet de la fromagerie

---

## Points clés

- Un incident coûte d'abord par l'**interruption d'activité**.
- Les victimes dépassent l'entreprise : clients, employés, usagers, partenaires.
- La criticité se juge sur trois critères : **valeur des données**,
  **exposition**, **impact métier**.
- Toute mesure a un coût — et parfois un coût en sécurité quand elle est
  contournée.
- Arbitrer, c'est choisir quoi faire **et** quoi ne pas faire — et l'écrire.

---

## Aller plus loin

*Ces approfondissements sont facultatifs : ils ne sont jamais exigés pour
terminer la journée.*

- **ANSSI (Agence nationale de la sécurité des systèmes d'information)** :
  l'autorité française en matière de cybersécurité, et son « Panorama de la
  cybermenace ».
- **DBIR (Data Breach Investigations Report, Verizon)** : une étude annuelle de
  milliers d'incidents réels.
- **CNIL (Commission nationale de l'informatique et des libertés)** : le cadre
  et les sanctions liés aux données personnelles en France.
- **EBIOS (Expression des Besoins et Identification des Objectifs de sécurité)**,
  version **RM (méthode de gestion des risques)** : la méthode française de
  l'ANSSI pour analyser les risques de bout en bout.

---

## Des questions ?

### Le dépôt reste la référence

Pour toute question [adressez-vous au service pédagogie](mailto:pedagogie@diginamic.fr)
