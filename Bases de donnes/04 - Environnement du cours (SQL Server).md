---
tags:
  - bases-de-données
  - bases-de-données/cours
---
# 04 — Environnement du cours (SQL Server)

> [[00 - Index|← Index]] | Précédent : [[03 - Les objets d'une base de données]] | Suivant : [[05 - Le langage SQL — SELECT]]

---

## Outils utilisés dans le cours

| Outil | Rôle |
|---|---|
| **SQL Server Express LocalDB** | Moteur de base de données |
| **SQL Server Management Studio (SSMS)** | Client SQL (interface graphique) |

---

## Pourquoi utiliser un client SQL ?

- Interface graphique au lieu de la ligne de commande
- Richesse fonctionnelle
- Aide à la saisie des commandes
- Éditeur de code SQL + fenêtre de résultats

---

## Connexion à SQL Server

Paramètres de connexion dans SSMS :

| Champ | Valeur |
|---|---|
| Type de serveur | Moteur de base de données |
| Nom du serveur | `(LocalDB)\420-212` |
| Authentification | Authentification Windows |

---

## Catégories du langage SQL

→ Détails dans [[05 - Le langage SQL — SELECT]] et [[08 - DDL — Data Definition Language]]

| Catégorie | Sigle | Commandes |
|---|---|---|
| Requête de données | **DQL** | `SELECT` |
| Définition de données | **DDL** | `CREATE`, `ALTER`, `RENAME` |
| Manipulation de données | **DML** | `INSERT`, `UPDATE`, `DELETE` |

---

> Précédent : [[03 - Les objets d'une base de données]] | Suivant : [[05 - Le langage SQL — SELECT]]
