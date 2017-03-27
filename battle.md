# Battle System
## Introduction

## Architecture

![Architecture diagram](images/diagram_battle.png)

### Data

The following section includes details on structures of persistent files used throughout the battle part of the game. With the sole exception of map files, all files are in human-readable JSON format.

#### Map

Maps are stored in a lua script file. Tiled export formats also include JSON and CSV, however the choice of a lua file including a table definition is preferable as it allows the programmer to skip deserialization. For a brief summary of contents, please refer to the Technology section of this thesis. As of version 0.17 Tiled also supports Defold's native tile format, however the current implementation only allows for orthogonal maps and is therefore unsuitable for my game.

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

### Components
