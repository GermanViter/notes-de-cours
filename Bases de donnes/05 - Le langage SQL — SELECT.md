# 05 — Le langage SQL — SELECT (DQL)

> [[00 - Index|← Index]] | Précédent : [[04 - Environnement du cours (SQL Server)]] | Suivant : [[06 - Fonctions SQL]]

---

## Syntaxe générale SELECT

```sql
SELECT DISTINCT | ALL  *  |  Champ1, Champ2, Champ3, ...
FROM   table_name | table_name2
WHERE  condition
GROUP BY  Champ1, Champ2
ORDER BY  Champ1, Champ2
```

---

## SELECT — Choisir les colonnes

Affiche des données à partir d'une ou plusieurs tables.

```sql
-- Colonnes spécifiques
SELECT Col1, Col2, Col3 FROM tblEtudiants

-- Toutes les colonnes
SELECT * FROM tblEtudiants
```

---

## Alias (AS)

Renomme une colonne **pour l'affichage uniquement** (le nom réel ne change pas).

```sql
-- Avec AS
SELECT CityEmployee AS VilleEmploye FROM tblEmployes

-- Sans AS (espace suffit)
SELECT CityEmployee VilleEmploye FROM tblEmployes

-- Alias multi-mots → guillemets obligatoires
SELECT CityEmployee AS 'Ville Employe' FROM tblEmployes
```

---

## FROM — Source des données

```sql
-- Une table
SELECT Liste_Colonne FROM Table1

-- Plusieurs tables (requis pour les jointures)
SELECT Liste_Colonne FROM Table1, Table2
```

> Pour combiner des données de plusieurs tables → [[09 - Les jointures]]

---

## WHERE — Filtrer les résultats

> Permet d'indiquer les **conditions** que le résultat doit respecter.

Une condition retourne **VRAI (TRUE)** ou **FAUX (FALSE)**.

```sql
SELECT * FROM tblEtudiants WHERE CodeCours = '420-212'
```

### Opérateurs disponibles

| Opérateur | Description |
|---|---|
| `<`, `<=`, `>`, `>=`, `=`, `<>` | Comparaisons relationnelles |
| `AND`, `OR` | Opérateurs logiques |
| `BETWEEN val1 AND val2` | Entre deux bornes **incluses** |
| `IS NULL` / `IS NOT NULL` | Teste si la valeur est indéterminée |
| `IN (val1, val2, ...)` | Valeur dans une liste |
| `LIKE` avec `%` ou `_` | Recherche par motif |

#### Le `LIKE` et ses caractères génériques
- `%` → n'importe quelle suite de caractères
- `_` → exactement un caractère

```sql
-- Noms qui commencent par 'Mar'
WHERE NomEtudiant LIKE 'Mar%'

-- Noms de 5 caractères commençant par 'L'
WHERE NomEtudiant LIKE 'L____'
```

---

## ORDER BY — Trier les résultats

```sql
-- Tri ascendant (par défaut)
SELECT * FROM tblEtudiants ORDER BY NomEtudiant ASC

-- Tri descendant
SELECT * FROM tblEtudiants ORDER BY NomEtudiant DESC

-- Tri sur plusieurs colonnes (d'abord par nom, puis par prénom)
SELECT * FROM tblEtudiants ORDER BY NomEtudiant, PrenomEtudiant
```

> `ORDER BY` trie l'**affichage** uniquement. Pour créer des sous-groupes → [[07 - GROUP BY, DISTINCT et agrégation]]

---

## Exemple complet

```sql
SELECT NomEtudiant, PrenomEtudiant, CodeCours
FROM   tblEtudiants
WHERE  CodeCours = '420-212'
ORDER BY NomEtudiant, PrenomEtudiant
```

---

> Fonctions SQL → [[06 - Fonctions SQL]]
> Précédent : [[04 - Environnement du cours (SQL Server)]] | Suivant : [[06 - Fonctions SQL]]
