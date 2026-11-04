# Exercice d'intégration — Sécuriser le lancement d'une boutique en ligne

> **Nature :** exercice d'intégration (non noté) · **Durée :** 75 min · **Notion :** mobiliser toute la journée, de l'enjeu métier à la note de sécurité
> 🔵 **Intégration** · **Lien :** la journée entière ([chapitres 01 à 06](Readme.md))
> **Objectif :** produire une note de sécurité de lancement, de bout en bout, pour un service simple.

---

## Contexte

**La Roue Libre** est un magasin de vélos de quartier, huit salariés. Après dix
ans de comptoir, la boutique lance sa **vente en ligne** — le lancement est prévu
dans trois semaines.

Le projet repose sur six briques :

- un **site de vente en ligne** : catalogue, panier, paiement géré par un
  prestataire — aucune carte bancaire n'est stockée par la boutique ;
- une **base de commandes** : nom, prénom, adresse e-mail, adresse de livraison,
  historique des achats ;
- un **espace client** : compte, mot de passe, suivi de commande ;
- une **interface d'administration** pour les deux employés du service client,
  joignable depuis Internet ;
- un **export quotidien des ventes** vers un tableur de suivi, utilisé par la
  gérante ;
- un **prestataire d'hébergement** qui héberge le site, la base — et les
  sauvegardes automatiques.

La gérante pose une seule question : « **qu'est-ce qu'il faut absolument faire
avant le lancement, et qu'est-ce qui peut attendre ?** »

Votre mission : y répondre par écrit, dans une **note de sécurité de lancement**.

---

## Objectifs

À l'issue de cet exercice, vous serez capable de :

- **Décrire** les actifs du service et les victimes d'un incident éventuel.
- **Évaluer** la criticité de chaque brique : valeur des données, exposition, impact métier.
- **Relier** menace, vulnérabilité, risque et impact sur les cas du contexte.
- **Raconter** une attaque plausible étape par étape, et dire où l'arrêter.
- **Cartographier** les zones de confiance et leurs flux, puis proposer une défense en couches.
- **Traduire** les obligations RGPD (Règlement général sur la protection des données) du projet en contraintes concrètes.
- **Rédiger** une note de sécurité qui arbitre : ce qu'on fait avant, ce qu'on fait après, ce qu'on accepte de ne pas faire.

---

## Étapes

### 1. Ce qu'on protège, et pour qui — chapitre 01

Listez les actifs en jeu (données, systèmes, personnes), puis nommez les
victimes d'un incident : au-delà de la boutique elle-même. Enfin, dites ce qu'un
incident coûterait, en reprenant les postes de coût du cours — sans chercher de
chiffre précis.

### 2. Ce que chaque brique mérite — chapitre 02

Notez la criticité de chaque brique de 1 (faible) à 5 (critique) sur les trois
critères du cours — valeur des données, exposition, impact métier — avec une
justification d'une ligne par brique. Puis, pour les deux briques les plus
critiques, retenez **au moins deux mesures** de ce menu, et nommez **une mesure
que vous écartez**, avec le risque résiduel que vous acceptez :

| Mesure | Ce qu'elle coûte à l'utilisateur |
| --- | --- |
| **MFA (authentification multi-facteurs)** à chaque connexion | une étape de plus, un code à saisir |
| **Expiration de session** courte | une reconnexion en plein travail |
| **Mots de passe longs et uniques**, gestionnaire fourni | un outil à apprivoiser |
| **Chiffrement des sauvegardes** | aucun |
| **Journalisation des accès** | aucun |
| **Sensibilisation de l'équipe** (hameçonnage, bons réflexes) | du temps de formation |

### 3. Lire le risque avec les bons mots — chapitre 03

Relevez **trois faiblesses** du contexte — un compte partagé, une sauvegarde mal
placée, un export qui circule en clair… à vous de trouver celles du cas. Pour
chacune, écrivez la ligne complète :

`menace → vulnérabilité → risque → impact`, avec le ou les piliers CID
(Confidentialité, Intégrité, Disponibilité) touchés.

Terminez par la **surface d'attaque** du service : ce qui est joignable, ce qui
est visible, ce qui permet d'aller plus loin.

