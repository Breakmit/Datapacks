# Colored Names & AFK Display


This datapack for servers combines an AFK display system and colored names, all without plugins. This works using teams so it might not be compatible with some datapacks and will definitely not be with datapacks that add suffixes, prefixes, change collision rules or do anything with teams.

## Features
* Name color can be changed using `/trigger color.<color>`
* Automatic AFK display
* Admin Configuration

## Installation
* Download the datapack
* Place it in your datapack folder
* Reload your world

## COnfiguration
To modify permissions, the datapack needs to be unzipped. All the configuration is done in `data/caa/functions/admin_config.mcfunction`.
Here are the different options
* `scoreboard players set playersColor caa.values 1`
  * 1 = All  players can change their color
  * 0 = Only specified players can change their color
* `execute as @a[name=!Steve, name=!Alex] run tag @s add caa.canColor`
  * This line controls who can change color, it only takes effect if the above value is 0. It is possible to have multiple lines for more complex permissions
  * If you know commands, all you need to know is every player whith the tag  `caa.canColor` can change color
  * Otherwise, here are some syntaxes you can use:
    * `execute as @a[name=<name>] run tag @s add caa.canColor` only lets the specified player change color, you can have multpile lines to give the permission to multiple players
    * `execute as @a[name=!<name1>, name=!<name2>] run tag @s add caa.canColor` lets all players change color except the specified ones. Here, using multiple lines will not work, the different name must use multiple `name=!` in the brackets, separated by ','
* Players with command access can change the color of other players ingame with `scoreboard players set <name> color.<color> 1`
* `scoreboard players set AFKdelay caa.values <n>`
  * n = How long before a player that is not moving beomes AFK (in seconds)

Performance:

* every 10s:
  * `commands`: up to 41+32*(Players)
  * `NBT access`: 0
  * `@e`: 0
* every 1s
  * `commands`: 12+16*(Players going AFK)
  * `NBT access`: 6*(Players)
  * `@e`: 0
