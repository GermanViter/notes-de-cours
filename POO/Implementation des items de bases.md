# Implementation
- ## Package : 
	- **Core** pour definire ce que c'est un item
	- Nouveaux **rpg.items** pour les items de soins et d'attaque

- ## GameItem.java (abstrait)
	- ### Fields
		- nom
		- description
		- Message
	
- ## HealingItem.java (abstraite, extends GameItem)
	- ### Fields
		- healAmount
		- healPercent

- ## HealingPotion.java

- ## AttackItem.java (abstraite , extends GameItem)
	- ### Fields
		- damageAmount
		-  damagePercent

- ## Grenage.java (extends AttackItem)

- ## Pistol.java (extends AttackItem)


