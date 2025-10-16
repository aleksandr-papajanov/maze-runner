# 2.2 Functional Requirements

## Core Game Mechanics (Must Have)
- **FR001**: Two players compete simultaneously in the same maze instance
- **FR002**: Players must find a randomly-placed key before accessing the exit
- **FR003**: First player to reach exit with key wins the game
- **FR004**: Real-time position synchronization between players (<100ms latency)
- **FR005**: QR code access - players scan code to join game within 1 minute maximum

## Ability System (Should Have - Nice to Have, Not Essential for MVP)
- **FR006**: Sleep potion - freezes opponent for 2 seconds and forces key drop
- **FR007**: Confusion ray - reverses opponent's joystick controls (left becomes right)
- **FR008**: Strategic traps - can be placed at exit or key locations
- **FR009**: Stunning projectiles - visible projectiles that can be fired at opponents
- **FR010**: Mixed activation system - power-ups auto-activate on pickup, strategic items use manual buttons
- **FR011**: Three ability buttons on mobile (right side), keyboard keys (JKL) on desktop
- **FR012**: Limited inventory - maximum 3 different ability types, refill after use or collect from maze

## Game Content (Must Have)
- **FR013**: Single maze layout with fixed wall structure for consistency
- **FR014**: Map randomization - randomize key placement, exit location, and power-up positions each game
- **FR015**: Limited viewport per player (fog of war effect)
- **FR016**: Visual feedback for all player actions and ability usage
- **FR017**: Automatic game termination after win condition or player disconnect

## Scoring and Side Challenges (Should Have)
- **FR018**: Point collection items (apples/coins) scattered throughout maze for high score
- **FR019**: Letter collection side challenge - collect letters to spell secret word for bonus prizes
- **FR020**: Time-based scoring - faster completion yields higher scores
- **FR021**: High score leaderboard with top 10 entries and initials (pinball-style)
- **FR022**: Bonus point system for completing side challenges while still winning main game

## Multiplayer Support (Must Have)  
- **FR023**: Support 5 concurrent game sessions (10 total players)
- **FR024**: Automatic matchmaking - first available player pairs with next joining player
- **FR025**: Spectator view displays full maze and both player positions on separate screen
- **FR026**: Teacher can switch between different active game sessions on spectator display

## User Interface (Must Have)
- **FR027**: Controls adapt to device type (touch joystick vs keyboard)
- **FR028**: Clear visual distinction between player avatars with direction indicators
- **FR029**: Game status display (timer, abilities, score, inventory)
- **FR030**: 8-directional movement support (not just 4-directional)
- **FR031**: Mobile controls - left thumb joystick, right thumb ability buttons
- **FR032**: Desktop controls - WASD movement, JKL ability activation
- **FR033**: Compass help system - after 5 minutes, show direction to key or opponent
- **FR034**: Viewport fairness - same viewport size regardless of device screen size for equal gameplay

## Optional Features (Should Have)
- **FR035**: Speed boost power-up (auto-activates on pickup)
- **FR036**: Enhanced vision power-up (expanded view radius)
- **FR037**: Post-game results screen with winner announcement, final score, and time
- **FR038**: Flexible time limits - 90% finish within 5 minutes, allow 7-8 minutes for remaining 10%