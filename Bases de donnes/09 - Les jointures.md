---
tags:
  - Cl
  - bases-de-données
  - bases-de-données/cours
---
# 09 — Les jointures

> [[00 - Index|← Index]] | Précédent : [[08 - DDL — Data Definition Language]]

---

## Qu'est-ce qu'une jointure ?

> Opération SQL qui permet d'**extraire des données provenant de plusieurs tables** de façon cohérente.

La jointure crée un **« pont »** entre plusieurs tables en s'appuyant sur :
- Une **clé primaire (PK)** dans la table principale
- Une **clé étrangère (FK)** dans la table secondaire

> Voir [[03 - Les objets d'une base de données#Clé primaire|Clé primaire]] et [[03 - Les objets d'une base de données#Clé étrangère|Clé étrangère]]

---

## Pourquoi les jointures ?

**Pour éviter la redondance**
- Les données doivent être stockées à **un endroit unique**
- On segmente les données dans des tables séparées…

**Pour recomposer les données**
- …puis on les recompose à l'aide de jointures, de façon cohérente

---

## Quand utiliser les jointures ?

Lorsqu'on veut présenter des données de **plusieurs tables** liées logiquement :

- Employé ↔ Département
- Étudiant ↔ Notes
- Client ↔ Commandes
- Abonné de bibliothèque ↔ Livres empruntés
- Fournisseur ↔ Produits

---

## Comment utiliser les jointures

### Syntaxe avec WHERE (méthode classique)

```sql
SELECT
    A.colonne1,
    A.colonne2,
    B.colonne1
FROM
    table1 A, table2 B
WHERE
    A.colonne1 = B.colonne1
```

### Syntaxe avec INNER JOIN (méthode moderne — recommandée)

```sql
SELECT
    A.colonne1,
    A.colonne2,
    B.colonne1
FROM
    table1 A
    INNER JOIN table2 B ON A.colonne1 = B.colonne1
```

> Les alias de table (`A`, `B`) permettent de **qualifier** les colonnes quand elles existent dans plusieurs tables.

---

## Démarche systématique

Pour construire une requête avec jointure :

1. **Identifier la table principale (maître)** → celle qui contient la **PK**
2. **Identifier la table secondaire (détail)** → celle qui contient la **FK**
3. **Identifier la clé primaire** dans la table maître
4. **Identifier la clé étrangère** dans la table détail
5. **Établir le lien** : `maître.PK = détail.FK`

> Une relation maître (PK) → détail (FK) est une relation de **1 à plusieurs**.

---

## Exemple complet

Tables :
- `tblClients(IDClient, NomClient, ...)`
- `tblCommandes(IDCommande, IDClient, DateCommande, ...)`

`IDClient` est la PK dans `tblClients` et la FK dans `tblCommandes`.

```sql
SELECT
    C.NomClient,
    O.IDCommande,
    O.DateCommande
FROM
    tblClients C
    INNER JOIN tblCommandes O ON C.IDClient = O.IDClient
ORDER BY
    C.NomClient
```

---

> Précédent : [[08 - DDL — Data Definition Language]] | [[00 - Index|← Retour à l'index]]
