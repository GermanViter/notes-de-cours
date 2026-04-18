---
tags:
  - bases-de-données
  - bases-de-données/cours
---
# 12 — Copie de tables (SELECT INTO)

> Précédent : [[11 - Les vues]] | Suivant : [[13 - ...]]

La commande `SELECT INTO` permet de **créer une nouvelle table** à partir des données ou de la structure d'une table existante. Elle est utile pour créer des sauvegardes, des tables de travail temporaires, ou des sous-ensembles de données.

> ⚠️ `SELECT INTO` crée la table **et** l'insère en une seule commande — la table cible ne doit pas déjà exister.

---

## Copie intégrale d'une table

Copie **toutes les colonnes et toutes les lignes** de la table source dans une nouvelle table.

```sql
SELECT *
INTO tblNouvelle
FROM tblSource;
```

**Exemple** :

```sql
SELECT *
INTO tblClientsBackup
FROM tblClients;
```

> Crée `tblClientsBackup` avec la même structure et les mêmes données que `tblClients`.

---

## Copie de la structure seulement (sans données)

Pour copier uniquement la structure d'une table (aucune ligne), on ajoute une clause `WHERE` avec une condition toujours fausse.

```sql
SELECT *
INTO tblNouvelle
FROM tblSource
WHERE 1 = 0;
```

> La condition `1 = 0` est toujours fausse — aucune ligne n'est copiée, mais les colonnes sont créées.

---

## Copie partielle — Sélection de colonnes

Pour ne copier que **certaines colonnes** de la table source :

```sql
SELECT col1, col2, col3
INTO tblNouvelle
FROM tblSource;
```

**Exemple** :

```sql
SELECT Nom, Prenom, Courriel
INTO tblContactsClients
FROM tblClients;
```

---

## Copie partielle — Sélection de lignes (avec WHERE)

Pour ne copier que **certaines lignes** selon une condition :

```sql
SELECT *
INTO tblNouvelle
FROM tblSource
WHERE condition;
```

**Exemple** :

```sql
SELECT *
INTO tblClientsQuebec
FROM tblClients
WHERE Province = 'QC';
```

---

## Copie partielle — Colonnes et lignes combinées

On peut combiner les deux pour copier un sous-ensemble précis :

```sql
SELECT col1, col2
INTO tblNouvelle
FROM tblSource
WHERE condition;
```

**Exemple** :

```sql
SELECT Nom, Prenom, Ville
INTO tblContactsQC
FROM tblClients
WHERE Province = 'QC';
```

---

## Colonnes calculées (attributs virtuels)

`SELECT INTO` peut inclure des colonnes calculées dans la nouvelle table :

```sql
SELECT Nom, Prenom, Prix * Quantite AS Total
INTO tblCommandesTotal
FROM tblCommandes;
```

> La colonne `Total` n'existe pas dans `tblCommandes` — elle est calculée à la volée et enregistrée dans la nouvelle table.

---

## ⚠️ Limites importantes

| Élément | Copié ? |
|---------|---------|
| Données | ✅ Oui (selon la requête) |
| Structure des colonnes | ✅ Oui |
| Clé primaire (`PRIMARY KEY`) | ❌ Non |
| Clé étrangère (`FOREIGN KEY`) | ❌ Non |
| Contraintes (`UNIQUE`, `CHECK`, `DEFAULT`) | ❌ Non |
| Index | ❌ Non |
| Propriété `IDENTITY` | ❌ Non |

> Après une copie, il faut recréer manuellement les contraintes avec `ALTER TABLE` si nécessaire. Voir [[08 - DDL — Data Definition Language#Contraintes]].

---

## Résumé

| Besoin | Syntaxe clé |
|--------|-------------|
| Copie intégrale | `SELECT * INTO ... FROM ...` |
| Structure seulement | `SELECT * INTO ... FROM ... WHERE 1 = 0` |
| Certaines colonnes | `SELECT col1, col2 INTO ...` |
| Certaines lignes | `SELECT * INTO ... WHERE condition` |
| Colonnes + lignes filtrées | `SELECT col1 INTO ... WHERE condition` |
