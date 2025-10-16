1. Game Mechanics and Items

- How should the game be intuitive to get started with (is there a need for tutorial, introduction sequence)?
**Answer**: The game should be extremely intuitive - most people know how to solve a maze. The concept should be simple: find the key, find the exit. From scanning a QR code to playing should take maximum 1 minute. No need for tutorials or complex explanations.

- What specific items/bonuses exist in the game and how do they affect player progress (e.g. acceleration, protection)?
**Answer**: Speed boost, better vision (expanded view radius if fog of war is implemented), point-collecting items like apples/coins for high score, possibly letter collection for secret word challenges.

- What specific items/actions can be used to affect the opponent (e.g. slowing down, blocking, traps)?
**Answer**: Sleeping potion to freeze opponent for 2 seconds and make them drop the key, confusion ray that reverses controls (left becomes right), traps that can be placed strategically at the exit, stunning projectiles.

- What limitations/penalties are imposed on a player affected by an item?
**Answer**: Freeze effects last about 2 seconds, confusion ray reverses joystick controls, key is dropped when hit by certain items.

- How are these items/actions activated? Automatically when picked up, or manually through player choice (with a dedicated button)?
**Answer**: Mixed approach - power-ups like speed boost activate automatically when walked over, strategic items like weapons/traps are activated manually with buttons (3 ability buttons on right side of mobile screen).

- Does a player need to see that the opponent has used an item against them, and how (visual, sound)?
**Answer**: Primarily visual feedback is important due to noisy environment (100+ people). Need to see projectiles being fired, splash effects when hit, visual indicators of status effects. Sound effects are secondary.

- What type of movement mechanics are used in the maze (keyboard/arrow keys, swipes, clicks)?
**Answer**: Mobile: on-screen joystick with left thumb, abilities with right thumb. Desktop: WASD keys with 8-directional movement, abilities with keyboard keys like JKL if mouse is not available.

- How many items can be in the maze simultaneously?
**Answer**: Limited inventory - maybe 3 different ability types, use one and it refills after a few seconds, or collect new ones from the maze.

2. Win Conditions, Duration and Difficulty

- What is the exact win condition? First to exit, or are there additional criteria (points, collected items)?
**Answer**: Primary win condition is first person to reach the exit with the key. Side missions like collecting letters for a secret word can give bonus prizes, but main win is reaching exit first.

- What happens when maximum game time (5 minutes) runs out? Draw, win for whoever got furthest, or loss for both?
**Answer**: Time is not a hard deadline. Game is designed so 90% of players finish within 5 minutes. For the remaining 10%, it's fine if they play 7-8 minutes. After 5 minutes, players might get help like compass direction to the key.

- Should the maze size be fixed or dynamically generated? What are the expected minimum and maximum sizes?
**Answer**: One fixed map is sufficient for MVP. Walls can be the same, but randomize key placement, power-ups, and exit location. Since most players play only once, it's still a new experience each time.

- How many difficulty levels should the game have?
**Answer**: No difficulty levels needed - keep it simple. Same game for everyone.

- Are random events allowed during gameplay (e.g. paths changing, new items spawning)?
**Answer**: Not mentioned as a requirement. Focus on core mechanics first.

3. User Interface and Display (UI/UX)

- Should players be able to see each other's positions on the map/screen? If yes, how is their position shown (icon, marker, minimap)?
**Answer**: Players see only a limited viewport centered on themselves (mobile shows small portion, fog of war possible). Spectator screen shows full map with both players visible. Players can "cheat" by looking at the big screen, but this creates fun social interaction.

- What elements must the player see on their screen (map, timer, status field for items)?
**Answer**: Player avatar with clear direction indicator (arrow or sprite), joystick controls, 3 ability buttons, inventory/status, limited map view centered on player. Same viewport size regardless of screen size for fairness.

- Does statistics need to be shown in real-time (e.g. speed, percentage progress, used bonuses)?
**Answer**: Timer display, point count for high score, possibly compass direction to opponent or key after certain time.

- How should a game session be presented on the big screen (one player at a time, split-screen, overview map)?
**Answer**: Full overview map showing both players simultaneously, not split-screen (would be too hard to see). Teacher can switch between different ongoing sessions if multiple games are running.

- Are there requirements for the game's design/style (e.g. retro, minimalist, futuristic)?
**Answer**: Avatar must match the environment thematically (e.g., if wizards, then dungeon setting). Fantasy theme suggested with isometric map. Otherwise quite open, but keep consistency between character and background.

- Is sound required (background music, sound effects for activation/interaction)?
**Answer**: Background music not needed. Sound effects are secondary due to noisy environment (100+ people). Visual feedback is most important, but some sound effects for shooting/actions can be included.

4. Multiplayer and Technical Requirements

