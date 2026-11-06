[← Chapitre précédent](04-paysage-cyber.md) · [Sommaire](Readme.md) · [Chapitre suivant →](06-cadre-juridique-intro.md)

# Modèles de défense — la sécurité en couches

> Un château fort : des douves, un rempart, un donjon. Si une couche tombe, les
> autres tiennent encore. Aucune mesure prise isolément ne protège un système —
> c'est leur **empilement** qui le protège, et la façon dont on accorde (ou non)
> sa confiance.

**Durée :** ≈ 20 min (lecture ≈ 12 min + atelier 5 min + réflexion et lecture de code) · **Prérequis :** [Le paysage de la cybersécurité](04-paysage-cyber.md)

---

## Objectifs

À l'issue de ce chapitre, vous serez capable de :

- **Décomposer** la défense d'une application en couches indépendantes.
- **Appliquer** le principe Zero Trust (« ne jamais faire confiance, toujours
  vérifier ») à une architecture cloud ou API (Application Programming Interface,
  interface de programmation).
- **Réduire** les privilèges de chaque acteur au strict nécessaire.
- **Situer** la maturité de sécurité d'une organisation avec un cadre de référence.

---

## I. Defense in depth — la défense en profondeur

L'analogie du château fort fonctionne parce qu'elle dit une chose simple : le
rempart n'est pas la seule défense, et sa chute n'est pas la fin de l'histoire.
En informatique, **defense in depth** (défense en profondeur) empile des mesures
**indépendantes**, de sorte qu'une défaillance isolée ne compromette pas le tout.

| Couche | Rôle | Exemple | Si elle tombe |
| --- | --- | --- | --- |
| **Réseau** | limiter ce qui est joignable | règles de sécurité cloud, filtrage | un port ouvert en trop |
| **Identités** | vérifier qui parle | comptes nominatifs, authentification multi-facteurs | un mot de passe volé |
| **Application** | rejeter ce qui est malveillant | validation des entrées, requêtes paramétrées | une injection exploitable |
| **Données** | rendre illisible, permettre de revenir en arrière | chiffrement, sauvegardes isolées | une sauvegarde volée ou chiffrée |
| **Détection** | voir et réagir | journalisation centralisée, alertes | une attaque invisible |

Le point décisif : ces couches doivent être **indépendantes**. Si la même erreur
de configuration ouvre le réseau, l'application et les données, l'empilement
n'existe que sur le papier.

> 🧪 **Atelier rapide (5 min)**
>
> Prenez une application que vous connaissez — une boutique en ligne, un
> tableau de bord data, un outil interne. Listez les couches qui la protègent
> aujourd'hui, puis dites pour chacune ce qui se passe **si elle tombe seule**.
> La couche « détection » est-elle dans votre liste ? Dans la plupart des
> systèmes réels, c'est elle qui manque.

> [!WARNING]
> Une mesure unique, même excellente, devient le seul point de défaillance du
> système. Un pare-feu parfaitement réglé ne protège rien contre un mot de passe
> deviné ; un chiffrement irréprochable ne protège pas contre un compte
> administrateur partagé.

---

## II. Zero Trust — ne jamais faire confiance, toujours vérifier

Pendant longtemps, la confiance s'arrêtait au mur : ce qui était **à
l'intérieur** du réseau d'entreprise était considéré comme sûr, ce qui était
dehors ne l'était pas. Le cloud, le travail à distance, les API et les
appels de service à service ont rendu cette frontière illisible — un compte
volé est « à l'intérieur » sans que personne ne l'ait décidé.

Le principe **Zero Trust** (« zéro confiance ») inverse la règle : **chaque
requête est vérifiée, quelle que soit son origine**. Concrètement :

- un service qui en parle à un autre s'authentifie, même au sein du même réseau ;
- l'accès est accordé **pour une durée et un périmètre limités**, pas pour
  toujours ;
- la vérification est **continue** : une session ouverte n'est pas un blanc
  seing, et un changement de contexte (lieu, appareil, comportement) peut la
  remettre en question ;
