# Butching Datapack

This datapack provides an alternative system for meat in minecraft

## Features
* Datapack for Minecraft 1.15.X
* Animals do not drop meat anyomre but lie dead on the floor, you can collect the body by right-clicking it. Currently included:
   * cows
   * pigs
   * sheeps (wool is still dropped on kill)
   * bears, pandas, llamas and horses planned
* Carcasses can be used as shields
* You can cook a carcass by placing down a campfire with 2 fences on each side, then right clicking above the campfire
* You can create a butching table by placing a smooth stone slab inside an item frame that is on a crafting table
* Once you have a butching table, you can place a carcass on it and collect ressources from it by right-clicking it with a tool

## Installation
### Installing
* Download the datapack and place it inside the datapack folder of your world (no need to unzip)
* Download the ressource pack and place it inside your ressourcepack folder (no need to unzip)
* Install the ressource pack and reload your world
* Go to the Advancement tab, you should see a tab called <Installed Datapacks> with an advancement for the pack
* Set your language to "English (US)" (unless you want your items to be called "item.breakmit.butcher.carcass.name)
### Uninstalling
There 2 ways of uninstalling the datapack:
* ```/function breakmit:butcher/uninstall``` to remove the scoreboards, then stop the pack. Use this if you will use the pack again.
* ```/function breabmit:butcher/uninstall_full``` to remove the scoreboards and all entities, then stop the pack. Use this if you wont use the pack anymore
### Configuration
from the game, you can modify a few things with these functions:
* `/scoreboard players set #max btc.cook.timer X` set the time needed to cook (X=time in ticks (1/20 seconds))
* `/scoreboard players set #max btc.carcTimer X` set how long it takes fo carcasses to be removed (X=time in ticks)
* `/scoreboard players set #max btc.ray.timer X` set how far ray tracing is computed (X=distance in 1/2 blocks)

## Details
This sections contains details on the features
### Carcasses
 * To take dead bodies, you need to right click just above them, in the middel of the model with nothing in your hand
 * Do not right click a carcass with a helemet in hand as you will loose it
 * Dropping a carcass will place it down
 * You can use a carcass as a shield, it will remain usable even after taking hits
 * Raw carcasses will be destroyed after some time (see below)
### Cooking
* This is the structure for campfires:

![](https://github.com/Breakmit/Datapacks/blob/master/Butching/examples/campfire.png)

* To cook something, you need to right click between the upper fences
* If you cant place a carcass on the campfire, try breaking and replacing it. Campfire placement is handled using ray tracing and because of client-server async and the fact that functions are not computed at the same time as block placing, you can move between when you place the block and when the ray tracing starts <hich causes the ray to never find the campfire
* Campfires placed before installing the pack or not placed by a player can't be used
### Butching Table
* To create a butching table, place an item frame with a Smooth Stone Slab in it on the top of a crafting table
* Right click the item frame with a carcass in hand to place it
* You can now right click (the item frame) 3 times with different tools to get ressources, the first click will drop leather, the second one meat and the last on bones. Here is a table of the amount or ressources obtained with each ool:

stage|axe|sword|shears
--|---|-----|----- 
1st: leather|wrong tool: a few|ok tool: some|right tool: a lot
2nd: meat|ok tool: some|right tool: a lot|ok tool: some
3rd: bones|right tool: a lot|ok tool: some|wrong tool: none
