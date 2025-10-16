# 2.4 Use Cases

## Primary Use Cases

### UC001: Join and Start Game
- **Actor**: Player
- **Precondition**: QR code scanned or URL visited
- **Flow**: 
  1. Player accesses game URL on device
  2. System displays waiting screen
  3. Second player joins within reasonable time
  4. Game starts automatically with 3-second countdown
- **Postcondition**: Both players see maze and can move

### UC002: Navigate and Compete  
- **Actor**: Players (both)
- **Precondition**: Game session active
- **Flow**:
  1. Players move through maze using device controls
  2. System synchronizes positions in real-time  
  3. Players search for key while potentially using abilities on opponent
  4. Player who finds key races to exit
- **Postcondition**: Winner reaches exit or game times out

### UC003: Spectate Game
- **Actor**: Event Organizer, Audience
- **Precondition**: Game session active, spectator view enabled  
- **Flow**:
  1. Organizer selects active game session to display
  2. Full maze view shows on large screen
  3. Audience can see both players' positions and actions
  4. Real-time updates maintain engagement
- **Postcondition**: Game conclusion visible to all attendees

### UC004: Handle Disconnection
- **Actor**: System
- **Precondition**: Player loses network connection
- **Flow**:
  1. System detects player disconnect
  2. Game terminates for both players  
  3. Both players return to start screen
  4. Spectator view shows appropriate message
- **Postcondition**: System ready for new game sessions

## Secondary Use Cases

### UC005: Track High Scores  
- **Actor**: Player, System
- **Flow**: Winner enters initials for leaderboard, system stores top 10 scores
- **Priority**: Should Have

### UC006: Multiple Session Management
- **Actor**: System, Event Organizer  
- **Flow**: Organizer switches between different active games on spectator display
- **Priority**: Should Have