# 3. System Design

## 3.1 Static Design (Compile-time)

### 3.1.1 Class Diagrams
[TO BE DEVELOPED AFTER EXPERT INTERVIEW]

Core classes to design:
- **GameSession**: Manages game state, timer, players
- **Player**: Position, inventory, network connection
- **Maze**: Layout, collision detection, item placement
- **GameItem**: Speed boost, obstacle, power-ups
- **NetworkManager**: WebSocket communication, synchronization

### 3.1.2 Module Diagram
[TO BE DEVELOPED]

Planned architecture:
- **Frontend Modules**: Game Canvas, Input Handler, UI Components
- **Backend Modules**: Session Manager, Game Logic, Database
- **Communication**: WebSocket API, REST endpoints
- **Display Module**: Spectator view renderer

## 3.2 Dynamic Design (Run-time)

### 3.2.1 Activity Diagrams
[TO BE CREATED AFTER REQUIREMENTS]

Priority diagrams needed:
1. **Game Start Flow**: Organizer creates → Players join → Game begins
2. **Gameplay Loop**: Move → Check collision → Update state → Sync clients  
3. **Game End Flow**: Timer expires/win condition → Display results → Reset

### 3.2.2 Sequence Diagrams
[TO BE CREATED]

Key sequences:
1. **Real-time Movement**: Player input → Server validation → Broadcast update
2. **Item Collection**: Collision detection → Remove from maze → Add to inventory
3. **Session Management**: Create session → Join session → Start game → End game

### 3.2.3 State Diagrams
[TO BE CREATED]

Essential states:
1. **Game Session**: Waiting → Active → Paused → Finished
2. **Player Connection**: Connecting → Ready → Playing → Disconnected  
3. **Game Items**: Placed → Collected → Used → Expired
