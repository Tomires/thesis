# Battle System
## Introduction

## Architecture

![Architecture diagram](images/diagram_battle.png)

### Data

The following section includes details on structures of persistent files used throughout the battle part of the game. With the sole exception of map files, all files are in human-readable JSON format.

#### Map

Maps are stored in a lua script file. Tiled export formats also include JSON and CSV, however the choice of a lua file including a table definition is preferable as it allows the programmer to skip deserialization. For a brief summary of contents, please refer to the Technology section of this thesis. As of version 0.17 Tiled also supports Defold's native tile format, however the current implementation only allows for orthogonal maps and is therefore unsuitable for my game.

### Components
