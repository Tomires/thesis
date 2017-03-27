# Battle System
## Introduction

## Architecture

![Architecture diagram](images/diagram_battle.png)

### Data

The following section includes details on structures of persistent files used throughout the battle part of the game. With the sole exception of map files, all files are in human-readable JSON format.

#### Map

Maps are stored in a Lua script file. Tiled export formats also include JSON and CSV, however the choice of a Lua file including a table definition is preferable as it allows the load routine to skip deserialization, which can be advantageous when using larger map files. For a brief summary of contents, please refer to the Technology section of this thesis. As of version 0.17 Tiled also supports Defold's native tile format, however the current implementation only allows for orthogonal maps and is therefore unsuitable for my game.

The game uses four map layers to store data:

1. large_object - contains sprites spanning multiple tiles (e.g. trees)
2. object - contains smaller obstacles such as rocks or tile decorations
3. logic - used by the battle logic script to determine whether a cell is accessible
4. terrain - contains base tiles

#### Dictionary

The file includes two arrays. The first array is used for less powerful spells and includes individual characters, which exclusively use kun'yomi readings, the second includes more complex composite characters used for more powerful spells, typically using on'yomi readings. Each entry includes a kanji character, its kana transcription and an English translation.

```JSON
[

[{"kanji": "日", "kana": "ひ", "meaning": "day"},
{"kanji": "人", "kana": "ひと", "meaning": "person"},
...
],

[
{"kanji": "銀行", "kana": "ぎんこう", "meaning": "bank"},
{"kanji": "小説", "kana": "しょうせつ", "meaning": "novel"}
...
]

]
```

#### Spellbook

The file includes an array of spells used in the game. Each spell has a name, mana cost and a difficulty which corresponds to each of the arrays in dictionary and accept values of either 1 or 2. Spells have a base damage, which decreases with time used up by player to answer the query, minimal and maximal range in cells indicating distance from player character.

Damage range can either be set to 1 which inflicts damage only on the selected cell or a larger integer, which also affects a corresponding number of surrounding cells - an effect often referred to in video game design as an Area of Effect (AoE) spell. The Linear AoE attribute can be set to 1 to make the spell affect targets behind the selected cell (from player character's point of view), 2 to inflict damage to targets in-between the player character and selected cell or 0 to use the more traditional planar AoE.

```JSON
[

{
  "name": "Whirl",
  "cost": 2,
  "kanji_difficulty": 1,
  "base_damage": 45,
  "min_range": 1,
  "max_range": 1,
  "damage_range": 1,
  "linear_aoe": 0
},
...
]
```

### Components
