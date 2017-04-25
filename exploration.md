# Exploration system

## Introduction

### Quest

The quest system is an important plot device that motivates the player to play the game and helps alleviate the negative effects of grind mechanics on player retention. While researching the possible quest archetypes, I wanted to focus on three aspects - repeatability, quests as means to motivating the player to move between game areas and variability.

#### Repeatability

The first aspect concerns quests that are meant to be experienced multiple times.

#### Exploration quests

These quests are generally one-time only opportunities that are designed to move the player from one area to another in a smooth and believable fashion. These types of quests are utilised in World of Warcraft, where they are referred to as breadcrumb quests. For the sake of simplicity, I will work with branching quest arcs. No two quests will be mutually exclusive.

The following diagram illustrates the relationships between quests, green exclamation marks symbolize main quests, while yellow marks symbolize side quests. Main quests are dependent on one another, while side quests are optional. Many main quests are of the breadcrumb type, as discussed in the previous paragraph, though this is not always the case.

![Quests diagram](images/diagram_quests.png)

#### Variability

One issue a lot of modern role-playing games face is the lack of variability when it comes to quests. The player is generally asked to kill a certain number of enemies or to collect certain items. To help combat this fact, I have listed below some examples that can be used within my game.

- Character hunting quest (triggering conversations with different NPCs)
- Scavenger hunt (locating certain cues hidden within the environment)
- Enemy killing quest (killing a number of enemies of a specified type)
- Crafting quest (collecting a number of resources from crafting nodes)
- Achievement quest (meeting a condition, such as achieving consistent success in regards to the learning element or completing a number of challenges)

### Economy

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

#### Droprate

```JSON
[

  {
    "enemy_id": 1,
    "items": [
        {
            "item_id": 1,
            "probability": 0.3
        },
        {
            "item_id": 3,
            "probability": 0.7
        }
    ]
  },

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

#### Map area

```JSON
[

  {
    "id": 5,
    "name": "Rabbit Island",
    "enemy_types": [[1, 0.2], [2, 0.1]],
    "max_mob_size": 4
  }
...
]
```

### Script entities
