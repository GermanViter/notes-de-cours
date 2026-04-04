# Shadow Arena
## Description
Le concepte de se jeux viens de [donjon et dragons](https://fr.wikipedia.org/wiki/Donjons_et_Dragons). La seul difference avec le jeux de societe c'est que le maitre du jeux est random. C'est a dire que les evenement du jeux comme les aparitions de monstres sont totalement aleatoires. 

---

## Choix de heros :

| Type de hero | ATQ | HP  | SPE                  |
| ------------ | --- | --- | -------------------- |
| Mage         | 25  | 100 | regeneration         |
| Warior       | 20  | 150 | attaque lourde : +10 |
|              |     |     |                      |

---

## Structure du projet
Le projet est divises en plusieurs packages qui ont des utilites differentes.
- **src.com.rpg.core** contient les classes abstraite coeurs du jeux qui definissent le fonctionnement de tous les elements comme les personnages (mobs ou hero) et les interfaces.

- **src.com.rpg.entities**, comme le nom l'indique, contient les differentes entites qui herites de la classe GameCharacter dans **core** comme *mage*,  *warrior*, *dragon*, *goblin*. Ces classes contienne des methodes qui override des methodes definies dans leur interfaces ou dans leur classe parent.

- **src.com.rpg.main** contient la classe *Main.java* ou il y a la boucle principale du jeux et ou tous les evenements du jeux se deroulent.

- Pour faciliter la compilation du projet, un *Makefile*, a ete nessessaire.


