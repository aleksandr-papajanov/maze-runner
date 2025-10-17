# 3.5 Datahantering

## Speltillståndslagring

### In-Memory Tillstånd (C# Server)
- Spelarpositioner och status
- Föremålspositioner och tillgänglighet  
- Speltiming och poänginformation
- Tillfälliga förmågeeffekter och cooldowns

### Beständig Lagring (SQLite)
- High score topplista (topp 10 poster)
- Spelkonfigurationsinställningar
- Användningsstatistik (valfritt)

## Datasynkroniseringsstrategi

### Auktoritativ Servermodell
- C# server upprätthåller enda källa till sanning för allt speltillstånd
- React-klienter skickar inmatningshändelser, inte tillståndsändringar
- Server validerar alla åtgärder innan ändringar tillämpas
- Optimistisk klient-sida prediktion för smidig rörelsekänsla
- Server korrigeringspaket för synkroniseringsfel

### Uppdateringsfrekvens
- Spelarpositioner: 20-30 uppdateringar per sekund via SignalR
- Spelhändelser: Omedelbar sändning
- Statusuppdateringar: 2-5 uppdateringar per sekund  
- Heartbeat/anslutningskontroll: Var 5:e sekund

## Databasschema (SQLite)

### HighScores Tabell
```sql
CREATE TABLE HighScores (
    Id INTEGER PRIMARY KEY,
    PlayerName TEXT,
    Score INTEGER,
    CompletionTime INTEGER,
    DateAchieved DATETIME
);
```

### GameSessions Tabell (Valfri Analys)
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