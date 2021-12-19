# RPG-Project-Public
This a public showcase of features present in my RPG Project. My goal was to implement many of the features present in other open world RPG titles, such as a branching dialogue system, branching quest system for nonlinear story development, character leveling, item and inventory management, and more.


## Branching Dialogue system

<div align="center">
<img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/branching%20dialogue.gif" width="512" height="384">
</div>

<font size="30"> **Explanation\:** </font>

The branching dialogue system is, in essence, a directed graph. If a dialogue node has more than one dialogue node in its adjacency list, buttons are instantiated, which can be selected to move to the next node. If there is a single dialogue node in the adjacency list, that node is loaded. If there are no nodes in the current dialogue node's adjacency list, dialogue is terminated.


## Inventory Management


<div align="center">
<img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/items%20and%20inventory%20compressed.gif" width="512" height="384">
</div>
 
 <font size="30"> **Explanation\:** </font>

Like any good RPG, the character can collect and use items dropped by defeated opponents, or found in the game world. The inventory UI implements a tab system to allow for viewing specific item types. It also accounts for stackable and non-stackable items, and displays the image and description associated with each item. Different item types also display different text on the button used to use the selected item.

## Melee Combat

<div align="center">
<p float="center">
   <img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/melee%20punching%20compressed.gif" width="400" height="300" />
  <img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/melee%20bat%20compressed.gif" width="400" height="300" />
</p>
</div>
 
 <font size="30"> **Explanation\:** </font>
 
Melee combat is done via use of IEnumerator methods and animation events called during specific frames, during which hitboxes (trigger box colliders) are activated. When an NPC is hit, their attack cooldown is reset, so as to allow the player to avoid being hit every time they engage in melee combat. If the player has a melee type weapon in their inventory, it can be equipped and used in lieu of unarmed combat.

## Shooting

<div align="center">
<img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/shooting%20compressed.gif" width="512" height="384">
</div>
 
 <font size="30"> **Explanation\:** </font>

The more fun and engaging combat type in this project involves shooting guns. When the player shoots, a projectile is spawned with an initial velocity and a reference to the character sheet of its source. As this projectile travels, if a collider overlap is detected with an NPC, a roll is done to determine whether the projectile hits and how much damage is dealt. A number of factors are taken into consideration for both, such as the source's Guns skill, Dexterity, distance to target, as well as base accuracy and damge of the gun in use. The resulting calculation is then modified by a small, random amount. Shooting is so far one of the elements of the project that leans most heavily on the RPG characteristics of the game.
