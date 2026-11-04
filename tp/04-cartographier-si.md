# Exercice — Cartographier les zones de confiance d'une plateforme data

> **Nature :** élément intégrable dans l'exercice d'intégration de fin de journée ([INTEGRATION-J1.md](INTEGRATION-J1.md)) — utilisable aussi en TD autonome · **Durée :** 30 min · **Notion :** cartographier les zones de confiance, les flux qui les traversent et les points de contrôle
> 🔵 **Avancé** · **Durée :** 30 min · **Lien :** chapitres [Le paysage de la cybersécurité](../04-paysage-cyber.md) et [Modèles de défense](../05-modeles-de-securite.md)
> **Objectif :** cartographier les zones de confiance d'une plateforme data, les
> flux qui les traversent, et y placer les étapes d'une attaque.

---

## Contexte

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

---

## Consignes

### Partie 1 — Lister les composants et les flux

Pour chaque composant, indiquez ce qu'il **reçoit**, ce qu'il **envoie**, et
**à qui**. Formalisez ensuite la liste des flux sous la forme
`source → destination` avec, pour chacun, le **contenu** transporté et le
**sens** (lecture, écriture, les deux).

### Partie 2 — Délimiter les zones de confiance

Regroupez les composants en **zones de confiance** — l'équipe en retient
généralement quatre sur ce type de plateforme. Pour chaque zone : un nom, ce
qu'elle contient, et la **justification de chaque frontière** : pourquoi ce qui
est d'un côté n'a pas besoin d'être de l'autre.

### Partie 3 — Placer les étapes de la kill chain

Les cinq étapes de la kill chain (reconnaissance, intrusion, exploitation,
persistance, exfiltration) se déroulent quelque part sur votre carte. Pour
chacune : la **zone** où elle se passe le plus probablement, le **composant**
visé, et **ce qui la rend possible** ici.

### Partie 4 — Points de contrôle

Pour chaque flux qui franchit une frontière, nommez le **contrôle** qui devrait
exister (authentification, chiffrement, journalisation, filtrage…). Distinguez
les contrôles qui **empêchent** de ceux qui **détectent**.

---

## ✅ Auto-évaluation

Avant de passer au corrigé, vérifiez que :

- [ ] Ma liste de flux indique source, destination, contenu et sens pour chaque flux.
- [ ] Mes zones sont nommées et peuplées, et chaque frontière est justifiée.
- [ ] Les cinq étapes de la kill chain sont placées sur la carte, avec le composant visé.
- [ ] Chaque flux qui franchit une frontière a au moins un contrôle associé.
- [ ] J'ai distingué les contrôles qui empêchent de ceux qui détectent.

---

## Pour aller plus loin

*Facultatif.* Un analyste doit accéder à la base depuis l'extérieur du réseau
interne. Redessinez la carte pour intégrer ce flux : qu'est-ce qui change dans
vos zones et dans vos contrôles ?
