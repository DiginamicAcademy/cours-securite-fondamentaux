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

*Formatif, jamais noté. Répondez sans relire le chapitre, puis cochez. Les réponses sont juste après le séparateur : ce qui compte est de repérer où vous vacillez, pas de faire 5 sur 5.*

**1.** Dans la defense in depth (défense en profondeur), quel est le point décisif ?

- A. Le nombre de couches, le plus élevé possible
- B. Que les couches soient indépendantes : une défaillance isolée ne doit pas compromettre le tout
- C. Que la couche réseau absorbe le plus gros du budget
- D. Que chaque couche applique la même mesure de sécurité

- [ ] ✓ je savais

**2.** Un service en appelle un autre sur le même réseau interne. Que prescrit Zero Trust ?

- A. Rien : à l'intérieur du réseau, la confiance est acquise
- B. Le service s'authentifie, avec un accès accordé pour une durée et un périmètre limités
- C. Le service doit passer par un pare-feu supplémentaire
- D. Le service est bloqué jusqu'à une validation humaine

- [ ] ✓ je savais

**3.** Un job nocturne exporte les ventes vers un stockage d'objets. Comment le moindre privilège s'applique-t-il ?

- A. On lui donne un compte administrateur pour éviter les blocages en production
- B. Le job lit le répertoire dont il a besoin, pas tout le stockage, sur un compte taillé au plus juste et révisé périodiquement
- C. On utilise un compte de service partagé avec l'équipe, plus simple à surveiller
- D. On lui accorde tous les droits le temps du projet, en y revenant plus tard

- [ ] ✓ je savais

**4.** Quelles sont les cinq fonctions du NIST CSF (Cybersecurity Framework) ?

- A. Identifier, protéger, détecter, répondre, restaurer
- B. Confidentialité, intégrité, disponibilité, traçabilité, conformité
- C. Prévenir, bloquer, corriger, auditer, sanctionner
- D. Reconnaissance, intrusion, exploitation, persistance, exfiltration

- [ ] ✓ je savais

**5.** *Question ouverte (2-3 lignes).* Le chapitre parie que la couche qui manque le plus souvent dans les systèmes réels est la détection. Expliquez ce que change son absence, et citez deux mesures qui la constituent.

- [ ] ✓ je savais

---

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

---

[← Chapitre précédent](04-paysage-cyber.md) · [Sommaire](Readme.md) · [Chapitre suivant →](06-cadre-juridique-intro.md)
