# 11 — Les vues (Views)

> Précédent : [[10 - DML -- Data Manipulation Language]] | Suivant : [[12 - ...]]

Une **vue** est une requête SQL enregistrée de façon persistante dans la base de données. Elle se comporte comme une table virtuelle : on peut l'interroger avec `SELECT`, mais elle ne stocke pas de données elle-même — elle les récupère dynamiquement depuis les tables sous-jacentes.

---

## Types de vues

| Type | Description |
|------|-------------|
| **Vues système** | Créées et gérées par le moteur SQL (comme les tables et procédures système) |
| **Vues utilisateur** | Créées par les utilisateurs pour leurs besoins spécifiques |

---

## Avantages et désavantages

### ✅ Avantages

- **Confidentialité** — Permet d'exposer uniquement certaines colonnes ou lignes d'une table, sans donner accès à la table complète.
- **Attributs virtuels** — Permet de créer des colonnes calculées (ex. : `prix * quantite AS total`) sans modifier la structure de la table.
- **Simplification** — Une vue complexe peut être réutilisée simplement comme si c'était une table.

### ❌ Désavantages

- **Lenteur relative** — La vue est recalculée à chaque exécution, ce qui peut être moins performant qu'une table réelle.

---

## Commandes DDL sur les vues

### CREATE VIEW — Créer une vue

```sql
CREATE VIEW vNouvelleVue
AS
SELECT *
FROM tblTable
WHERE condition;
```

> ⚠️ La clause `ORDER BY` n'est **pas acceptée** dans la définition d'une vue.

**Exemple concret** :

```sql
CREATE VIEW vClientsQuebec
AS
SELECT Nom, Prenom, Ville
FROM tblClients
WHERE Province = 'QC';
```

---

### ALTER VIEW — Modifier une vue existante

Permet de redéfinir la requête d'une vue sans la supprimer et recréer.

```sql
ALTER VIEW vNouvelleVue
AS
SELECT col1, col2
FROM tblTable
WHERE nouvelleCondition;
```

---

### DROP VIEW — Supprimer une vue

```sql
DROP VIEW vVotreVue;
```

> ⚠️ La suppression d'une vue est **irréversible**. Les données des tables sous-jacentes ne sont pas affectées.

---

## Résumé — Tableau comparatif

| Commande | Action |
|----------|--------|
| `CREATE VIEW` | Crée une nouvelle vue |
| `ALTER VIEW` | Modifie la définition d'une vue existante |
| `DROP VIEW` | Supprime une vue |
