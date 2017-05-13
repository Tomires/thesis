# Testing

Three individuals were selected to test an unfinished prototype featuring the first two quests. The focus of our play testing sessions was primarily on usability and accessibility. As the graphical part of the user interface hadn't been finished at that time, I wanted to use this opportunity to analyse which elements were often overlooked in order to pass the resulting information onto David, our graphics designer. Secondly, we were looking for both minor and game-breaking bugs.

## Setting

All three individuals had previously mastered basics of Japanese, including knowledge of hiragana. Two individuals had prior experiences with an earlier build of the game, which contained some, but not all battle mechanics. One individual did not have any prior experience with the game and for the rest of the testing group, this was their first experience with the exploration portion of the game.

Testing was conducted on two different machines running the following operating systems:
- elementaryOS 0.4 "Loki"
- macOS 10.12 "Sierra"

In addition to the three testing sessions, we have briefly tested the game on three additional operating systems:
- Windows 7
- Windows 8.1
- Windows 10

## Results

Sessions were each 15 to 20 minutes in length with testers reacting positively to the overall gameplay experience. I have divided this section into four subsections. The first two sections include technical issues encountered, the third talks about game design issues that need to be resolved and the fourth relates to issues regarding user experience.

### Critical bugs

The game has issues with display scaling in Windows 10. When scaling is enabled, the game window either does not fully display or displays partially on a secondary display. This practically limits the use on HiDPI machines running the OS. I did not encounter the issue on machines running macOS, Linux or earlier versions of Windows operating system. I have notified the developers about this behaviour.

Another critical issue regarding the game engine used is the inability to dynamically set a resolution on runtime. The game is currently hard coded to run at a resolution of 1920 by 1080 pixels. If a user attempts to launch the game on a system with a lower resolution, it causes the game to crash on startup. There are two possible ways to solve this issue. One is to create a launcher application which would allow the user to select an appropriate resolution prior to launching the game, an approach used heavily by videogames built using the Unity game engine. The other is to wait for an official roll-out of the Native Extensions system, which should allow for writing code that utilises OS-specific APIs in order to obtain a supported resolution.

### Minor bugs

- When an enemy moves, it can sometime pass the player without attacking them.
- The camera moves abruptly, which can distract the player.
- To interact with enemies and NPCs, the player has to click on the tile the character is located on.
- The player automatically initiates unwanted conversations with NPCs that are located en-route to target.

### Game design issues

- The game would benefit from having AoE spells with diagonal targets. In the current state, the player sometimes have no choice but to end the turn without attacking.
- The damage output of more expensive spells should be increased in order to motivate the player to use them more often.

### User experience

- The tutorial should limit possible movement during the first battle. It is possible for the player to reach a tile diagonal to the enemy, which leaves the player with no option but to end the turn, thus breaking the tutorial's flow.
- Players often do not pay enough attention to NPC dialogues, which can create confusing experiences for the player if an NPC instructs them to visit another NPC in order to continue the quest chain.
- Two testers have made repeated mistakes while answering queries related to parsing a trailing 'n' character. The parser should be modified to convert a trailing 'n' character to the corresponding hiragana character (ん).
- One tester thought the game wanted them to enter on'yomi or kun'yomi readings of individual characters rather than readings of kanji compounds. The interface has been redesigned to accommodate this issue by including on'yomi and kun'yomi readings on the back of a rotating tablet element as these readings are not complementary to the gameplay experience.
- One tester had issues navigating the map. The use of isometric perspective means that the player has two possible ways to interpret a cardinal direction. This issue will be partially solved by implementing a map interface in the future version of the game.
