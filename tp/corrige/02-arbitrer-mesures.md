# Corrigé — Arbitrer des mesures de sécurité

> Corrigé de [l'exercice « Arbitrer des mesures de sécurité »](../02-arbitrer-mesures.md).
> Comparez d'abord votre travail aux **étapes** ci-dessous : la méthode compte
> autant que le résultat.

---

## Partie 1 — Évaluer la criticité

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

---

## Partie 2 — Choisir les mesures

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

---

## Partie 3 — Ce qu'on accepte de ne pas faire

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

---

## Partie 4 — Rédiger l'avis d'arbitrage

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

---

## Points à retenir

- La criticité se juge sur **trois critères** : valeur des données, exposition,
  impact métier.
- Les mesures sans coût d'usage se généralisent ; celles qui coûtent du confort se
  méritent.
- Écarter une mesure est un choix : il se motive, il se date, il se documente.
- Un bon avis d'arbitrage dit aussi **ce qu'on ne fait pas**.
