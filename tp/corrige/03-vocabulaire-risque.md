# Corrigé — Construire une matrice menace → vulnérabilité → risque

> Corrigé de [l'exercice « Construire une matrice menace → vulnérabilité → risque »](../03-vocabulaire-risque.md).
> Comparez d'abord votre travail aux **étapes** ci-dessous : la méthode compte
> autant que le résultat. Les formulations proposées ne sont pas les seules
> valables — elles montrent le niveau de précision attendu.

---

## Partie 1 — Formuler les vulnérabilités

**Éléments attendus** (une phrase par constat : faiblesse + lieu + raison pour
laquelle elle est exploitable) :

1. L'interface d'administration repose sur un compte partagé : la faiblesse est
   l'absence d'identité nominative, sur l'interface d'administration, ce qui rend
   chaque action non attribuable et le départ d'un agent invisible.
2. Les identifiants de la base de données sont stockés en clair dans un fichier
   présent dans l'historique du dépôt Git : la faiblesse est un secret committé,
   dans le dépôt de code, exploitable par quiconque accède à cet historique.
3. Les sauvegardes sont copiées sur le même serveur que l'application : la
   faiblesse est l'absence d'isolement des sauvegardes, sur le serveur
   d'application, ce qui permet de toucher aux deux en une seule action.
4. L'export quotidien vers l'entrepôt de données circule sans chiffrement : la
   faiblesse est l'absence de protection du transport, sur le flux d'export,
   exploitable par qui peut observer ce flux.
5. L'interface d'administration accepte un nombre illimité de tentatives de
   connexion : la faiblesse est l'absence de limitation des essais, sur le point
   d'authentification, ce qui rend la devinette de mot de passe automatisable.

**Ce qu'il faut retenir :** une vulnérabilité n'est pas un « problème de
sécurité » vague. Elle nomme **une faiblesse**, **un endroit**, et **ce qui la
rend exploitable** — sans quoi on ne peut pas la traiter.

---

## Partie 2 — Associer les menaces

**Associations probables** (justification en une ligne) :

- **M1** (groupe criminel automatisé) → constats 2 et 5 : les robots publics
  indexent les dépôts et testent les interfaces sans limitation de tentatives,
  sans cibler personne en particulier.
- **M2** (ancien employé) → constats 1 et 5 : il connaît le mot de passe partagé
  et peut revenir sur l'interface sans être bloqué ni reconnu.
- **M3** (attaquant intéressé par les données clients) → constats 2, 3 et 4 : les
  identifiants de la base donnent un accès direct, les sauvegardes isolées
  nulle part offrent tout l'historique en une copie, et l'export non chiffré se
  lit en transit.

**Erreurs fréquentes :** associer chaque menace à exactement une vulnérabilité
(comme un QCM à choix unique) — les menaces réelles enchaînent plusieurs
faiblesses ; ou justifier par « c'est dangereux » au lieu de dire **pourquoi ce
moyen-là** atteint **cette faiblesse-là**.

---

## Partie 3 — Construire la matrice

**Matrice indicative** — d'autres couples se défendent, à condition que la chaîne
soit complète :

| Menace | Vulnérabilité | Risque | Impact métier | Pilier(s) CID |
| --- | --- | --- | --- | --- |
| M3 | Identifiants de base dans l'historique Git | Accès direct à la base de commandes | Fuite des données clients, notification, perte de confiance | Confidentialité |
| M1 | Interface sans limitation de tentatives | Prise de contrôle d'un compte du service client | Commandes détournées, temps d'investigation | Confidentialité, Intégrité |
| M3 | Export quotidien sans chiffrement | Interception des exports de ventes | Fuite de données clients et commerciales | Confidentialité |
| M2 | Mot de passe partagé | Accès durable à l'interface par un ancien employé | Actions non attribuables, modifications possibles | Confidentialité, Intégrité |
| M3 | Sauvegardes sur le même serveur | Copie de l'ensemble des données en une seule action | Fuite massive, remise en confiance longue | Confidentialité |
| M1 | Sauvegardes sur le même serveur | Chiffrement de l'application et des sauvegardes par un rançongiciel | Activité arrêtée, restauration impossible | Disponibilité |

**Points de vigilance :**

- La colonne « risque » décrit **ce qui peut arriver** ; la colonne « impact »
  décrit **ce que ça coûte** à l'activité et aux clients. Écrire « fuite de
  données » dans les deux colonnes signale qu'on n'a pas fait la distinction.
- Un pilier CID (Confidentialité, Intégrité, Disponibilité) non touché n'a pas à
  figurer ; mais si vous hésitez entre deux, mettez les deux et dites pourquoi.

---

## Partie 4 — Qualifier et prioriser

**Éléments attendus** (classement indicatif — l'important est le critère
explicite) :

1. **M3 × identifiants dans l'historique Git** — probabilité élevée (l'exposition
   est déjà là, indépendamment de toute action de l'attaquant) et gravité
   maximale (fuite de données personnelles).
2. **M1 × interface sans limitation de tentatives** — probabilité élevée
   (l'attaque est automatisée et gratuite pour l'attaquant), gravité forte (prise
   de compte).
3. **M3 × export sans chiffrement** — probabilité moyenne (il faut être sur le
   flux), gravité forte (données clients et commerciales).
4. **M2 × mot de passe partagé** — probabilité faible à moyenne (il faut un
   départ), gravité moyenne (mais détection difficile).
5. **Sauvegardes sur le même serveur** — probabilité faible, gravité maximale :
   c'est le risque qui ne se voit qu'au moment où on en a besoin.

**Les deux risques à traiter en premier, et la mesure de premier niveau :**

- **Les identifiants de base exposés** — réinitialiser les identifiants et
  purger l'historique du dépôt, avant toute autre action : la porte est déjà
  ouverte.
- **L'interface sans limitation de tentatives** — limiter les tentatives de
  connexion et passer en comptes nominatifs : cela réduit la probabilité et rend
  les actions attribuables.

**Sur le classement :** deux critères se défendent — la **probabilité × gravité**
(ici) ou le **coût de traitement** (où les sauvegardes isolées, peu chères,
remonteraient dans le classement). Ce qui est attendu, c'est que le critère soit
**dit** : un classement sans critère affiché ne se discute pas.

---

## Points à retenir

- Une vulnérabilité se formule en une phrase : **faiblesse + lieu + raison pour
  laquelle elle est exploitable**.
- La matrice relie quatre niveaux — menace, vulnérabilité, risque, impact — et
  ajoute le pilier CID touché : c'est ce qui la rend discutable et donc utile.
- Un même couple menace × vulnérabilité peut produire plusieurs risques (fuite
  **et** activité arrêtée) : ne les fusionnez pas.
- Prioriser, c'est choisir **deux risques à traiter maintenant** — et savoir
  dire pourquoi les autres attendent.
