# 08 — DDL — Data Definition Language

> [[00 - Index|← Index]] | Précédent : [[07 - GROUP BY, DISTINCT et agrégation]] | Suivant : [[09 - Les jointures]]

> Les commandes DDL servent à **créer et modifier la structure** d'une base de données.

---

## Commandes principales

| Commande | Rôle |
|---|---|
| `CREATE` | Créer un objet (base, table…) |
| `USE` | Sélectionner une base de données |
| `DROP` | Supprimer un objet |
| `ALTER` | Modifier un objet existant |

---

## CREATE — Créer un objet

```sql
CREATE DATABASE nom_db

CREATE TABLE nom_table

-- Vérifie l'existence avant de créer
CREATE TABLE IF NOT EXISTS nom_table
```

---

## USE — Sélectionner une base de données

```sql
USE base_de_donnees
```

---

## SELECT — Afficher des informations système

```sql
-- Affiche le nom de la base de données active
SELECT DB_NAME()
```

---

## DROP — Supprimer un objet

S'applique à : `DATABASE`, `TABLE`, `VIEW`, `INDEX`

```sql
DROP TABLE NomTable

-- Recommandé : vérifie avant de supprimer
DROP TABLE IF EXISTS tblEtudiants
```

---

## ALTER — Modifier un objet existant

S'applique aux **tables** et aux **vues**.

Raisons courantes :
- Ajouter une colonne oubliée
- Supprimer une colonne inutile
- Rendre une colonne obligatoire

```sql
ALTER TABLE NomTable
Action (ADD | DROP | ALTER COLUMN)
```

---

## Création d'une table

### Option 1 — Supprimer avant de recréer

```sql
DROP TABLE IF EXISTS tblClient;
CREATE TABLE tblClients ( ... )
```

### Option 2 — Créer seulement si inexistant

```sql
CREATE TABLE IF NOT EXISTS tbl_test (
    COLLID   INT          PRIMARY KEY IDENTITY(1,1),
    Column1  NVARCHAR(20) NOT NULL,
    Column2  INT          NOT NULL,
    Column3  DATE
)
```

### Afficher la structure d'une table

```sql
EXEC sp_help tblCollection
```

---

## Types de colonnes

| Type | Description |
|---|---|
| `NVARCHAR(n)` | Chaîne de caractères (max n caractères) |
| `DATE` | Date |
| `TIME` | Heure |
| `FLOAT` | Nombre réel |
| `DECIMAL(n, m)` | Nombre réel — **n** = chiffres total, **m** = décimales |
| `INT` | Entier |
| `BIT` | Booléen → `0` ou `1` |
| `MONEY` | Valeur monétaire |

> Voir aussi le tableau complet dans [[03 - Les objets d'une base de données#Types de données]]

---

## Propriétés de colonnes

| Propriété | Description |
|---|---|
| `IDENTITY(n, m)` | Auto-incrément — **n** = départ, **m** = incrément |
| `DEFAULT` | Valeur par défaut |
| `NOT NULL` | Saisie obligatoire |
| `FOREIGN KEY` | Clé étrangère |

---

## Opérations ALTER TABLE

### Ajouter une colonne

```sql
ALTER TABLE tblNom
ADD Actif BIT NOT NULL
```

### Rendre une colonne obligatoire (NOT NULL)

```sql
ALTER TABLE tblEtudiants
ALTER COLUMN courriel NVARCHAR(100) NOT NULL
```

### Modifier la longueur d'une colonne

```sql
ALTER TABLE tblEtudiant
ALTER COLUMN Courriel NVARCHAR(100) NULL
```

### Supprimer une colonne

> ⚠️ Impossible si la colonne est dans une contrainte ou fait partie d'une clé primaire.

```sql
ALTER TABLE tblEtudiant
DROP COLUMN IF EXISTS Actif
```

### Renommer une colonne

```sql
EXEC sp_rename 'NomTable.ancienne_colonne', 'nouvelle_colonne', 'COLUMN'
```

---

## Contraintes

### Clé primaire

```sql
-- Ajouter
ALTER TABLE tblTest
ADD CONSTRAINT PK_tblTest PRIMARY KEY (NoSerie)

-- Supprimer
ALTER TABLE tblTest
DROP CONSTRAINT PK_tblTest
```

### Clé étrangère

```sql
-- Ajouter
ALTER TABLE tblNotes
ADD CONSTRAINT FK_tblNotes
FOREIGN KEY (NoEtudiant)
REFERENCES tblEtudiants(NoEtudiant)

-- Supprimer
ALTER TABLE tblNotes
DROP CONSTRAINT FK_tblNotes
```

> La clé étrangère est utilisée dans les [[09 - Les jointures|jointures]].

### Contrainte UNIQUE

```sql
ALTER TABLE NomTable
ADD CONSTRAINT nom_contrainte UNIQUE (colonne)
```

### Contrainte DEFAULT

```sql
ALTER TABLE NomTable
ADD CONSTRAINT nom_contrainte
DEFAULT valeur FOR nom_colonne
```

### Contrainte CHECK

```sql
ALTER TABLE tblEtudiants
ADD CONSTRAINT CK_Notes
    CHECK (Note BETWEEN 0 AND 100),
ADD CONSTRAINT CK_DateDeNaissance
    CHECK (DateDeNaissance < GETDATE())
```

### Supprimer une contrainte

```sql
ALTER TABLE NomTable
DROP CONSTRAINT nom_contrainte
```

---

> Précédent : [[07 - GROUP BY, DISTINCT et agrégation]] | Suivant : [[09 - Les jointures]]
