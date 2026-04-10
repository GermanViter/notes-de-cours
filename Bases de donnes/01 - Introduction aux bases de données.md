---
tags:
  - bases-de-données
  - bases-de-données/cours
---
# 01 — Introduction aux bases de données

> [[00 - Index|← Index]] | Suivant : [[02 - Terminologie SGBDR]]

---

## Définitions de base

### Système informatique
Ensemble des équipements **matériels et logiciels** qui fonctionnent de manière coordonnée pour accomplir un traitement informatique.

### Système d'information
Ensemble des ressources informatiques (matérielles et logicielles) **et humaines** (informaticiens et gestionnaires) destinées à produire de l'information. Il permet de **collecter, mémoriser, traiter et transmettre** les informations.

### Information
Ensemble de données qui, après avoir subi un traitement informatique, produit un **renseignement utile à la prise de décision**.

---

## Exemples concrets d'utilisation de la donnée

| Entreprise     | Découverte                                           | Action                                             |
| -------------- | ---------------------------------------------------- | -------------------------------------------------- |
| **Walmart**    | Les hommes achètent bière + couches le vendredi soir | Rapprocher les produits en rayon                   |
| **Target**     | Habitudes d'achat prédisant une grossesse            | Envoi de coupons ciblés                            |
| **Netflix**    | Genres/acteurs populaires par segment                | Production de *House of Cards*, algorithme de reco |
| **Starbucks**  | Trafic, revenus, concurrence locale                  | Prédire les emplacements rentables                 |
| **McDonald's** | Préférences alimentaires régionales                  | McBaguette (France), McSpicy (Inde), McArabia (MO) |
| **Amazon**     | Prix concurrents + demande en temps réel             | Tarification dynamique plusieurs fois/jour         |

---

## Définition d'une base de données

> Ensemble structuré de données mémorisé sur un **support permanent**, utilisé par des personnes ou des programmes, dont l'organisation est régie par un **modèle**.

Une base de données représente la **partie centrale du système d'information**.

### Avant les BD informatisées
Des fiches papier (cartons).

### Banques de données
Ensemble d'informations sur un **domaine précis** (médecine, physique, économie…), le plus détaillé possible.

### Entrepôts de données
Bases de données **historisées** permettant l'informatique décisionnelle. Répondent aux questions :
- Qu'est-ce qui s'est passé ?
- Qu'est-ce qui se passe ?
- Qu'est-ce qui va se passer ?

### Caractéristiques d'une BD
- Organisation et description des données
- Stockage des données
- Partage des données
- Sécurité et confidentialité
- Performance

---

## Les SGBD (Systèmes de Gestion de Bases de Données)

Ensemble coordonné de logiciels qui permettent de **décrire, mémoriser, manipuler, interroger** les données, tout en assurant sécurité et confidentialité dans un environnement multi-utilisateur.

### Types de SGBD

| Type | Description |
|---|---|
| Hiérarchiques | Anciens modèles en arbre |
| Réseaux | Anciens modèles en graphe |
| **Relationnels** ⭐ | Modèle en tables liées (standard actuel) |
| Déductifs | Basés sur la logique |
| Objets | Données sous forme d'objets |
| NoSQL | Pour données non structurées ou massives |

### Caractéristiques d'un bon SGBD

- **Bonne représentation** : image fidèle de la réalité
- **Non redondance** : une info = un seul endroit
- **Indépendance** du programme : les données ne sont pas créées pour les programmes
- **Sécurité et confidentialité** : accès physique + accès autorisé seulement
- **Performance** : accès rapide
- **Résistance aux pannes** : robustesse + mécanisme de secours
- **Accès, manipulation et partage** de données

---

## Les SGBDR (relationnels)

Apparus en **1980**. Construit autour du **modèle relationnel** : les données sont en relation les unes avec les autres.

Exemples de relations :
- Les transactions bancaires d'une personne
- Les commandes d'un client
- Les notes d'un étudiant

### Le modèle relationnel
Diagramme représentant les **tables** et les **liens** entre elles (via clés primaires et étrangères).

### Quelques SGBDR connus

| SGBDR | Éditeur |
|---|---|
| Oracle | Oracle |
| DB2 | IBM |
| **SQL Server** ⭐ | Microsoft |
| MySQL / MariaDB | Open source |
| PostgreSQL | Open source |

### Métiers liés aux SGBDR

| Rôle | Description |
|---|---|
| DBA | Gestion, sécurité, optimisation des BD |
| Analyste de données | Examiner et visualiser les données |
| Ingénieur de données | Pipelines, infrastructures de données |
| Scientifique de données | ML, modèles prédictifs |
| Architecte de données | Structure globale des systèmes |
| BI Analyst | Rapports et tableaux de bord |
| Développeur BD | Scripts SQL, structures de données |
| Spécialiste gouvernance | Politiques, intégrité, conformité |
| ML Engineer | Déploiement de modèles ML |
| Data Quality Manager | Précision et cohérence des données |

---

> Suivant : [[02 - Terminologie SGBDR]]
