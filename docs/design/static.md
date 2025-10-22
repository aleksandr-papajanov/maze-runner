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
MazeRunner-systemet följer en **lager-baserad klient-server arkitektur** med centraliserad speltillståndshantering. All spellogik körs på en enda server för att säkerställa synkronisering och förhindra desync-problemen som upplevdes i tidigare projekt.

**Arkitekturmönster**: Klient-Server med WebSocket-kommunikation  
**Distributionsmodell**: Enkelserver-applikation som körs på laptop med webbaserade klienter

## Systemlager och Moduler

Detta diagram visar fyra huvudlager:

### **Layer 1: Client Layer (Browser)**
- **Player Client**: React-baserad spelklient med responsiv UI
  - Game Renderer: Canvas-baserad labyrintrendering med fog of war
  - Input Controller: Hanterar touch (joystick) och tangentbord (WASD)
  - UI Components: HUD, förmåga-knappar, poäng-display
  - WebSocket Client: SignalR-anslutning för realtidsuppdateringar

- **Spectator Client**: Åskådarvy som visar alla aktiva sessioner
  - Full Map Renderer: Ingen fog of war, visar fullständig labyrint
  - WebSocket Client: Tar emot periodiska snapshots

### **Layer 2: Communication Layer**
- **SignalR Hub**: WebSocket-server för bidirektionell realtidskommunikation
  - PlayerHub: Hanterar spelactions (move, ability use, collect)
  - SpectatorHub: Broadcastar snapshots till åskådare

- **REST API**: HTTP-endpoints för initial anslutning
  - `/sessions`: Join-or-create, session info
  - `/highscores`: Query och post high scores

### **Layer 3: Server Core Layer (C# ASP.NET Core)**
- **Game Controller**: Orchestrerar alla sessioner och anslutningar
  - Session Manager: Skapar, matchar och rensar sessioner
  - Connection Manager: Hanterar player connections och disconnects
  - Spectator Manager: Hanterar åskådare, broadcastar snapshots

- **Game Logic**: Kärnspelmekanik
  - Game Session: Äger sin egen Action Bus, hanterar 2 spelare
  - Maze Generator: Skapar randomiserade labyrinter
  - Collision Detection: Validerar rörelser, detekterar insamling
  - Win Condition: Kontrollerar om spelare nått utgång med nyckel

- **Action Bus**: Event-driven kommunikation (pub/sub-mönster)
  - Event Publisher: Publicerar IAction-händelser
  - Event Subscribers: Registrerar lyssnare med filter
  - Action Filter: Filtrerar på SessionId/PlayerId/ActionType
  - *Viktigt*: Varje session har sin egen isolerade action bus

- **Domain Model**: Spelentiteter
  - Player: Tillstånd, position, inventory, abilities
  - Maze & Cells: Labyrintstruktur, väggar, cells
  - Collectibles: Nyckel, bonuspoäng, power-ups
  - Abilities: Stun Shot, Confusion Beam, Speed Boost, Traps

### **Layer 4: Persistence Layer**
- **SQLite Database**: Embedded databas (ingen extern server)
  - High Scores: Spara vinnare och poäng
  - Session History: Logga sessioner för analys

## Kommunikationsflöden

**Spelare → Server:**
1. HTTP GET → REST API → GameController (join session)
2. WebSocket connect → SignalR PlayerHub
3. Game actions → PlayerHub → GameController → GameLogic
4. GameLogic publicerar till Action Bus
5. Action Bus notifierar subscribers (andra spelare i session)

**Server → Spelare:**
1. Action Bus event → PlayerConnection.OnEvent()
2. SignalR broadcast → WebSocket → Player Client
3. Client uppdaterar rendering

**Server → Åskådare:**
1. GameController.BroadcastAllSessionsToSpectators() (periodisk, t.ex. 100ms)
2. ISessionSnapshot för varje aktiv session
3. SignalR SpectatorHub → SpectatorConnection.ReceiveSnapshot()

## Teknisk Stack
- **Frontend**: React med TypeScript för responsivt UI
- **Backend**: C# med ASP.NET Core för spelserver
- **Kommunikation**: SignalR (WebSocket) för realtidsuppdateringar, REST API för initial anslutning
- **Databas**: SQLite för high scores och sessionsdata
- **Hosting**: Lokal server på laptop eller lättviktig molndistribution

![Module Diagram](/diagrams/3.1.2-module-diagram.png)
[View PlantUML source](/diagrams/3.1.2-module-diagram.puml)

## Distributionsarkitektur
- **Utveckling**: Lokal utvecklingsmiljö med React dev server och C# backend
- **Produktion**: Enkel körbar fil som kör både React build och C# server på demonstrations-laptop
- **Skalbarhet**: Enkelserver-instans designad för maximum 10 samtidiga spelare (5 sessioner)