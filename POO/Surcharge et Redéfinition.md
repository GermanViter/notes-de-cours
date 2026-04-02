# Redéfinition (`@Override`)

## Comportement différent

> `@Override` sert à redéfinir une fonction pour qu'elle ait un comportement différent

- L'[héritage](https://cegepmv.github.io/420-210/poo_2/index.html) est obligatoire pour la redéfinition
- Même nom
- On redéfinit la classe enfant

### Exemple de code

```Java
// Main.java
Animal a = new Animal("fox", 10); // en supposant que Animal.java existe
Chien c = new Chien("chien", 14);
a.faitUnBruit();
```

#### La classe Animal

```Java
// Classe Animal.java
public class Animal {
    private final String nom;
    private final int age;

    public Animal(String nom, int age) {
        this.nom = nom;
        this.age = age;
    }

    // ...getters et setters

    public String faitUnBruit() {
        return "Animal fait un bruit";
    }
}
```

#### Et pour mettre de l'héritage

```Java
// Classe Chien.java
public class Chien extends Animal {
    private final int nbOsMange;

    public Chien(String nom, int age, int nbOsMange) {
        super(nom, age);
        this.nbOsMange = nbOsMange;
    }

    // ...getter et setter
}
```

#### Finalement, ajouter `@Override` dans Chien.java

> **Note:** Un typo dans la méthode dans `@Override` ne fait pas de redéfinition

```Java
// Chien.java
@Override
public String faitUnBruit() {
    // ici, la fonction faitUnBruit est redéfinie dans la classe enfant
    return "Le chien fait un bruit";
}
```

```Java
// Main.java
(a.faitUnBruit() != c.faitUnBruit()); // true
```

---

# Surcharge

> Pour la surcharge, l'héritage n'est pas obligatoire

- Type de retour **différent**
- Même nom
- Paramètres **différents**
- Comportement **différent**

### Exemple de code

```Java
// ex 1:
public int hello(int i) { return i * 2; }
public int hello(double i) { return (int) (i * 2); } // surcharge ici

// ex 2:
public String retourneText(String s) { return s + "texte"; }
public String retourneText(String s, int t) { return s.repeat(t); }
// surcharge ici
```