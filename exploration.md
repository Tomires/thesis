# Exploration system

## Introduction

## Architecture

### Data structures

#### Item

```JSON
[

  {
    "id": 1,
    "name": "Potion",
    "icon": "potion.png",
    "value": 30,
    "category": "Consumable",
    "effects": {
        "health": 60
    }
  }
...
]
```

#### NPC

```JSON
[

  {
    "id": 1,
    "name": "Old Guy",
    "vendor": 0,
    "starting_dialogue": 25
  }
...
]
```

#### Dialogue

```JSON
[

  {
    "id": 25,
    "text": "I have a favour to ask.
             My crops have been decimated by rabbits you see...",
    "next_dialogue": 26
  }
...
]
```

#### Quest

```JSON
[

  {
    "id": 5,
    "npc": 1,
    "active": true,
    "repeatable": false,
    "description": "Reclaim the land by killing the Elder Rabbit
                    and four of its friends!",
    "prerequisites": [2],
    "triggers": [["KILL_ENEMY", 2, 1], ["KILL_ENEMY", 1, 4]],
    "exp_reward": 500,
    "gold_reward": 60,
    "item_reward": [1, 1, 5],
    "set_npc_dialogue": 54
  }
...
]
```

### Script entities
