# Corrigé — Analyser un incident

> Corrigé de [l'exercice « Analyser un incident »](../01-analyser-incident.md).
> Comparez d'abord votre travail aux **étapes** ci-dessous : la méthode compte
> autant que le résultat.

---

## Partie 1 — Décrire l'incident

**Éléments attendus :**

L'attaque est arrivée par un **courriel piégé** (hameçonnage) imitant un fournisseur.
Sophie a cliqué sur un lien et saisi ses identifiants sur un faux site : l'attaquant
a récupéré son compte d'accès à l'extranet. Avec cet accès, il a pu consulter les
commandes clients, puis s'en servir pour envoyer de faux courriels de
« remboursement » aux clients de la fromagerie.

**Ce qu'il faut retenir :** le point d'entrée est **humain et organisationnel**
(un courriel, un clic), pas une faille technique spectaculaire. La plupart des
incidents commencent ainsi.

---

## Partie 2 — Identifier les actifs touchés

**Compromis** (l'attaquant y a accédé) :

- le compte d'accès de Sophie à l'extranet ;
- la base des commandes clients (noms, adresses, historique d'achats) ;
- les coordonnées de contact des clients (utilisées pour les faux courriels).

**Menacés** (impactés sans accès direct avéré) :

- la confiance des clients envers la fromagerie ;
- le système de suivi de livraison (données devenues peu fiables) ;
- les comptes des autres employés (le même stratagème peut être rejoué).

---

## Partie 3 — Classer selon les piliers CID (Confidentialité, Intégrité, Disponibilité)

| Pilier | Affecté ? | Justification |
| --- | --- | --- |
| **Confidentialité** | ✅ Oui | Les commandes clients ont été lues par un tiers non autorisé. |
| **Intégrité** | ✅ Oui | Des commandes ont disparu du suivi : les données ont été modifiées ou supprimées. |
| **Disponibilité** | ✅ Oui, partiellement | Le suivi de livraison est dégradé : les informations ne sont plus fiables ni accessibles normalement. |

**Erreurs fréquentes :** considérer que la disponibilité n'est touchée que si le
site tombe complètement. Une donnée devenue **inutilisable** parce qu'on ne lui
fait plus confiance est aussi un problème de disponibilité. Inversement, ne pas
justifier un pilier « non affecté » est une erreur : l'absence d'impact est un
diagnostic, pas un oubli.

---

## Partie 4 — Estimer l'impact

**Éléments attendus** (classement indicatif — l'important est le critère explicite) :

1. **Sanctions et contentieux** — des données personnelles ont fui : obligations
   légales en jeu, plaintes possibles des clients.
2. **Image et confiance** — les clients ont été directement contactés par
   l'attaquant : la confiance est atteinte là où elle est la plus fragile.
3. **Interruption d'activité** — le suivi de livraison est perturbé, le traitement
   des commandes ralenti.
4. **Réparation et remise en état** — investigation, réinitialisation des accès,
   sécurisation du compte compromis.

**Sur le classement :** deux critères se défendent — la **gravité pour les
personnes** (ici les clients, d'où les sanctions et l'image en tête) ou le
**coût financier direct** (où l'interruption d'activité peut passer devant). Ce
qui est attendu, c'est que le critère soit **dit** : un classement sans critère
affiché ne se discute pas.

---

## Points à retenir

- Le point d'entrée est souvent **humain** : un courriel, un clic, un identifiant.
- Un même incident touche **plusieurs piliers CID** à la fois — rarement un seul.
- L'impact se juge d'abord sur **les personnes et l'activité**, ensuite sur la technique.
- Un classement d'impact n'a de valeur que si son **critère est explicite**.
