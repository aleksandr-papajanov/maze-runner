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

# 3.1.2 Moduldiagram

Statisk design - Compile-time systemarkitektur och moduler.

## Övergripande Arkitektur
MazeRunner-systemet följer en klient-server arkitektur med centraliserad speltillståndshantering. All spellogik körs på en enda server för att säkerställa synkronisering och förhindra desync-problemen som upplevdes i tidigare projekt.

**Arkitekturmönster**: Klient-Server med WebSocket-kommunikation
**Distributionsmodell**: Enkelserver-applikation som körs på laptop med webbaserade klienter

## Teknisk Stack
- **Frontend**: React med TypeScript för responsivt UI
- **Backend**: C# med ASP.NET Core för spelserver
- **Kommunikation**: SignalR (WebSocket) för realtidsuppdateringar, REST API för initial anslutning
- **Databas**: SQLite för high scores och sessionsdata
- **Hosting**: Lokal server på laptop eller lättviktig molndistribution

*[PLACEHOLDER: Systemarkitekturdiagram som visar klient-server interaktion, WebSocket-anslutningar och komponentrelationer]*

## Distributionsarkitektur
- **Utveckling**: Lokal utvecklingsmiljö med React dev server och C# backend
- **Produktion**: Enkel körbar fil som kör både React build och C# server på demonstrations-laptop
- **Skalbarhet**: Enkelserver-instans designad för maximum 10 samtidiga spelare