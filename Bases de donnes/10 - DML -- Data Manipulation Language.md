# 10 — DML — Data Manipulation Language

> Précédent : [[09 - ...]] | Suivant : [[11 - ...]]

Le **DML** (Data Manipulation Language) regroupe les commandes SQL qui permettent de **manipuler les données** contenues dans les tables d'une base de données.

| Commande | Description |
|----------|-------------|
| `INSERT` | Insérer de nouvelles lignes dans une table |
| `UPDATE` | Mettre à jour des données existantes |
| `DELETE` | Supprimer des lignes d'une table |

---

## INSERT INTO — Insertion de données

### Syntaxe de base

Insertion ligne par ligne (une commande par ligne) :

```sql
INSERT INTO tblEx VALUES (val1, val2, val3);
INSERT INTO tblEx VALUES (val1, val2, val3);
INSERT INTO tblEx VALUES (val1, val2, val3);
```

Insertion de plusieurs lignes en une seule commande :

```sql
INSERT INTO tblEx
VALUES
    (val1, val2, val3),
    (val1, val2, val3),
    (val1, val2, val3);
```

### Insertion avec énumération des colonnes

Il est recommandé de spécifier explicitement les colonnes ciblées :

```sql
INSERT INTO tblEx (col1, col2, col3)
VALUES (valeur1, valeur2, valeur3);
```

### ⚠️ Points importants

- **Colonnes obligatoires** : toute colonne `NOT NULL` sans valeur par défaut doit recevoir une valeur.
- **Colonnes `IDENTITY` et `DEFAULT`** : ne pas les inclure dans la liste — leur valeur est gérée automatiquement par le moteur SQL.
- **Valeurs inconnues ou absentes** : utiliser `NULL` pour les colonnes qui l'acceptent.

---

## UPDATE — Mise à jour de données

### Syntaxe de base

> ⚠️ Sans clause `WHERE`, **toutes les lignes** de la table sont modifiées !

```sql
UPDATE tblEx
SET col = valeur;
```

**Exemple** — Remplace la valeur de `Ville` par `'Montréal'` pour **toutes les lignes** de la table :

```sql
UPDATE tblTest
SET Ville = 'Montréal';
```

### UPDATE conditionnel (avec WHERE)

La clause `WHERE` permet de cibler uniquement les lignes à modifier :

```sql
UPDATE tblEx
SET col = valeur
WHERE condition;
```

**Exemple** :

```sql
UPDATE tblTest
SET Ville = 'Montréal'
WHERE Province = 'QC';
```

---

## DELETE — Suppression de données

### Syntaxe de base

> ⚠️ Sans clause `WHERE`, **toutes les lignes** de la table sont supprimées !

```sql
DELETE FROM tblEx;
```

### DELETE conditionnel (avec WHERE)

```sql
DELETE FROM tblEx
WHERE condition;
```

**Exemple** :

```sql
DELETE FROM tblTest
WHERE Ville = 'Québec';
```

---

## Résumé — Tableau comparatif

| Commande | Modifie les données | Utilise WHERE | Risque sans WHERE            |
| -------- | ------------------- | ------------- | ---------------------------- |
| `INSERT` | Ajoute des lignes   | Non           | —                            |
| `UPDATE` | Modifie des valeurs | Oui           | Toutes les lignes modifiées  |
| `DELETE` | Supprime des lignes | Oui           | Toutes les lignes supprimées |
