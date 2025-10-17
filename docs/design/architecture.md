# 3.1 Systemarkitektur

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