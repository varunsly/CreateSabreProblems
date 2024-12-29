# Action Castle - Sabre Planning Implementation

## Overview
This repository contains an implementation of Action Castle as a planning problem using the Sabre narrative planner. The project converts a traditional text adventure game into a formal planning domain where characters, locations, and items interact through well-defined actions and state changes.

## Project Structure

### World Model

#### Locations

##### Castle Exterior
* Cottage
* Garden Path
* Fishing Pond
* Winding Path
* Top of Tree
* Drawbridge

##### Castle Interior
* Courtyard
* Tower Stairs
* Tower
* Dungeon Stairs
* Dungeon
* Feasting Hall
* Throne Room

#### Characters
* **Player**: The protagonist seeking to become royalty
* **Princess**: Royal character trapped in the tower
* **Guard**: Protects the castle with sword and key
* **Ghost**: Haunts the dungeon, possesses the crown
* **Troll**: Guards the drawbridge, can be appeased with food

#### Items

##### Key Items
* **Crown**: Required for becoming royalty
* **Key**: Opens the tower door
* **Sword**: Weapon for combat
* **Fishing Pole**: Used to catch fish

##### Secondary Items
* **Branch**: Can be used as a weapon
* **Candle**: Can be lit
* **Lamp**: Provides light
* **Fish**: Can be caught and used
* **Rose**: Can be given as a gift

#### Properties
* Path connections between locations
* Character and item locations
* Inventory management
* Object states (lit/unlit, locked/unlocked)
* Character attributes (royal, married, emotions)

### Actions

#### Movement
##### `walk(character, from, to)`
* Allows characters to move between connected locations
* Requires valid path connection
* Character must not be incapacitated

#### Item Manipulation
##### `get(character, item)`
* Picks up gettable items from locations
* Item must be in same location as character
* Item must not be in anyone's inventory

##### `give(character, npc, item)`
* Transfers items between characters
* Both characters must be in same location
* Special effects when giving items to certain NPCs

#### Character Interactions
##### `propose(character, npc)`
* Initiates marriage between characters
* Both must be happy and unmarried
* Transfers royal status if applicable

##### `hit(character, npc, item)`
* Combat action using weapons
* Can incapacitate NPCs
* Special effects when hitting guard

#### Special Actions
##### `read()`
* Used for ritual with ghost
* Requires specific conditions
* Results in ghost being banished

##### `wear(character)`
* Puts on the crown
* Requires royal status
* Grants crowned status

### Utility Functions

#### Basic Goals
```prolog
# Becoming Royal
if(royal(Player)) 1 else 0

# Obtaining Crown
if(inv(Crown) == Player) 1 else 0
