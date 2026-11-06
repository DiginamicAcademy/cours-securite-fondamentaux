[← Chapitre précédent](05-modeles-de-securite.md) · [Sommaire](Readme.md) · [Chapitre suivant →](A-Glossaire-et-ressources.md)

# Cadre juridique introductif — le RGPD (Règlement général sur la protection des données) comme contrainte technique

> Une boutique en ligne conserve des adresses e-mail « au cas où », depuis des
> années, sans savoir pourquoi — et reçoit un courrier de la CNIL (Commission
> nationale de l'informatique et des libertés). La loi n'est pas un frein à
> contourner : c'est un cadre qui se traduit en **contraintes techniques**, aussi
> concrètes qu'une règle de pare-feu.

**Durée :** ≈ 25 min (lecture ≈ 12 min + atelier 8 min + réflexion) · **Prérequis :** [Modèles de défense](05-modeles-de-securite.md)

---

## Objectifs

À l'issue de ce chapitre, vous serez capable de :

- **Identifier** les principes du RGPD applicables à une application.
- **Repérer** les données personnelles dans un schéma de base de données.
- **Décrire** la procédure à suivre en cas de violation de données personnelles.
- **Relier** chaque obligation légale à une contrainte technique ou organisationnelle.

---

## I. Le RGPD en 5 minutes

Le **RGPD** est le texte européen qui encadre le traitement des données
personnelles. Il s'applique dès qu'on traite des données relatives à des
personnes identifiées ou identifiables — quel que soit le pays où se trouve le
serveur.

### Qu'est-ce qu'une donnée personnelle ?

Tout ce qui identifie une personne, directement ou indirectement : nom, adresse
e-mail, numéro de téléphone, mais aussi identifiant de session, adresse IP
(Internet Protocol, le protocole d'adressage d'Internet), historique d'achats,
géolocalisation. Un identifiant technique « anonyme » qui permet de retrouver
une personne est une donnée personnelle.

### Les principes qui dérangent (et qui structurent tout)

| Principe | Ce qu'il impose | Traduction technique |
| --- | --- | --- |
| **Finalité** | collecter pour une raison précise, annoncée | un champ de formulaire a une raison d'être documentée |
| **Minimisation** | ne collecter que le strict nécessaire | supprimer les champs « on ne sait jamais » |
| **Durée de conservation** | garder le temps utile, puis effacer | purge planifiée, durée par table |
| **Exactitude** | des données à jour | mise à jour et rectification possibles |
| **Sécurité** | protéger les données | chiffrement, contrôle des accès, journalisation |
| **Transparence** | informer les personnes | mentions lisibles, politique de confidentialité |

Deux rôles à distinguer, parce qu'ils n'engagent pas les mêmes obligations :

- le **responsable de traitement** décide des finalités — l'entreprise qui vend ;
- le **sous-traitant** traite pour son compte — l'hébergeur, le prestataire
  d'envoi de courriels, l'éditeur du logiciel de gestion.

Pour un développeur, la conséquence est directe : choisir un prestataire, c'est
encadrer un sous-traitant — contrat, instructions, sécurité.

### Les droits des personnes

Accès, rectification, effacement, portabilité, opposition. Concrètement, une
application qui ne sait pas **retrouver** les données d'une personne, les
**corriger** ou les **supprimer** sur demande ne respecte pas le texte — quelles
que soient ses belles intentions.

> [!TIP]
> Posez-vous la question dès la conception du schéma de base : « si une personne
> demande l'effacement de ses données, sais-je où elles sont toutes ? » Les
> copies, exports et sauvegardes comptent — c'est là que la réponse se complique.

---

## II. Que faire en cas de violation ?

Une **violation de données personnelles**, c'est un accès, une perte, une
altération ou une divulgation non autorisée. Un rançongiciel qui copie une base
clients en est une ; un export oublié sur un serveur public aussi.

La procédure tient en trois gestes :

1. **Notifier** l'autorité de contrôle — la **CNIL** en France — dans les **72
   heures** après en avoir pris connaissance, sauf si la violation ne fait pas
   courir de risque aux personnes.
2. **Documenter** l'incident : ce qui s'est passé, quelles données sont
   concernées, quelles mesures ont été prises. Même quand on ne notifie pas, on
   écrit.
3. **Prévenir les personnes concernées** quand la violation fait courir un risque
   élevé pour leurs droits — de façon claire, sans jargon.

Le point qui surprend toujours : le délai court à partir de la **connaissance**
de l'incident, pas de sa découverte technique complète. Une organisation qui
met trois semaines à comprendre ce qui s'est passé, puis notifie, est hors délai.

> 🧪 **Atelier rapide (8 min)**
>
> Voici les colonnes de la table `commandes` d'une boutique en ligne :
> `id`, `client_nom`, `client_email`, `adresse_livraison`, `telephone`,
> `date_commande`, `montant_total`, `code_promo_utilise`, `ip_client`.
>
> Repérez quelles colonnes sont des **données personnelles**, lesquelles
> méritent une attention particulière, et lesquelles n'en sont pas. Justifiez
> chaque choix en une ligne — et dites ce que vous feriez des colonnes
> superflues.

---

## III. Les transversales

Le RGPD n'est pas le seul cadre à croiser. Deux autres préoccupations
reviennent dans les cahiers des charges, et se traitent au même moment : à la
conception.

### L'accessibilité PSH

**PSH (Personnes en Situation de Handicap)** — l'accessibilité rend un service
utilisable par tous : contrastes suffisants, navigation au clavier, textes
alternatifs pour les images, formulaires explicités. Les référentiels de
référence sont le **RGAA (Référentiel général d'amélioration de l'accessibilité)**
en France, et les **WCAG (Web Content Accessibility Guidelines)** au niveau
international.

Elle est **obligatoire** pour certains services (secteur public, grandes
entreprises) et **toujours utile** ailleurs : un service accessible est plus
lisible pour tout le monde, y compris sur un écran petit ou dans une pièce
éclairée.

### L'éco-conception

Alléger les pages, réduire le poids des transferts, limiter les traitements
inutiles : l'éco-conception numérique réduit la consommation d'énergie — et
améliore en général la performance et l'accessibilité. Elle entre parfois dans
les obligations d'achat public, et toujours dans la durée de vie du service.

> [!WARNING]
> Une transversale plaquée après coup coûte dix fois plus cher qu'une
> transversale intégrée à la conception. Accessibilité, éco-conception et
> protection des données se décident au moment du schéma de base et des maquettes
> — pas au moment de la recette.

---

## IV. Aller plus loin

> ⏭️ **Facultatif — pas exigé pour finir la journée.**

- **Le rôle de la CNIL** : elle contrôle, elle sanctionne, mais elle accompagne
  aussi — ses fiches pratiques et ses référentiels détaillent les bonnes
  configurations pour des cas courants (vidéosurveillance, cookies, ressources
  humaines).
- **Les amendes** : le texte prévoit des sanctions à la hauteur du manquement —
  jusqu'à 20 millions d'euros ou une part du chiffre d'affaires mondial. Les
  décisions publiées montrent surtout que les manquements reprochés sont
  ordinaires : durée de conservation non définie, information des personnes
  absente, sécurité insuffisante.
- **Le DPO (délégué à la protection des données)** : la personne désignée pour
  suivre ces obligations au quotidien. Dans une petite structure, le rôle existe
  quand même — il est simplement porté par une personne déjà en poste.

---

## Points clés

- Le **RGPD** s'applique dès qu'on traite des données personnelles : c'est une
  contrainte technique, pas un sujet « juridique à part ».
- Les principes à traduire en code : **finalité, minimisation, durée de
  conservation, exactitude, sécurité, transparence**.
- En cas de violation : **notifier** la CNIL dans les **72 heures**, **documenter**
  toujours, **prévenir** les personnes quand le risque est élevé.
- **Accessibilité PSH** et **éco-conception** se décident à la conception — au
  moment du schéma de base et des maquettes.

---

[← Chapitre précédent](05-modeles-de-securite.md) · [Sommaire](Readme.md) · [Chapitre suivant →](A-Glossaire-et-ressources.md)
