# Corrigé — Identifier les obligations RGPD sur un cas type

> Corrigé de [l'exercice « Identifier les obligations RGPD sur un cas type »](../05-defi-rgpd.md).
> Pour un défi, pas de pas-à-pas : une **réponse de référence** et une **grille de
> vérification**. Confrontez votre travail aux points ci-dessous — d'autres
> formulations se défendent, à condition de s'appuyer sur les faits du contexte.

---

## Réponse de référence

### Les traitements et leurs finalités

| Traitement | Données | Finalité déclarable | Avis |
| --- | --- | --- | --- |
| Carte de fidélité | nom, prénom, e-mail, date de naissance, historique d'achats | gérer le programme : cumul d'avantages, suivi des points | recevable, sous réserve de la minimisation |
| Application mobile | géolocalisation, préférences de notifications | proposer les magasins et les offres pertinentes | recevable si l'accord est révocable et la donnée minimisée |
| Newsletter | adresse e-mail | informer des actualités et promotions | recevable si l'inscription est volontaire et révocable |

**Ce qui cloche dès cette lecture :** la date de naissance n'a de finalité que si
des avantages anniversaires sont réellement prévus ; sinon, c'est une collecte
sans raison — le premier réflexe est de la supprimer, pas de la « sécuriser ».

### Les manquements probables, principe par principe

- **Minimisation** — la date de naissance sans finalité, et une géolocalisation
  plus précise que ce que le service exige (l'historique complet des magasins
  visités n'est pas nécessaire pour proposer le magasin le plus proche).
- **Finalité** — les « notifications de promotions » ne sont pas reliées de façon
  explicite au programme de fidélité : une finalité doit être annoncée, pas
  déduite.
- **Durée de conservation** — « tant que le compte est actif » n'est pas une
  durée : aucun critère d'activité n'est défini, aucune purge n'est prévue. C'est
  le manquement le plus fréquent, et le plus facile à corriger.
- **Transparence** — rien n'indique que les personnes ont été informées des
  traitements, ni des éventuels destinataires des données.
- **Consentement** — la géolocalisation et la newsletter exigent un accord libre,
  révocable, et **prouvable** : la preuve du consentement est une donnée à
  conserver elle aussi.

### Traduction en contraintes concrètes

| Obligation | Contrainte technique ou organisationnelle |
| --- | --- |
| Minimisation | supprimer le champ de date de naissance s'il n'a pas de finalité ; borner la géolocalisation à la donnée utile |
| Durée de conservation | définir une durée par table, une tâche de purge planifiée et journalisée, un critère d'inactivité pour les comptes |
| Transparence | une mention au moment de la collecte, une politique de confidentialité par traitement |
| Consentement | case non pré-cochée, retrait en un clic, preuve du consentement stockée avec sa date et la version de la mention |
| Sécurité | chiffrement de la base, contrôle des accès, journalisation, et revue des copies de données hors du périmètre déclaré |
| Droits des personnes | possibilité de retrouver, corriger et effacer les données d'une personne sur demande |

### Le plan d'action de l'incident

- **Confinement et constat** — couper l'accès du serveur tiers, établir ce que
  contenait la copie, quand elle a été faite, et par qui elle était accessible.
- **Notification à la CNIL (Commission nationale de l'informatique et des
  libertés)** — dans les **72 heures** à partir du moment où l'organisation a
  **pris connaissance** de la violation, pas à partir de la fin de l'investigation.
- **Registre des violations** — documenter les faits, les données concernées, les
  mesures prises. Même quand la notification n'est pas due, l'écriture est
  obligatoire.
- **Information des personnes** — quand le risque pour leurs droits est élevé :
  ici, des données d'identité et d'achats fuitées exposent au hameçonnage ciblé,
  l'information doit être claire et dire quoi faire.
- **Revue de la cause** — une copie de base trouvée sur un serveur tiers révèle
  un flux ou un prestataire non encadré : c'est cette brèche-là qu'il faut
  refermer, pas seulement l'incident.

---

## Grille de vérification

Votre travail tient la route si vous cochez l'essentiel ci-dessous :

- [ ] Chaque traitement est relié à une finalité annoncée aux personnes concernées.
- [ ] La date de naissance et la géolocalisation sont traitées sous l'angle de la minimisation, pas seulement de la sécurité.
- [ ] La durée de conservation est critiquée comme un manquement à part entière — et non renvoyée à « plus tard ».
- [ ] Le plan d'action nomme la CNIL, le registre, et l'information des personnes.
- [ ] Le délai de 72 heures est rattaché à la **connaissance** de l'incident.
- [ ] Au moins une contrainte concrète est proposée par obligation retenue.

---

## Erreurs fréquentes

- **Traiter le cas comme un problème de sécurité uniquement** — chiffrer la base
  ne règle ni la minimisation, ni la durée de conservation, ni l'information des
  personnes.
- **Inventer des obligations hors contexte** — ce défi porte sur les faits
  donnés ; ajouter des hypothèses éloigne de l'exercice.
- **Oublier la preuve du consentement** — un accord qu'on ne peut pas prouver
  n'est pas un consentement recevable.
- **Confondre notification et information** — la CNIL reçoit la notification ;
  les personnes concernées reçoivent l'information. Les deux ne vont pas
  toujours ensemble, et les délais diffèrent.

---

## Points à retenir

- Les obligations RGPD se lisent **dans le projet**, pas dans un texte à part :
  chaque champ de formulaire, chaque durée de conservation, chaque destinataire
  est une décision.
- **Minimiser** est plus efficace que protéger : une donnée qu'on n'a pas
  collectée ne peut ni fuir, ni dépasser sa durée de conservation.
- En cas de violation : **confiner**, **notifier** la CNIL dans les 72 heures à
  partir de la connaissance, **documenter** toujours, **informer** les personnes
  si le risque est élevé.
- La cause d'un incident est souvent un **flux oublié** ou un **prestataire non
  encadré** : c'est là que le travail de fond se fait.
