---
tags:
  - bases-de-données
  - bases-de-données/cours
---
# 07 — GROUP BY, DISTINCT et agrégation

> [[00 - Index|← Index]] | Précédent : [[06 - Fonctions SQL]] | Suivant : [[08 - DDL — Data Definition Language]]

---

## DISTINCT — Éliminer les doublons

> Affiche une **seule occurrence** de chaque valeur répétée dans une colonne.

```sql
-- Valeurs uniques d'un pays
SELECT DISTINCT Pays FROM tblClients

-- Combinaisons uniques de plusieurs colonnes
SELECT DISTINCT Continent, Pays FROM tblClients
```

💡 Utile pour savoir **de quels pays viennent les clients** sans répétition.

---

## GROUP BY — Regrouper et agréger

> Divise les résultats en **sous-ensembles de lignes** basés sur une ou plusieurs colonnes.

S'utilise **presque toujours** avec une fonction d'agrégation.

```sql
-- Regrouper par code de cours
SELECT CodeCours FROM tblEtudiants GROUP BY CodeCours

-- Regrouper sur plusieurs colonnes (session → puis cours)
SELECT Session, CodeCours FROM tblEtudiants GROUP BY Session, CodeCours
```

---

## Fonctions d'agrégation

Effectuent une **opération statistique** sur chaque groupe formé.

### COUNT — Compter les lignes

```sql
-- Nombre total d'employés
SELECT COUNT(*) AS NbEmploye FROM Employee

-- Nombre de clients par pays
SELECT Country, COUNT(CustomerID) FROM Customers GROUP BY Country
```

### SUM — Somme

```sql
-- Masse salariale totale
SELECT SUM(Salary) AS MasseSalariale FROM Employee

-- Masse salariale par département
SELECT Department, SUM(Salary) FROM Employee GROUP BY Department
```

### AVG — Moyenne

```sql
-- Salaire moyen global
SELECT AVG(Salary) AS SalaireMoyen FROM Employee

-- Salaire moyen par département
SELECT Department, AVG(Salary) FROM Employee GROUP BY Department
```

### MAX — Maximum

```sql
SELECT MAX(Salary) AS SalaireMax FROM Employee
SELECT Department, MAX(Salary) FROM Employee GROUP BY Department
```

### MIN — Minimum

```sql
SELECT MIN(Salary) AS SalaireMin FROM Employee
SELECT Department, MIN(Salary) FROM Employee GROUP BY Department
```

---

## ORDER BY vs GROUP BY — Comparaison

> Ces deux clauses sèment souvent la **confusion**.

| | `ORDER BY` | `GROUP BY` |
|---|---|---|
| **Rôle** | Trier l'affichage | Créer des sous-ensembles |
| **Résultat** | Mêmes lignes, réordonnées | Lignes fusionnées par groupe |
| **Utilisé avec** | Rien de spécial | Fonctions d'agrégation |
| **Tri** | A→Z ou Z→A, croissant/décroissant | Ne trie pas |

```sql
-- ORDER BY → trie les étudiants par nom
SELECT * FROM tblEtudiants ORDER BY NomEtudiant

-- GROUP BY → compte les étudiants par cours
SELECT CodeCours, COUNT(*) FROM tblEtudiants GROUP BY CodeCours
```

---

> Précédent : [[06 - Fonctions SQL]] | Suivant : [[08 - DDL — Data Definition Language]]
