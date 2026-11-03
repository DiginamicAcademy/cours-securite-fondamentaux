# Exercice — Analyser un incident

> 🟢 **Débutant** · **Durée :** 20 min · **Lien :** chapitre [Pourquoi sécuriser ?](../01-pourquoi-securiser.md)
> **Objectif :** classifier un incident de sécurité : actifs touchés, piliers CID, impact.

---

## Contexte

**DIGICHEESE** (la fromagerie du fil rouge) vend ses fromages en ligne. Un lundi matin,
Sophie, responsable des commandes, ouvre un courriel qui semble venir de son
fournisseur de cartons. Elle clique sur le lien, saisit ses identifiants sur une
page qui ressemble à s'y méprendre à l'extranet de la fromagerie.

Dans la semaine qui suit :

- des commandes clients disparaissent du suivi de livraison ;
- plusieurs clients reçoivent un courriel de « remboursement » contenant un lien
  de paiement suspect ;
- la direction découvre la situation grâce à un client qui signale l'arnaque.

---

## Consignes

### Partie 1 — Décrire l'incident

En deux ou trois phrases, racontez ce qui s'est passé : **par quel point d'entrée**
l'attaque est arrivée, et **ce que l'attaquant a pu obtenir**.

### Partie 2 — Identifier les actifs touchés

Listez les actifs concernés (données, systèmes, personnes). Classez-les en deux
catégories : ce qui est **compromis** (l'attaquant y a accédé) et ce qui est
**menacé** (impacté sans être forcément compromis).

### Partie 3 — Classer selon les piliers CID (Confidentialité, Intégrité, Disponibilité)

Pour chaque pilier, dites s'il est affecté ou non, et justifiez en une phrase.
Un pilier non affecté doit être justifié lui aussi.

### Partie 4 — Estimer l'impact

En vous appuyant sur les postes de coût du chapitre (interruption, réparation,
image, sanctions, contentieux), listez les conséquences probables pour la
fromagerie. Classez-les par gravité, de la plus grave à la moins grave, et
expliquez votre classement en deux lignes.

---

## ✅ Auto-évaluation

Avant de passer au corrigé, vérifiez que :

- [ ] Ma description nomme le **point d'entrée** de l'attaque (et pas seulement ses conséquences).
- [ ] J'ai distingué actifs **compromis** et actifs **menacés**.
- [ ] J'ai donné un avis **justifié** pour les trois piliers CID, y compris ceux que je considère non affectés.
- [ ] Ma liste d'impact cite au moins **trois postes de coût** parmi ceux du chapitre.
- [ ] Mon classement de gravité s'appuie sur un **critère explicite** (argent, personnes, durée…).

---

## Pour aller plus loin

*Facultatif.* Refaites le même exercice en supposant que l'attaquant n'a pas
envoyé de faux courriels aux clients, mais s'est contenté de revendre la base de
commandes. Qu'est-ce qui change dans votre classification ?