- le cloisonnement découpe le système en zones où une compromission reste
  locale (voir l'exercice 1 de ce chapitre).

Exemple tiré d'une plateforme data : un worker d'orchestration (Airflow) qui
accède à un stockage d'objet (MinIO) présente un jeton propre à sa tâche, valable
le temps du traitement — même si les deux composants partagent le même réseau
interne. La confiance n'est plus déduite de la position : elle est **prouvée** à
chaque appel.

> [!TIP]
> Zero Trust est une direction, pas un produit à installer. Le premier pas
> tient en une question, posée à chaque flux : « si ce composant était
> compromis, que pourrait-il faire de plus que ce dont il a besoin ? »

---

## III. Le moindre privilège

Le **moindre privilège** (least privilege) est le pendant opérationnel de Zero
Trust : chaque acteur — personne, application, tâche planifiée — ne dispose que
du **strict nécessaire**, et rien de plus.

Côté base de données (SQL, Structured Query Language), cela se traduit
directement dans les droits accordés :

```sql
-- Un compte d'application n'a pas besoin d'être administrateur de la base :
-- on lui accorde uniquement ce qu'il utilise réellement.
CREATE ROLE app_ventes LOGIN;
GRANT SELECT, INSERT ON commandes TO app_ventes;
```

Trois applications concrètes de ce principe :

1. **Les comptes sont nominatifs.** Un compte partagé rend toute action non
   attribuable — et le départ d'un collaborateur invisible.
2. **Les comptes de service sont taillés au plus juste.** Le job qui exporte les
   ventes lit un répertoire, pas tout le stockage.
3. **Les privilèges se revisent.** Un droit accordé pour un projet survit
   souvent au projet : la revue périodique des accès fait partie de la mesure.

Le moindre privilège réduit deux choses à la fois : la **probabilité** qu'un
accès compromis mène loin, et l'**impact** quand cela arrive.

---

## IV. Situer sa maturité de sécurité

Une fois les couches posées, reste à savoir où l'on en est. Un **cadre de
maturité** donne une échelle commune pour se situer, comparer et progresser. Le
plus utilisé est le **NIST (National Institute of Standards and Technology) CSF
(Cybersecurity Framework)**, qui organise la sécurité en cinq fonctions :
**identifier, protéger, détecter, répondre, restaurer**.

L'usage en est simple : pour chaque fonction, dire ce qui est assuré, ce qui ne
l'est pas encore, et à quel niveau. On obtient une photographie honnête plutôt
qu'une liste de vœux. Et le niveau visé n'est pas le même pour tout le monde :
il dépend de la criticité du système — on retrouve la logique de
[sécurité proportionnée](02-securite-proportionnee.md).

---

### Exercice 1 — Cartographier les zones de confiance d'une plateforme data (30 min)

**Contexte.**

Une plateforme de décisionnel consolide les ventes d'une chaîne de magasins et
les restitue aux équipes. Elle repose sur cinq composants :

- une **API web** (FastAPI) qui expose des indicateurs de vente, accessible
  depuis Internet ;
- une **base PostgreSQL** qui stocke les données de vente consolidées ;
- un **stockage d'objet** (MinIO) qui reçoit les exports quotidiens des boutiques ;
- un **orchestrateur de traitements** (Airflow) qui déclenche les exports et les
  chargements ;
- les **utilisateurs** : analystes data, service client et direction, qui se
  connectent depuis le réseau interne ou à distance.

L'équipe data doit présenter sa plateforme à la direction sous l'angle sécurité.
Votre mission : produire la carte qui rend cette présentation crédible.

**Partie 1 — Lister les composants et les flux.**

Pour chaque composant, indiquez ce qu'il **reçoit**, ce qu'il **envoie**, et
**à qui**. Formalisez ensuite la liste des flux sous la forme
`source → destination` avec, pour chacun, le **contenu** transporté et le
**sens** (lecture, écriture, les deux).

**Partie 2 — Délimiter les zones de confiance.**

Regroupez les composants en **zones de confiance** — l'équipe en retient
généralement quatre sur ce type de plateforme. Pour chaque zone : un nom, ce
qu'elle contient, et la **justification de chaque frontière** : pourquoi ce qui
est d'un côté n'a pas besoin d'être de l'autre.

**Partie 3 — Placer les étapes de la kill chain.**

Les cinq étapes de la kill chain (reconnaissance, intrusion, exploitation,
persistance, exfiltration) se déroulent quelque part sur votre carte. Pour
chacune : la **zone** où elle se passe le plus probablement, le **composant**
visé, et **ce qui la rend possible** ici.

**Partie 4 — Points de contrôle.**

Pour chaque flux qui franchit une frontière, nommez le **contrôle** qui devrait
exister (authentification, chiffrement, journalisation, filtrage…). Distinguez
les contrôles qui **empêchent** de ceux qui **détectent**.

**Avant d'ouvrir la correction**, vérifiez que :

- [ ] Ma liste de flux indique source, destination, contenu et sens pour chaque flux.
- [ ] Mes zones sont nommées et peuplées, et chaque frontière est justifiée.
- [ ] Les cinq étapes de la kill chain sont placées sur la carte, avec le composant visé.
- [ ] Chaque flux qui franchit une frontière a au moins un contrôle associé.
- [ ] J'ai distingué les contrôles qui empêchent de ceux qui détectent.

*Pour aller plus loin (facultatif).*

Un analyste doit accéder à la base depuis l'extérieur du réseau
interne. Redessinez la carte pour intégrer ce flux : qu'est-ce qui change dans
vos zones et dans vos contrôles ?

<details>
<summary>Voir la correction</summary>

Comparez d'abord votre travail aux **étapes** ci-dessous : la méthode compte autant que le résultat. Une autre découpe en zones peut se défendre, à condition d'être justifiée.

**Partie 1 — Lister les composants et les flux.**

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

**Partie 2 — Délimiter les zones de confiance.**

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

**Partie 3 — Placer les étapes de la kill chain.**

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

**Partie 4 — Points de contrôle.**

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

**Points à retenir.**

- Une **zone de confiance** regroupe ce à quoi on accorde le même niveau de
  confiance — pas le même type de machine.
- La **kill chain** se lit sur la carte : chaque étape est une zone, un composant
  et une condition qui la rend possible.
- L'**exfiltration** se détecte aux frontières sortantes : c'est là que la
  surveillance rapporte le plus.
- Tout flux qui franchit une frontière porte **au moins un contrôle**, et l'on
  sait s'il empêche ou s'il détecte.

</details>

---

## V. Aller plus loin

> ⏭️ **Facultatif — pas exigé pour finir la journée.**

- **NIST CSF** : le cadre détaillé, ses niveaux de maturité et ses critères
  d'évaluation — pour transformer la photographie de la section IV en plan
  d'action.
- **Les modèles de maturité** en général : même logique que
  le NIST CSF.
- **L'IAM (Identity and Access Management, gestion des identités et des accès)** :
  la brique technique qui rend le moindre privilège applicable à grande échelle —
  provisionnement, revue des droits, suppression des comptes.

---

## Points clés

- **Defense in depth** : des couches **indépendantes** — réseau, identités,
  application, données, détection. Une couche qui tombe ne doit pas emporter les
  autres.
- **Zero Trust** : la confiance n'est plus déduite de la position réseau, elle
  est **prouvée** à chaque requête, pour une durée et un périmètre limités.
- **Moindre privilège** : chaque acteur dispose du strict nécessaire — comptes
  nominatifs, comptes de service taillés au plus juste, revue périodique des
  accès.
- La **détection** est une couche à part entière : sans elle, une défense
  contournée reste invisible.
- La **maturité** se situe avec un cadre de référence (NIST CSF) : cinq
  fonctions, un état par fonction.

---

## 🧠 Vérifiez vos acquis

*Formatif, jamais noté. Répondez sans relire le chapitre. Les réponses se déplient juste après le séparateur : ce qui compte est de repérer où vous vacillez, pas de faire 5 sur 5.*

**1.** Dans la defense in depth (défense en profondeur), quel est le point décisif ?

- A. Le nombre de couches, le plus élevé possible : plus l'empilement est épais, moins une faille isolée est grave
- B. Que les couches soient indépendantes : une défaillance isolée ne doit pas compromettre le tout
- C. Que la couche réseau absorbe le plus gros du budget, puisque c'est elle qui décide de ce qui est joignable
- D. Que chaque couche applique la même mesure de sécurité, pour que le niveau de protection soit homogène

**2.** Un service en appelle un autre sur le même réseau interne. Que prescrit Zero Trust ?

- A. Rien : à l'intérieur du réseau, la confiance est acquise et l'authentification ne ferait que ralentir les échanges
- B. Le service s'authentifie, avec un accès accordé pour une durée et un périmètre limités
- C. Le service doit passer par un pare-feu supplémentaire, placé entre les deux services pour filtrer leurs échanges
- D. Le service est bloqué jusqu'à une validation humaine, qui autorise l'appel une fois puis le laisse passer

**3.** Un job nocturne exporte les ventes vers un stockage d'objets. Comment le moindre privilège s'applique-t-il ?

- A. On lui donne un compte administrateur pour éviter les blocages en production, quitte à le retirer plus tard
- B. Le job lit le répertoire dont il a besoin, pas tout le stockage, sur un compte taillé au plus juste et révisé périodiquement
- C. On utilise un compte de service partagé avec l'équipe, plus simple à surveiller et à dépanner la nuit
- D. On lui accorde tous les droits le temps du projet, en revenant les restreindre une fois la livraison faite

**4.** Quelles sont les cinq fonctions du NIST CSF (Cybersecurity Framework) ?

- A. Identifier, protéger, détecter, répondre, restaurer
- B. Confidentialité, intégrité, disponibilité, traçabilité, conformité
- C. Prévenir, bloquer, corriger, auditer, sanctionner
- D. Reconnaissance, intrusion, exploitation, persistance, exfiltration

**5.** *Question ouverte (2-3 lignes).* Le chapitre parie que la couche qui manque le plus souvent dans les systèmes réels est la détection. Expliquez ce que change son absence, et citez deux mesures qui la constituent.

---

<details>
<summary>Vérifier ses réponses</summary>

### Réponses

**1. B.** L'empilement ne protège que si les mesures sont indépendantes.
**Pourquoi :** si la même erreur de configuration ouvre le réseau, l'application et les données, l'empilement n'existe que sur le papier — et une mesure unique, même excellente, devient le seul point de défaillance du système.

**2. B.** Chaque requête est vérifiée, quelle que soit son origine : un service qui en parle à un autre s'authentifie, même dans le même réseau.
**Pourquoi :** le cloud, le travail à distance et les appels de service à service ont rendu la frontière intérieur/extérieur illisible — un compte volé est « à l'intérieur » sans que personne ne l'ait décidé. La confiance n'est plus déduite de la position, elle est prouvée à chaque appel.

**3. B.** Chaque acteur — personne, application, tâche planifiée — ne dispose que du strict nécessaire, et rien de plus.
**Pourquoi :** le moindre privilège réduit à la fois la probabilité qu'un accès compromis mène loin et l'impact quand cela arrive ; un compte partagé rendrait toute action non attribuable, et un droit accordé pour un projet survit souvent au projet.

**4. A.** Identifier, protéger, détecter, répondre, restaurer : une échelle commune pour se situer, comparer et progresser.
**Pourquoi :** on obtient une photographie honnête plutôt qu'une liste de vœux, et le niveau visé dépend de la criticité du système — la logique de sécurité proportionnée.

**5.** Attendu : sans détection, une défense contournée reste invisible — l'attaque se déroule sans que personne ne réagisse ; deux mesures de cette couche : la journalisation centralisée et les alertes.
**Pourquoi :** la détection est une couche à part entière, dont le rôle est de voir et de réagir ; c'est elle qui manque le plus souvent dans les systèmes réels.

</details>

---

[← Chapitre précédent](04-paysage-cyber.md) · [Sommaire](Readme.md) · [Chapitre suivant →](06-cadre-juridique-intro.md)
