# Modèles de défense — la sécurité en couches

> Un château fort : des douves, un rempart, un donjon. Si une couche tombe, les
> autres tiennent encore. Aucune mesure prise isolément ne protège un système —
> c'est leur **empilement** qui le protège, et la façon dont on accorde (ou non)
> sa confiance.

**Durée de lecture :** 50 min · **Prérequis :** [Le paysage de la cybersécurité](04-paysage-cyber.md)

---

## Objectifs

À l'issue de ce chapitre, vous serez capable de :

- **Décomposer** la défense d'une application en couches indépendantes.
- **Appliquer** le principe Zero Trust (« ne jamais faire confiance, toujours vérifier ») à une architecture cloud ou API.
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
  locale (voir la [cartographie des zones de confiance](tp/04-cartographier-si.md)).

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

Côté base de données, cela se traduit directement dans les droits accordés :

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

## IV. Aller plus loin

*Ces approfondissements sont facultatifs : ils ne sont jamais exigés pour terminer
la journée.*

- **NIST (National Institute of Standards and Technology) CSF (Cybersecurity
  Framework)** : un cadre de référence qui organise la sécurité en fonctions —
  identifier, protéger, détecter, répondre, restaurer. Il sert moins à « être
  conforme » qu'à **situer sa maturité** : quelle fonction est assurée, laquelle
  ne l'est pas encore.
- **Les modèles de maturité** en général : ils donnent une échelle commune pour
  comparer deux organisations ou suivre sa propre progression dans le temps. Le
  niveau visé dépend de la criticité du système — on retrouve la logique de
  proportionnalité du [chapitre sur la sécurité proportionnée](02-securite-proportionnee.md).
- **L'IAM (Identity and Access Management, gestion des identités et des accès)**
 : la brique technique qui rend le moindre privilège applicable à grande
  échelle — provisionnement, revue des droits, suppression des comptes.

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
