# Corrigé — Cartographier les zones de confiance d'une plateforme data

> Corrigé de [l'exercice « Cartographier les zones de confiance d'une plateforme data »](../04-cartographier-si.md).
> Comparez d'abord votre travail aux **étapes** ci-dessous : la méthode compte
> autant que le résultat. Une autre découpe en zones peut se défendre, à condition
> d'être justifiée.

---

## Partie 1 — Lister les composants et les flux

**Éléments attendus** — une liste de flux, pas une liste de machines :

| Flux | Source | Destination | Contenu | Sens |
| --- | --- | --- | --- | --- |
| F1 | Les boutiques | Stockage d'objet | Exports quotidiens de ventes | Écriture |
| F2 | Orchestrateur | Stockage d'objet | Lecture des exports pour chargement | Lecture |
| F3 | Orchestrateur | Base de données | Données consolidées | Écriture |
| F4 | API web | Base de données | Indicateurs agrégés | Lecture |
| F5 | Utilisateurs | API web | Consultation des tableaux de bord | Lecture |

**Ce qu'il faut retenir :** un flux se décrit par sa **source**, sa
**destination**, son **contenu** et son **sens**. Sans le contenu, on ne sait pas
ce qui fuit en cas de problème ; sans le sens, on ne sait pas qui a le droit
d'écrire où.

---

## Partie 2 — Délimiter les zones de confiance

**Découpe indicative** en quatre zones :

| Zone | Contenu | Niveau de confiance |
| --- | --- | --- |
| **Zone publique** | Internet, les boutiques qui déposent leurs exports, les utilisateurs à distance | aucune confiance a priori |
| **Zone de présentation** | l'API web | exposée, donc conçue pour être hostile |
| **Zone de traitement** | l'orchestrateur de traitements | confiance technique, accès restreint |
| **Zone de données** | la base de données et le stockage d'objet | la valeur de la plateforme |

**Justification des frontières :**

- **Publique ↔ présentation** : tout ce qui vient de l'extérieur est non fiable ;
  l'API web est le seul composant conçu pour l'être, et pour n'exposer que des
  lectures.
- **Présentation ↔ traitement** : l'API lit des indicateurs, elle ne déclenche
  pas de traitements. Séparer les deux évite qu'une faille web donne la main sur
  l'orchestration de la plateforme.
- **Traitement ↔ données** : l'orchestrateur doit lire les exports et écrire les
  données consolidées — un accès technique, limité à ce besoin, et rien de plus.
- **Interne ↔ données** : les analystes interrogent la base, mais depuis des
  postes identifiés, pas depuis n'importe où.

**Erreur fréquente :** découper par type de machine (« les serveurs web, les
serveurs de base ») au lieu de découper par **niveau de confiance**. Ce qui
définit une zone, c'est la confiance qu'on lui accorde — pas la technologie qui
la compose.

---

## Partie 3 — Placer les étapes de la kill chain

**Éléments attendus** (la zone et le composant varient selon votre carte, la
logique reste la même) :

| Étape | Zone | Composant visé | Ce qui la rend possible |
| --- | --- | --- | --- |
| **Reconnaissance** | publique | l'API web | tout ce qui est visible : documentation, schéma d'API, annonces de recrutement, dépôts publics |
| **Intrusion** | présentation | l'API web ou un compte utilisateur | hameçonnage d'un analyste, identifiants réutilisés, faille web non corrigée |
| **Exploitation** | traitement | l'orchestrateur | un compte de service trop puissant, un secret de configuration accessible depuis l'API |
| **Persistance** | traitement ou données | l'orchestrateur, la base | tâche planifiée ajoutée, compte de service créé, vue de lecture oubliée |
| **Exfiltration** | frontière sortante | le stockage d'objet ou la base | flux sortants non surveillés, copies vers un stockage externe |

**Points de vigilance :**

- L'**exfiltration** n'est pas « dans » une zone : c'est un **flux qui sort**.
  Elle se voit aux frontières, ce qui en fait le contrôle le plus rentable de la
  chaîne.
- L'**orchestrateur** est souvent le maillon le plus utile à un attaquant : il
  parle à tout le monde, déclenche des traitements, et détient des accès
  techniques. L'oublier dans la carte est l'erreur la plus fréquente.

---

## Partie 4 — Points de contrôle

**Éléments attendus** — un contrôle par franchissement de frontière, avec sa
nature :

| Frontière | Contrôle | Empêche ou détecte |
| --- | --- | --- |
| Publique → présentation | authentification des utilisateurs, limitation du nombre de tentatives | empêche |
| Publique → présentation | journalisation des accès et des erreurs | détecte |
| Présentation → données | compte d'application aux privilèges limités (lecture seule des indicateurs) | empêche |
| Présentation → données | journalisation des requêtes exécutées | détecte |
| Traitement → données | comptes de service nominatifs, chiffrement du transport | empêche |
| Traitement → données | alerte sur les volumes de lecture anormaux | détecte |
| Boutiques → stockage | jeton d'accès propre à chaque boutique | empêche |
| Boutiques → stockage | contrôle d'intégrité des exports reçus | détecte |

**Erreurs fréquentes :** accumuler les contrôles qui **empêchent** sans jamais
prévoir ceux qui **détectent** — alors qu'une protection contournée ne se voit
qu'avec la détection ; ou citer un contrôle générique (« un pare-feu ») sans dire
quelle frontière il protège et contre quoi.

---

## Points à retenir

- Une **zone de confiance** regroupe ce à quoi on accorde le même niveau de
  confiance — pas le même type de machine.
- La **kill chain** se lit sur la carte : chaque étape est une zone, un composant
  et une condition qui la rend possible.
- L'**exfiltration** se détecte aux frontières sortantes : c'est là que la
  surveillance rapporte le plus.
- Tout flux qui franchit une frontière porte **au moins un contrôle**, et l'on
  sait s'il empêche ou s'il détecte.
