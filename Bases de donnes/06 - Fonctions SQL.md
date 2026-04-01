# 06 — Fonctions SQL

> [[00 - Index|← Index]] | Précédent : [[05 - Le langage SQL — SELECT]] | Suivant : [[07 - GROUP BY, DISTINCT et agrégation]]

> 📖 Documentation complète : https://learn.microsoft.com/fr-fr/sql/t-sql/functions/functions?view=sql-server-ver16

---

## Fonctions sur les chaînes de caractères

S'appliquent aux types `nchar`, `nvarchar`.

| Fonction | Description |
|---|---|
| `LEN(col)` | Nombre de caractères dans la colonne |
| `LEFT(col, n)` | Extrait n caractères à **gauche** |
| `RIGHT(col, n)` | Extrait n caractères à **droite** |
| `LOWER(col)` | Convertit en **minuscules** |
| `UPPER(col)` | Convertit en **majuscules** |
| `STR(col)` | Convertit un numérique en chaîne |
| `TRIM(col)` | Supprime les espaces **avant et après** |
| `LTRIM(col)` | Supprime les espaces **avant** |
| `RTRIM(col)` | Supprime les espaces **après** |
| `SUBSTRING(col, début, longueur)` | Extrait une sous-chaîne à partir de `début` |
| `CHARINDEX(char, col)` | Position d'un caractère dans la colonne |
| `CONCAT(ch1, ch2, ...)` | Met les chaînes bout à bout |
| `FORMAT(valeur, format, culture)` | Formate une valeur selon des paramètres |
| `REPLICATE(chaîne, n)` | Répète une chaîne n fois |

---

## Fonctions numériques

| Fonction | Description |
|---|---|
| `ROUND(valeur, précision)` | Arrondit à la précision indiquée |
| `SQRT(nombre)` | Racine carrée |
| `SQUARE(nombre)` | Carré du nombre |
| `AVG(col)` | Moyenne |
| `SUM(col)` | Somme totale |
| `MIN(col)` | Valeur minimale |
| `MAX(col)` | Valeur maximale |
| `COUNT(col)` | Nombre de lignes |

> `AVG`, `SUM`, `MIN`, `MAX`, `COUNT` sont aussi des **fonctions d'agrégation** → [[07 - GROUP BY, DISTINCT et agrégation]]

---

## Fonctions de date et heure

| Fonction | Description |
|---|---|
| `GETDATE()` | Date et heure du système |
| `YEAR(col)` | Extrait l'**année** |
| `MONTH(col)` | Extrait le **mois** (1–12) |
| `DAY(col)` | Extrait le **jour** |
| `ISDATE(col)` | Retourne 1 si c'est une date, 0 sinon |
| `DATEDIFF(intervalle, date_récente, date_ancienne)` | Différence entre deux dates |
| `DATEADD(intervalle, nombre, col)` | Ajoute une valeur à une date |
| `DATENAME(intervalle, col)` | Nom de la portion (ex: "February", "Monday") |
| `DATEPART(intervalle, col)` | Valeur numérique de la portion |

### Intervalles disponibles

| Intervalle | Alias |
|---|---|
| Année | `year`, `yyyy`, `yy` |
| Mois | `month`, `mm`, `m` |
| Jour | `day`, `dy`, `y` |
| Semaine | `week`, `ww`, `wk` |
| Heure | `hour`, `hh` |

```sql
-- Différence en années entre deux dates
DATEDIFF(year, DateNaissance, GETDATE())

-- Ajouter 30 jours à une date
DATEADD(day, 30, DateCommande)

-- Nom du mois courant
DATENAME(MONTH, GETDATE())

-- Nom du jour courant
DATENAME(WEEKDAY, GETDATE())
```

---

## Fonctions avancées (conversion et logique)

| Fonction | Description |
|---|---|
| `CAST(expression AS data_type)` | Conversion vers un autre type |
| `CONVERT(data_type, expression)` | Conversion vers un autre type |
| `ISNULL(expression)` | Teste si une expression est NULL |
| `ISNUMERIC(expression)` | Teste si une expression est numérique |
| `IIF(condition, vrai, faux)` | Instruction conditionnelle (si/sinon) |

```sql
-- Exemple IIF
SELECT IIF(Salary > 50000, 'Senior', 'Junior') AS Niveau FROM Employee

-- Exemple CAST
SELECT CAST(Prix AS nvarchar(10)) FROM tblProduits
```

---

> Précédent : [[05 - Le langage SQL — SELECT]] | Suivant : [[07 - GROUP BY, DISTINCT et agrégation]]
