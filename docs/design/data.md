# 3.5 Data Management

## Game State Storage

### In-Memory State (C# Server)
- Player positions and status
- Item locations and availability  
- Game timing and score information
- Temporary ability effects and cooldowns

### Persistent Storage (SQLite)
- High score leaderboard (top 10 entries)
- Game configuration settings
- Usage statistics (optional)

## Data Synchronization Strategy

### Authoritative Server Model
- C# server maintains single source of truth for all game state
- React clients send input events, not state changes
- Server validates all actions before applying changes
- Optimistic client-side prediction for smooth movement feel
- Server correction packets for synchronization errors

### Update Frequency
- Player positions: 20-30 updates per second via SignalR
- Game events: Immediate broadcast
- Status updates: 2-5 updates per second  
- Heartbeat/connection check: Every 5 seconds

## Database Schema (SQLite)

### HighScores Table
```sql
CREATE TABLE HighScores (
    Id INTEGER PRIMARY KEY,
    PlayerName TEXT,
    Score INTEGER,
    CompletionTime INTEGER,
    DateAchieved DATETIME
);
```

### GameSessions Table (Optional Analytics)
```sql
CREATE TABLE GameSessions (
    Id INTEGER PRIMARY KEY,
    StartTime DATETIME,
    EndTime DATETIME,
    Player1Name TEXT,
    Player2Name TEXT,
    WinnerId TEXT
);
```