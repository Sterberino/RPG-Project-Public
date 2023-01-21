# RPG-Project-Public
This a public showcase of features present in my RPG Project in C# and Unity3D. My goal was to implement many of the features present in other open world RPG titles, such as a branching dialogue system, branching quest system for nonlinear story development, character leveling, item and inventory management, and more. I won't be making the code available, because I want to ship this game someday. I will be offering detailed explanations of the project though.


## Branching Dialogue system

<div align="center">
<img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/branching%20dialogue.gif" width="512" height="384">
</div>

<font size="30"> **Explanation\:** </font>

The branching dialogue system is, in essence, a directed graph. If a dialogue node has more than one dialogue node in its adjacency list, buttons are instantiated, which can be selected to move to the next node. If there is a single dialogue node in the adjacency list, that node is loaded. If there are no nodes in the current dialogue node's adjacency list, dialogue is terminated.

## Flexible and Branching Quest system

<div align="center">
<p float="center">
   <img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/quest1%20compressed.gif" width="400" height="300" />
  <img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/quest2%20compressed.gif" width="400" height="300" />
</p>
</div>

<div align="center">
<p float="center">
   <img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/Quest3%20compressed.gif" width="400" height="300" />
  <img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/Quest4.gif" width="400" height="300" />
</p>
</div>

 
 <font size="30"> **Explanation\:** </font>

Any good RPG must have a fully realized quest system. When designing this quest system, I needed to ask myself what a quest is. The answer I found is that a quest is a task or series of tasks whose availability are determined by the completion state of other quests. Most RPG quests are comprised of the following task types:

<ol>
  <li>Kill a specific character or a number of a character type (Zombie, Bandit, etc.)</li>
  <li>Collect a specific item or a number of an item type</li>
  <li>Trigger a specific piece of dialogue</li>
  <li>Reach a target destination</li>
</ol>
 
The quest system can, as shown above, accomplish the implementation of all of these things. Each quest node has an adjacency list of nodes required to be completed prior to being marked as available. These quest nodes can also require nodes in their adjacency list to be failed or to be not yet available, so as to allow for player choice. The architecture makes use of Unity's Scriptable Object class for cross scene referencing and persistence.
 
Note: Images are from earlier builds of the game.

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


## Saving Data

<div align="center">
<p float="center">
   <img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/save1%20compressed.gif" width="400" height="300" />
  <img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/Save2%20compressed.gif" width="400" height="300" />
</p>
</div>
 
 <font size="30"> **Explanation\:** </font>
 
What good is an RPG if you can't save your progress? The save system makes use of C#'s System.IO namespace and Unity's Application.PersistentDataPath variable, which provides a platform specific path used by unity for data storage. Quests' state, the player's inventory, position and scene, and level information, as well as scene data such as dead NPCs are all saved by serializing information into Json files using Unity's JsonUtility.ToJson() method, which takes as input structs comprised of simple data types such as integers, strings, and arrays/ lists, and formats that information into a json string. Then, using System.IO, the string is saved as a Json file to an appropriate save file (save folder) directory. This information is then retrieved when loading a saved game using JsonUtility.FromJson(). A .png file showing the player's location is also saved using System.IO.File.WriteAllBytes() This .png file is loaded in at runtime when the player is viewing their save. The player can name their save directory, so a check must be done for special characters prior to saving. When the directories are loaded into the save menu to be viewed by the player, the button for selecting the save has text equivalent to the save's truncated directory/ save name.

## Pathfinding

<div align="center">
<p float="center">
   <img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/Pathfinding-Showcase.gif" width="400" height="300" />
  <img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/Context-Steering.gif" width="400" height="300" />
</p>
</div>

<font size="30"> **Explanation\:** </font>

If we want convincing enemies, they need to be able to navigate the game world and avoid obstacles. In order to accomplish this, I wrote an A Star pathfinding script that makes use of Unity's Job system and Burst compiler. This allows for safe, multithreaded code that is translated from IL/. NET bytecode to highly optimized native code using LLVM. Pathfinding is very fast, but it can be faster. Despite this, pathfinding is still compputationally expensive, so if the NPC has no obstructions between it and its target, it simply moves towards its goal without pathfinding. One issue with pathfinding is that because the colliders for NPCs have a non-zero size, the corners of those colliders can get caught on obstacles even with pathfinding. To fix this, I implemented some context steering to help them avoid local obstacles.

## A demo?

Unfortunately, while the core systems are largely in place now, the game still needs a lot of work before it is demo ready. Using the quest system to design playable tests, drawing areas of the game world for the player to traverse, and writing dialogue are all still in progress endeavors. I will absolutely be uploading an executable file containing the demo when the time comes.
