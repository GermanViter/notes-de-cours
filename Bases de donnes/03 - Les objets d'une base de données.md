# 03 — Les objets d'une base de données

> [[00 - Index|← Index]] | Précédent : [[02 - Terminologie SGBDR]] | Suivant : [[04 - Environnement du cours (SQL Server)]]

---

## Les objets principaux

- **Tables** ⭐ — objet principal, stocke les données
- Vues
- Procédures stockées
- Objets systèmes

---

## Les tables

> Créer une table = définir sa **structure**.

La bonne définition d'une table est **cruciale**.

### Étapes de création d'une table

#### 1. Nom de la table
Doit être **significatif**.
```
tblEtudiants, tblProfesseurs, tblVoitures, tblAmis
```

#### 2. Nom des colonnes
Doit être **représentatif**.
```
tblEtudiants(NoEtudiant, NomEtudiant, PrenomEtudiant, AdresseEtudiant)
tblProfesseurs(NoProfesseur, NomProfesseur, PrenomProfesseur, DepartementProfesseur)
```

#### 3. Type des colonnes
→ Voir [[#Types de données]]

#### 4. Taille des colonnes
L'espace réservé dans la colonne pour recevoir les données.
```
Exemple : NomEtudiant — 40 caractères
```

---

## Types de données

### Numériques

| Type       | Plage                          |
| ---------- | ------------------------------ |
| `tinyint`  | 0 à 255                        |
| `smallint` | -32 766 à 32 767               |
| `int`      | -2 147 483 648 à 2 147 483 647 |
| `bigint`   | ± 9 223 372 036 854 775 808    |
| `float`    | Nombre décimal (ex : 1234.50)  |

### Chaînes de caractères

Stocke tous les caractères alphanumériques : A→Z, a→z, 0-9, espace.

| Type          | Description                                     |
| ------------- | ----------------------------------------------- |
| `nchar(n)`    | Chaîne de **longueur fixe** de n caractères     |
| `nvarchar(n)` | Chaîne de **longueur variable** de n caractères |

### Date et heure

| Type       | Description                                |
| ---------- | ------------------------------------------ |
| `date`     | Date entre 01-01-01 et 12-31-9999          |
| `time(n)`  | Heure format 24h — n = précision centièmes |
| `datetime` | Date + heure dans la même colonne          |

Exemple :
```
time(2) → 11:54:04:20
time(3) → 11:54:04:205
datetime → 01-01-01 11:15:05:245
```

### Complexes

| Type               | Description                                   |
| ------------------ | --------------------------------------------- |
| `uniqueidentifier` | Valeur unique séquentielle automatique (GUID) |

---

## Propriétés des colonnes

### Clé primaire

> Colonne qui **identifie une ligne de façon unique**.

Règles strictes :
- ✅ Valeur **unique** — jamais deux fois la même
- ✅ Une table ne peut avoir qu'**une seule** clé primaire
- ✅ **Indexée** automatiquement (valeurs triées)
- ✅ **Non vide** — doit toujours contenir une valeur (`NOT NULL`)

```
Exemple : IDEtudiant dans tblEtudiant
```

### Clé étrangère

> Colonne d'une table qui est **clé primaire dans une autre table**.

```
Exemple : IDEtudiant dans tblCours
```

Crée le **lien** entre deux tables → utilisée dans les [[09 - Les jointures|jointures]].

### Autres propriétés

| Propriété | Description |
|---|---|
| `NOT NULL` | La colonne doit obligatoirement contenir une valeur |
| Auto-incrémentée | Valeurs qui augmentent automatiquement (1, 2, 3…) |
| Valeur par défaut | La colonne se remplit automatiquement |
| Index | Contenu trié automatiquement et en permanence |

---

## Formalisme de notation

```
NomRelation(Clé, attribut_1, attribut_2, attribut_3)
```

La clé primaire est **soulignée** dans ce formalisme.

---

> Pour créer des tables en SQL → [[08 - DDL — Data Definition Language]]

> Précédent : [[02 - Terminologie SGBDR]] | Suivant : [[04 - Environnement du cours (SQL Server)]]
