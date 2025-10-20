# 3.2 Dynamisk Design (Runtime-beteende)

Dynamisk design - Run-time beteende, interaktioner och tillståndsövergångar.

## 3.2.1 Aktivitetsdiagram

### Förmågeanvändning och Stridsflöde

Aktivitetsdiagram som fokuserar på förmågessystemet: insamling, aktivering (auto vs manuell), cooldown-hantering och strategisk användning.

![Aktivitetsdiagram](/diagrams/3.2.1-activity-diagram.png)

## 3.2.2 Sekvensdiagram

### Spelflöde

Sekvensdiagram som visar flödet i multiplayer-spelet MazeRunner: sessionsskapande, spelartillträde, kontroll av beredskap, spelstart, spelhandlingar och spelavslut. Visar kommunikation mellan Spelare, Frontend, REST API, WebSocket, GameController, Databas och Admin.

![Sekvensdiagram](/diagrams/3.2.2-sequence-diagram.png)

## 3.2.3 Tillståndsdiagram

### Förmågetillstånd med Cooldown

Tillståndsdiagram som visar en förmågas tillståndscykel från tillgänglig till cooldown och tillbaka.

![Tillståndsdiagram](/diagrams/3.2.3-state-diagram.png)