### 4. Raconter une attaque, et dire où l'arrêter — chapitre 04

Choisissez l'une de vos lignes de risque et reconstituez-la en **kill chain** :
reconnaissance, intrusion, exploitation, persistance, exfiltration. Pour chaque
étape : ce que fait l'attaquant, et la mesure qui **coupe la chaîne ici**.

### 5. Cartographier les zones, défendre en couches — chapitre 05

La méthode est celle de la [cartographie des zones de confiance](04-cartographier-si.md),
appliquée ici à votre contexte :

- regroupez les briques en **zones de confiance** (deux à quatre) et listez les
  **flux** qui les traversent — `source → destination`, contenu transporté, sens ;
- pour chaque flux qui franchit une frontière, nommez le **contrôle** qui devrait
  exister, en distinguant ce qui **empêche** de ce qui **détecte** ;
- organisez la défense en **couches indépendantes** (réseau, identités,
  application, données, détection) ;
- appliquez le **moindre privilège** aux comptes — les deux employés du service
  client, la gérante, l'export quotidien — et dites où la confiance doit être
  **prouvée à chaque appel** (Zero Trust) plutôt que déduite de la position,
  notamment entre la boutique et le prestataire.

### 6. Traduire le RGPD en contraintes — chapitre 06

Repérez les **données personnelles** du contexte. Dites ce qui manque au projet
au regard des principes du cours — finalité, minimisation, durée de conservation,
transparence — et traduisez chaque manquement en **une contrainte concrète** : ce
qu'il faut faire, où, et à quel moment.

Enfin, rédigez la procédure à suivre si la base de commandes est retrouvée chez
un tiers : qui prévenir, quoi documenter, dans quel ordre — et à partir de quand
court le délai.

### 7. Rédiger la note de sécurité de lancement — le livrable

Rassemblez le tout dans une note de deux à trois pages, avec ces sections :

1. **Contexte** — le service, ce qu'il y a à protéger.
2. **Actifs et criticité** — le résultat des étapes 1 et 2.
3. **Risques prioritaires** — trois lignes de risque au maximum, choisies et motivées.
4. **Carte de sécurité et défense en couches** — le résultat des étapes 4 et 5.
5. **Contraintes légales** — le résultat de l'étape 6.
6. **Arbitrage** — ce qu'on fait **avant** le lancement, ce qu'on fait **après**,
   ce qu'on **n'accepte pas de faire** — et pourquoi, pour chacun des trois.

---

## Livrable

**Une note de sécurité de lancement** (deux à trois pages), unique : c'est elle
qui répond à la question de la gérante. Les étapes 1 à 6 en sont la matière, pas
des livrables à part.

Cet exercice n'est **pas noté** : il sert à vérifier que la journée tient
ensemble, de bout en bout.

---

## ✅ Auto-évaluation

Avant de considérer la note terminée, vérifiez que :

- [ ] Ma note nomme les **actifs** et les **victimes**, au-delà de la boutique.
- [ ] Chaque brique a une **criticité justifiée**, et les mesures retenues sont reliées à cette criticité.
- [ ] Au moins **trois lignes de risque** complètes : menace, vulnérabilité, risque, impact, piliers CID.
- [ ] Ma kill chain se lit **en cinq étapes**, et chacune a une mesure qui la coupe.
- [ ] Mes zones sont nommées, mes flux listés, et chaque frontière a un **contrôle** associé.
- [ ] Ma défense est décrite **en couches indépendantes**, et les comptes sont au moindre privilège.
- [ ] Chaque obligation RGPD devient une **contrainte concrète** — ce qu'on fait, où, quand.
- [ ] La procédure de violation nomme l'**autorité de contrôle**, le **délai de 72 heures** et son point de départ.
- [ ] Mon arbitrage dit ce qu'on fait avant, après, et ce qu'on **n'accepte pas de faire** — avec une raison pour chacun.

---

## Pour aller plus loin

*Facultatif.* La gérante envisage d'ajouter un **programme de fidélité** — carte
avec historique d'achats sur cinq ans — six mois après le lancement. Reprenez
votre note : qu'est-ce que ce projet change à vos contraintes légales, à votre
criticité, et à votre arbitrage ?