- What is the expected maximum number of pairs playing simultaneously during the event ("open house")?
**Answer**: Maximum 5 concurrent sessions (10 players total). Only about 10 people can physically fit around the booth anyway. Even if 30 sessions were running, it wouldn't be a heavy data load.

- Is each pair completely independent, or is interaction/influence between different playing pairs possible?
**Answer**: Each pair is completely independent. No interaction between different game sessions.

- Should mobile devices support full gameplay (with controls) or only be used for viewing/spectator view?
**Answer**: Full gameplay on mobile with on-screen joystick and touch controls. Must work on both Android and iOS, including phones 6-7 years old.

- Which server architecture is preferred: Client-Server or Peer-to-Peer (P2P)?
**Answer**: Client-Server with single server. All game state managed on server and synchronized to clients. This prevents sync issues that occurred in previous projects where calculations were done on phones.

- Do game results need to be saved (for statistics, leaderboards and analysis)? If yes, what type of database is preferred?
**Answer**: High score system where players can enter initials for top 10, similar to pinball machines. Show final score and time.

- Is any form of authentication/registration of players required?
**Answer**: No authentication needed. Players are matched automatically - first ready player waits for second player to connect, then game starts automatically.

- How should player positions and states be synchronized to minimize the effect of network delay (lag)?
**Answer**: Very little data needs to be sent - just position and occasional ability usage with direction/speed. Server handles all game state to ensure synchronization.

- What is the minimum set of features that must be working for a successful demonstration on open house day?
**Answer**: MVP is one map, key collection, exit finding, basic multiplayer, spectator view. Items and abilities are nice-to-have but not essential.

- Are there accessibility requirements for players with functional variations (e.g. color blindness, motor limitations)?
**Answer**: No special accessibility features required for this context. However, good design practices: different avatar shapes (not just colors) for players, high contrast, primarily visual instructions rather than text, clear distinction between player and opponent.

## Additional Questions Based on Expert Interview

5. Technical Implementation and Platform

- What technology stack is preferred for implementation?
**Answer**: Web-based solution preferred for easy setup. Frontend: React, Vue, or Angular. Backend: C# Blazor, Python Flask/Django, or similar. WebSockets for communication. Avoid Unity as it's complex to set up and maintain.

- How should the game handle player disconnections?
**Answer**: If player loses connection, game ends for both players with "Connection lost, game ended" message. Both return to start screen. No winner declared.

- What happens if someone griefs by intentionally disconnecting when losing?
**Answer**: Not a problem - players are friends from high school just having fun. It's not a serious competitive environment.

6. Game Setup and Logistics

- How is matchmaking handled?
**Answer**: Automatic matchmaking - first player ready waits for second player to connect, then game starts automatically. No choosing opponents to reduce complexity.

- Can teacher/demonstrator spectate specific games?
**Answer**: Yes, teacher gets list of ongoing sessions and can select which one to display on projector. Can switch between different active games.

- What is the target setup time from laptop to running demo?
**Answer**: Maximum 2 minutes. Game should run as web service on laptop or as Docker container on web server.

7. Game Content and Themes

- Are there specific visual themes or characters preferred?
**Answer**: Fantasy theme suggested (wizards/warriors on isometric dungeon map). Avatar must match background thematically. Relatively open as long as it's consistent.

- Should there be multiple maps?
**Answer**: One map is sufficient for MVP. Can randomize key, items, and exit positions while keeping walls the same.

- Can players see the key location initially?
**Answer**: No, key location is hidden. Exit is visible but players must find where it is on the map. After 5 minutes, might give compass direction to key as help.

8. Scoring and Competition

- How detailed should the scoring system be?
**Answer**: Time-based scoring for quick completion, plus optional point collection (apples/coins) for higher scores. Possibly letter collection for secret word bonus prizes.

- Should unfairness be avoided (e.g., spawning next to key)?
**Answer**: Perfect fairness not critical since players only play once. Could make map symmetric for fairness, but not essential.

- Is there replay value needed?
**Answer**: No replay value required. Designed for one-time play experience that's engaging enough to be interesting but doesn't need depth for repeated play.

9. Context and Purpose

- Why was MazeRunner chosen over the previous haptic technology demo?
**Answer**: Previous system was cool but required complex hardware setup, driver installations, and was unreliable (broke with OS updates). Wanted something that "always works" - just open laptop and run in 2 minutes.

- What's the main goal for the open house demonstration?
**Answer**: Engage two players, create spectator entertainment, serve as icebreaker for conversations about computer science education. Replace "Are you interested in computer science?" with "Want to play a game?"

- How long should gameplay sessions be?
**Answer**: 5 minutes target, but flexible. 90% should finish within 5 minutes, remaining 10% can play 7-8 minutes. Goal is quick engagement, not extended gameplay.

- Will this project be used for multiple years?
**Answer**: Yes, Josef has been creating new game projects every year for 4 years. Previous games had issues (sync problems, Unity export complexity). Looking for reliable, maintainable solution.
