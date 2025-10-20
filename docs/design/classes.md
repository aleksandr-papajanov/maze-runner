# 3.1.1 Klassdiagram

Statisk design - Compile-time klassstruktur.

## Kärnklasser

### GameSession (C#)
- **Egenskaper**: sessionId, players[], gameState, startTime, maze, keyLocation, exitLocation
- **Metoder**: addPlayer(), removePlayer(), startGame(), endGame(), processPlayerAction()

### Player (C#)
- **Egenskaper**: playerId, position, inventory[], isAlive, score, lastActivity
- **Metoder**: move(), useAbility(), collectItem(), dropKey()

### Maze (C#)
- **Egenskaper**: width, height, walls[][], items[], spawnPoints
- **Metoder**: isValidMove(), getVisibleArea(), placeRandomItems()

### GameItem (C#)
- **Egenskaper**: itemType, position, effect, duration  
- **Metoder**: activate(), deactivate(), applyEffect()

### GameHub (C# SignalR)
- **Egenskaper**: activeConnections[], gameSessions[]
- **Metoder**: broadcastUpdate(), handlePlayerDisconnect(), createSession()

*[PLACEHOLDER: UML-klassdiagram som visar relationer, arv och nyckelmetoder för alla klasser]*

## Dataflödesarkitektur
1. **Klientinmatning**: Spelaraktioner fångade i React-komponent
2. **Validering**: C# server validerar aktion mot spelregler  
3. **Tillståndsuppdatering**: Server uppdaterar auktoritativt speltillstånd
4. **Sändning**: SignalR skickar uppdateringar till alla klienter i session
5. **Rendering**: React-komponenter uppdaterar display baserat på mottaget tillstånd