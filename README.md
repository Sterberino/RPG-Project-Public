# RPG-Project-Public
This a public showcase of features present in my RPG Project. My goal was to implement many of the features present in other open world RPG titles, such as a branching dialogue system, branching quest system for nonlinear story development, character leveling, item and inventory management, and more.


## Branching Dialogue system

<img src="https://github.com/Sterberino/RPG-Project-Public/blob/main/compressed%20showcase%20gifs/branching%20dialogue.gif" width="512" height="384">

<font size="20">**Explanation**</font>
The branching dialogue system is, in essence, a directed graph. If a dialogue node has more than one dialogue node in its adjacency list, buttons are instantiated, which can be selected to move to the next node. If there is a single dialogue node in the adjacency list, that node is loaded. If there are no nodes in the current dialogue node's adjacency list, dialogue is terminated.
