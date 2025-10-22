# 3.1.1 Klassdiagram

Statisk design - Compile-time klassstruktur.

## 3.1.1.1 Speldomän och Kärnmekanik

Detta diagram visar spelets huvudkomponenter och domänmodell:
- **Labyrintstruktur**: IMaze och IMazeCell hanterar spelets rutnät och väggar
- **Spelarsystem**: IPlayer med tillstånd (NORMAL, STUNNED, CONFUSED, SPEED_BOOSTED)
- **Samlarobjekt**: Nyckel, bonuspoäng, power-ups och förmågor
- **Förmågssystem**: StunShot, ConfusionBeam, SpeedBoost för spelare-mot-spelare interaktion

Designen använder interface-baserad arkitektur för flexibilitet och testbarhet.

![Class Diagram](/diagrams/3.1.1.1-class-diagram.png)
[View PlantUML source](/diagrams/3.1.1.1-class-diagram.puml)

## 3.1.1.2 Action Bus och Händelsesystem

Detta diagram visar event-driven kommunikationsarkitekturen:
- **IAction**: Bashändelse med SessionId, SenderId och Timestamp
- **Händelsetyper**: PlayerMove, AbilityUse, ItemCollect, SessionStateUpdate, etc.
- **Pub/Sub-mönster**: IActionPublisher publicerar händelser, IActionSubscriber prenumererar
- **Filtrering**: ActionFilter för att prenumerera på specifika sessioner/spelare/händelsetyper

Alla spelkomponenter kommunicerar via action bus för löst kopplad, utbyggbar arkitektur.

![Action Bus Diagram](/diagrams/3.1.1.2-class-bus-diagram.png)
[View PlantUML source](/diagrams/3.1.1.2-class-bus-diagram.puml)

## 3.1.1.3 Nätverksarkitektur och Sessionshantering

Detta diagram visar hur klienter ansluter och hur sessioner hanteras:
- **PlayerConnection**: Implementerar både IActionSubscriber och IActionPublisher för tvåvägskommunikation
- **SpectatorConnection**: Tar emot periodiska snapshots av alla aktiva sessioner för storsärm
- **IGameSession**: Varje 2-spelar-match har sin egen isolerade action bus
- **ISessionManager**: Hanterar skapande, matchmaking och rensning av sessioner

Spelare kommunicerar via sessionens action bus, medan åskådare får fullständiga snapshots centralt.

![Network Diagram](/diagrams/3.1.1.3-class-network-diagram.png)
[View PlantUML source](/diagrams/3.1.1.3-class-network-diagram.puml)

# 3.1.2 Moduldiagram - Systemarkitektur

Statisk design - Compile-time systemarkitektur och moduler.

## Övergripande Arkitektur
MazeRunner följer en **lager-baserad arkitektur** med centraliserad spellogik på servern. SignalR används som tunn transportadapter som delegerar till ConnectionManager.

## Systemlager

### **Client Layer (Browser)**
- **Player Client & Spectator Client**: React + TypeScript med WebSocket-kommunikation

### **Communication Layer**
- **SignalR Hub**: Tunn transportadapter som delegerar alla meddelanden till ConnectionManager
- **REST API**: Initial sessionhantering och high scores

### **Server Core Layer (C# ASP.NET Core)**
- **Game Controller**: Äger SessionManager och ConnectionManager
- **Session Manager**: Skapar och hanterar sessioner
- **Connection Manager**: Enda entry point för WebSocket-meddelanden, hanterar både spelare och åskådare
- **Game Logic**: Session, Maze Generator, Collision Detection, Win Condition
- **Connection Types**: PlayerConnection (bidirektionell), SpectatorConnection (mottagning)
- **Action Bus**: Pub/Sub-mönster, isolerad per session
- **Domain Model**: Player, Maze, Collectibles, Abilities

### **Persistence Layer**
- **SQLite Database**: Embedded databas för high scores och sessionshistorik

## Nyckelprinciper
- ConnectionManager är enda WebSocket entry point
- SignalR delegerar direkt till ConnectionManager (ingen affärslogik i Hub)
- Varje GameSession äger sin isolerade Action Bus
- PlayerConnection är både publisher och subscriber
- SpectatorConnection är endast subscriber

![Module Diagram](/diagrams/3.1.2-module-diagram.png)
[View PlantUML source](/diagrams/3.1.2-module-diagram.puml)