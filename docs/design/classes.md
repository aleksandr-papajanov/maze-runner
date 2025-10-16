# 3.2 Static Design (Class Structure)

## Core Classes

### GameSession (C#)
- **Properties**: sessionId, players[], gameState, startTime, maze, keyLocation, exitLocation
- **Methods**: addPlayer(), removePlayer(), startGame(), endGame(), processPlayerAction()

### Player (C#)
- **Properties**: playerId, position, inventory[], isAlive, score, lastActivity
- **Methods**: move(), useAbility(), collectItem(), dropKey()

### Maze (C#)
- **Properties**: width, height, walls[][], items[], spawnPoints
- **Methods**: isValidMove(), getVisibleArea(), placeRandomItems()

### GameItem (C#)
- **Properties**: itemType, position, effect, duration  
- **Methods**: activate(), deactivate(), applyEffect()

### GameHub (C# SignalR)
- **Properties**: activeConnections[], gameSessions[]
- **Methods**: broadcastUpdate(), handlePlayerDisconnect(), createSession()

*[PLACEHOLDER: UML Class Diagram showing relationships, inheritance, and key methods for all classes]*

## Data Flow Architecture
1. **Client Input**: Player action captured in React component
2. **Validation**: C# server validates action against game rules  
3. **State Update**: Server updates authoritative game state
4. **Broadcast**: SignalR sends updates to all clients in session
5. **Rendering**: React components update display based on received state