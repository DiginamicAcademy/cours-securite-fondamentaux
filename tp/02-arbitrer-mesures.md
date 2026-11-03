# Exercice — Arbitrer des mesures de sécurité

> 🟡 **Intermédiaire** · **Durée :** 35 min · **Lien :** chapitre [Sécurité proportionnée](../02-securite-proportionnee.md)
> **Objectif :** évaluer la criticité de quatre systèmes, choisir les mesures qui
> les protègent — et dire ce qu'on accepte de ne pas faire.

---

## Contexte

Après l'incident raconté dans le chapitre précédent, la direction de la fromagerie
*Les Comtés du Jura* décide de revoir sa sécurité. Le cabinet qui l'accompagne
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

---

## Consignes

### Partie 1 — Évaluer la criticité

Pour chaque système, notez de 1 (faible) à 5 (critique) les trois critères du
chapitre : **valeur des données**, **exposition**, **impact si compromis**.
Justifiez chaque note en une ligne. Classez ensuite les quatre systèmes du plus
critique au moins critique.

### Partie 2 — Choisir les mesures

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

### Partie 3 — Ce qu'on accepte de ne pas faire

Pour chaque système, nommez **au moins une mesure du menu que vous écartez**, et
motivez : quel risque reste-t-il, et pourquoi est-il acceptable ici ? Si vous
estimez qu'aucune mesure n'est écartable pour un système, dites-le et expliquez
pourquoi : c'est un arbitrage comme les autres.

### Partie 4 — Rédiger l'avis d'arbitrage

En une dizaine de lignes maximum, rédigez l'avis pour **l'extranet de la
fromagerie**, en suivant la trame du chapitre : contexte, mesures retenues,
mesures écartées, recommandation.

---

## ✅ Auto-évaluation

Avant de passer au corrigé, vérifiez que :

- [ ] J'ai noté les trois critères pour les **quatre** systèmes, et justifié chaque note.
- [ ] Mon classement de criticité est **explicite** : je peux le défendre à l'oral.
- [ ] Chaque système a **au moins deux mesures** retenues, reliées à sa criticité.
- [ ] J'ai nommé **au moins une mesure écartée** par système, avec le risque résiduel accepté.
- [ ] Mon avis d'arbitrage dit ce qu'on fait **et** ce qu'on ne fait pas, avec une raison.

---

## Pour aller plus loin

*Facultatif.* Le cabinet suggère d'ajouter la MFA partout, « ça ne coûte rien ».
Reprenez votre avis : qu'auriez-vous répondu, et sur quels systèmes cette mesure
vous semble-t-elle justifiée ou excessive ?
