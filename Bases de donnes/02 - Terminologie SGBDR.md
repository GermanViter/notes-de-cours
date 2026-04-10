---
tags:
  - bases-de-données
  - bases-de-données/cours
---
# 02 — Terminologie SGBDR

> [[00 - Index|← Index]] | Précédent : [[01 - Introduction aux bases de données]] | Suivant : [[03 - Les objets d'une base de données]]

---

## La relation

Le modèle relationnel est basé sur la **relation**.

> Une relation est une **structure tabulaire** (lignes et colonnes) représentant des éléments du monde réel.

Règles :
- Une relation doit contenir **au moins une colonne**
- Une relation peut ne contenir **aucune ligne** → on dit qu'elle est **vide**

---

## Les attributs

Ce sont les **colonnes** de la relation.

- Le nom doit être **unique** dans la relation
- Le nom doit être **représentatif** de son contenu

```
Exemples : NomProduit, PrixProduit
```

---

## Les occurrences (tuples)

Chaque **ligne** de la relation = une occurrence = un **enregistrement** = un **tuple**.

---

## Cardinalité et degré

| Concept | Définition | Exemple (table Voitures) |
|---|---|---|
| **Cardinalité** | Nombre de **lignes** | 3 voitures = cardinalité 3 |
| **Degré** | Nombre de **colonnes** | Marque, Modèle, Série, Numéro = degré 4 |

---

## Table des synonymes

| Modèle relationnel | SQL courant | Autre terme |
|---|---|---|
| Relation | Table | Entité |
| Attribut | Colonne | Champ |
| Tuple / Occurrence | Ligne | Enregistrement |

> 💡 Ces trois familles de termes désignent exactement les mêmes concepts. On les retrouve selon le contexte (théorique, SQL, ou base de données).

---

## Résumé visuel

```
TABLE (relation)
│
├── COLONNES (attributs)
│   ├── Référence  ← clé primaire
│   ├── Nom
│   ├── En stock
│   └── Prix (€)
│
└── LIGNES (tuples / enregistrements)
    ├── 554871 | Confiture de fraise | true | 4.80
    ├── 543154 | Gelée de coing      | true | 3.75
    └── ...
```

Les **valeurs** stockées peuvent être : nombre, texte, booléen, date, NULL…

---

> Précédent : [[01 - Introduction aux bases de données]] | Suivant : [[03 - Les objets d'une base de données]]
