# Exercice — Construire une matrice menace → vulnérabilité → risque

> **Nature :** exercice · **Durée :** 25 min · **Notion :** construire la chaîne menace → vulnérabilité → risque → impact, et qualifier les risques d'un système
> 🟡 **Intermédiaire** · **Durée :** 25 min · **Lien :** chapitre [CID et vocabulaire du risque](../03-cid-et-vocabulaire.md)
> **Objectif :** construire une matrice menace → vulnérabilité → risque → impact, et qualifier les risques d'un système.

---

## Contexte

Une PME (petite et moyenne entreprise) de vente en ligne de fournitures de
bureau prépare sa revue annuelle des
risques. Son système repose sur quatre briques :

- un **site web de vente en ligne** (catalogue, panier, paiement géré par un
  prestataire) ;
- une **base de données des commandes** (noms, adresses de livraison,
  historique d'achats) ;
- un **export quotidien des ventes** vers un entrepôt de données, utilisé par
  l'équipe data pour alimenter les tableaux de bord ;
- une **interface d'administration**, joignable depuis Internet, utilisée par le
  service client.

Vous êtes chargé de construire la matrice des risques de ce système.

---

## Consignes

### Partie 1 — Formuler les vulnérabilités

L'audit a relevé cinq constats :

1. Le mot de passe de l'interface d'administration est partagé entre les six
   agents du service client.
2. Un fichier de configuration contenant les identifiants de la base de données
   est présent dans l'historique du dépôt Git.
3. Les sauvegardes de la base sont copiées sur le même serveur que l'application.
4. L'export quotidien vers l'entrepôt de données est transporté sans chiffrement.
5. L'interface d'administration ne limite pas le nombre de tentatives de
   connexion.

Pour chaque constat, formulez la vulnérabilité en une phrase : **quelle
faiblesse**, **où**, et **pourquoi elle est exploitable**.

### Partie 2 — Associer les menaces

Trois menaces ont été identifiées pour ce système :

- **M1** — un groupe criminel qui automatise la recherche de failles connues sur
  Internet ;
- **M2** — un ancien employé dont le compte n'a pas été désactivé après son
  départ ;
- **M3** — un attaquant qui vise spécifiquement les données clients pour les
  revendre.

Associez chaque menace aux vulnérabilités de la partie 1 qu'elle peut exploiter.
Justifiez chaque association en une ligne. Une menace peut viser plusieurs
vulnérabilités, et une vulnérabilité peut servir à plusieurs menaces.

### Partie 3 — Construire la matrice

Complétez la matrice ci-dessous : pour chaque couple menace × vulnérabilité
retenu, écrivez le **risque** (ce qui peut arriver), l'**impact métier**
(conséquence pour l'activité et pour les clients), et le ou les **piliers CID**
(Confidentialité, Intégrité, Disponibilité) touchés.

| Menace | Vulnérabilité | Risque | Impact métier | Pilier(s) CID |
| --- | --- | --- | --- | --- |
| | | | | |
| | | | | |
| | | | | |

### Partie 4 — Qualifier et prioriser

Classez les risques de votre matrice du plus prioritaire au moins prioritaire, en
croisant **probabilité** et **gravité**. Donnez votre critère de classement de
façon explicite, puis nommez **les deux risques** que vous traitez en premier et,
pour chacun, la mesure de premier niveau que vous proposez — sans entrer dans le
détail technique.

---

## ✅ Auto-évaluation

Avant de passer au corrigé, vérifiez que :

- [ ] Chaque vulnérabilité est formulée en une phrase : faiblesse, lieu, raison pour laquelle elle est exploitable.
- [ ] Chaque menace est associée à au moins une vulnérabilité, avec une justification.
- [ ] Ma matrice est complète : chaque ligne relie une menace, une vulnérabilité, un risque, un impact et un pilier CID.
- [ ] Mon classement affiche son critère (probabilité, gravité, ou les deux).
- [ ] J'ai nommé les deux risques prioritaires et une mesure de premier niveau pour chacun.

---

## Pour aller plus loin

*Facultatif.* Ajoutez une quatrième menace de votre choix — interne, technique ou
humaine — et la ligne de matrice qui va avec. Qu'est-ce que cette menace change à
votre classement ?
