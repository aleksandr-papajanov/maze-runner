# MazeRunner Game - Complete Vision

## Game Overview

MazeRunner is a simple, web-based multiplayer maze game designed as an interactive demonstration tool for university open house events. The game creates an engaging "ice-breaker" experience that gets high school students excited about computer science while showcasing student work.

## Core Gameplay Experience

### The Basic Game Loop
1. **Quick Setup**: Students scan a QR code or visit a URL on their phones/laptops
2. **Instant Matching**: First player waits, second player joins → game starts automatically  
3. **5-Minute Adventure**: Players race through a maze to find a key and escape
4. **Spectator Excitement**: Audience watches on a large screen, cheering and giving hints
5. **Simple Conclusion**: Winner celebration, optional high score entry, back to start

### What Players See and Do

**On Your Device (Phone/Laptop)**:
- Top-down view of your character in the maze
- You only see a small portion around your character (like a spotlight in darkness)
- Character faces the direction you're moving (important for aiming abilities)
- Simple controls: Arrow keys/WASD on computer, on-screen joystick on phone
- 3 ability buttons on the right side of screen

**On the Big Screen (Spectator View)**:
- Full maze overview showing both players
- Everyone can see the entire layout, key location, exit location
- Perfect for audience to cheer: "The key is behind you!" or "Watch out, they're coming!"

## Character and World

### Visual Style
- **Top-down perspective** (like classic arcade games)
- **Fantasy theme preferred**: Wizards or warriors moving through a dungeon-style maze
- **Simple but clear graphics**: Easy to distinguish your character from opponent
- **Consistent theme**: If characters are wizards, the maze looks like a dungeon (not modern building)

### Your Character
- Either a detailed animated sprite with legs/movement OR a simple geometric shape with direction arrow
- Different visual appearance from opponent (different color AND different shape - important for accessibility)
- Clear indication of which direction you're facing (affects where you shoot abilities)

## Core Gameplay Mechanics

### The Objective
**Win condition**: Find the key, then reach the exit first
- **Key**: Hidden somewhere in the maze, location randomized each game
- **Exit**: Visible to everyone, but you need the key to use it
- **Strategy element**: You can camp at the exit and ambush the key-holder!

### Movement and Vision
- **Fog of War**: You only see a circular area around your character
- **Maybe**: 5-second full-map preview at the start, then fog kicks in
- **Fair Play**: All devices show roughly the same amount of the maze (same "viewport")

### Combat System - The Fun Part!
Players can use abilities to stop each other:

**Ability Types**:
1. **Stun Shot**: Freeze opponent for 2 seconds, they drop the key
2. **Confusion Ray**: Reverse opponent's controls (left becomes right, etc.)
3. **Speed Boost**: Move faster for a short time (auto-activates when picked up)

**Ability Usage**:
- 3 ability slots, each with different cooldown/usage rules
- Some activate automatically when you walk over them (speed boost)
- Others you save and use strategically (stun shot, confusion ray)
- Visual feedback: See projectiles fly, see impact effects, know if you hit/missed

**Strategic Elements**:
- Hide near the exit and ambush the key-holder
- Set traps at chokepoints
- Hunt down the person with the key using compass direction (given after some time)

## Items and Power-ups

### Collectible Items
- **Bonus Points**: Apple/coin-like objects scattered around maze for high score
- **Power-ups**: Speed boost, better vision, extra abilities
- **Secret Letters**: Optional side-quest to spell a daily word for prizes

### Risk vs Reward
- Collecting bonus items makes you vulnerable (takes time, exposes position)
- Key-holder is visible to others through compass hints after time passes
- Smart players balance speed, combat, and collection

## Technical Experience

### Device Compatibility
**Works on Everything**:
- Modern smartphones (Android/iOS, even 6-7 years old)
- Laptops and desktops (Windows/Mac/Linux)
- Tablets and other touch devices

**Controls Adapt to Device**:
- **Phone**: On-screen joystick (left thumb) + ability buttons (right side)
- **Computer**: WASD movement + keyboard shortcuts for abilities
- **Flexible**: Can use mouse, trackpad, or keyboard-only depending on setup

### Performance Requirements
- **Fast startup**: From QR code scan to playing in under 1 minute
- **Smooth gameplay**: <100ms response time for movements
- **Reliable**: Works even with spotty wifi, handles disconnections gracefully
- **Scalable**: Supports 5 concurrent games (10 players) without issues

## Social and Spectator Experience

### The "E-sports" Element
- **Big screen drama**: Audience sees everything, players don't
- **Natural commentary**: "He's right behind you!" "The key is over there!"
- **Tension building**: Close races to the exit, last-second ability usage
- **Quick turnaround**: Games end fast enough to keep audience engaged

### Educational Value
- **Student showcase**: "This game was made by students in their 3rd year"
- **Tech demonstration**: Shows web development, real-time networking, game design
- **Conversation starter**: Gets students talking about programming and game development
- **Accessibility**: No need to explain complex rules - everyone understands "find key, reach exit"

## Game Flow and Timing

### Typical Game Session (3-5 minutes)
1. **0-30 seconds**: Players join, brief instruction screen, countdown
2. **30 seconds - 3 minutes**: Core gameplay - exploring, finding key, combat
3. **3-5 minutes**: Endgame - key holder racing to exit, final confrontations
4. **Optional**: Overtime assistance (compass to key) if game runs long

### End Conditions
- **Victory**: First player to exit with key wins
- **Connection loss**: Game ends, both players return to start screen
- **Time limit**: Soft limit with assistance, not hard cutoff
- **Results**: Clear winner/loser screen, points display, optional high score entry

## Why This Design Works

### For the University (Josef's Goals)
- **Reliable**: No hardware setup, no driver issues, just open browser
- **Portable**: Runs on one laptop, works anywhere with wifi
- **Maintainable**: Web technology, easy updates, familiar to students
- **Scalable**: Multiple games running simultaneously without problems

### For High School Students
- **Instantly familiar**: Maze games are universally understood
- **Social experience**: Fun to play with friends, fun to watch others
- **Quick gratification**: Fast games, immediate feedback, clear winners
- **Low barrier**: No app download, no account creation, just scan and play

### For the Audience
- **Visual excitement**: Can see the whole game unfold on big screen
- **Participation**: Natural urge to help and cheer for players
- **Understanding**: Easy to follow what's happening, clear objectives
- **Replayability**: Each game is different due to randomized elements

## Development Priorities

### Must Have (Minimum Viable Product)
1. Basic maze navigation with fog of war
2. Key spawning and collection
3. Exit activation with key
4. Simple stun ability
5. Spectator view on separate screen
6. Win/lose conditions

### Should Have (Enhanced Experience)
1. Multiple ability types
2. Visual effects for abilities
3. Bonus point collection
4. High score system
5. Mobile-optimized controls

### Could Have (Nice Additions)
1. Multiple maze layouts
2. Daily word collection quest
3. Animated character sprites
4. Sound effects (where appropriate)
5. Advanced power-ups

This vision gives us a clear target: create a simple, reliable, engaging multiplayer experience that works perfectly for its intended purpose - getting high school students excited about computer science through hands-on play!