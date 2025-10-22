<p align="center">
  <img src="../../assets/logo.png" alt="Logo" width="100%" />
</p>

# 3.2 Dynamisk Design (Runtime-beteende)

Dynamisk design - Run-time beteende, interaktioner och tillståndsövergångar.

## 3.2.1 Aktivitetsdiagram - Spelcykel från Start till Vinst

Detta aktivitetsdiagram visar hela spelflödet för MazeRunner:

**Fas 1: Nyckel-sökning**
- Spelare utforskar labyrinten med fog of war (begränsad sikt)
- Strategiskt val: Jaga nyckel direkt eller hindra motståndare
- Förmågor används taktiskt för att stoppa motståndare från att plocka upp nyckel
- Efter 5 minuter: Kompass aktiveras för att visa riktning till nyckel

**Fas 2: Slutspel med nyckel**
- **Nyckelinnehavare**: Väljer strategi (direkt till utgång vs samla bonuspoäng)
- **Motståndare**: Väljer strategi (campa vid utgång vs jaga aktivt)
- Parallella flöden visar båda spelares perspektiv samtidigt
- Risk/reward-balans: Samla mer poäng = högre risk att förlora nyckel

**Vinstvillkor**: Första spelare som når utgången med nyckeln vinner

[![Aktivitetsdiagram](/diagrams/3.2.1-activity-diagram.png)](/diagrams/3.2.1-activity-diagram.png)

<p align="center">
  <a href="/diagrams/3.2.1-activity-diagram.puml">View PlantUML source</a>
</p>

## 3.2.2 Sekvensdiagram - Multiplayer-sessionslivscykel

Detta sekvensdiagram visar kommunikationsflödet mellan alla systemkomponenter:

**Fas 1: Lobby & Matchmaking (0-30 sekunder)**
- Spelare ansluter via REST API: `POST /sessions/join-or-create`
- System skapar ny session eller hittar öppen session
- WebSocket-anslutning etableras för realtidskommunikation

**Fas 2: Beredskapscheck**
- System väntar på minst 2 spelare
- Alternative flow: Admin kan tvinga start med färre spelare (för demo)
- Broadcast: "AboutToStart" till alla anslutna klienter

**Fas 3: Bekräftelse & Nedräkning**
- Alla spelare måste bekräfta beredskap
- 5-sekunders nedräkning visas
- Database sparar spel-start

**Fas 4: Aktivt Spel (3-5 minuter)**
- Parallell kommunikation: Flera spelare skickar actions samtidigt
- GameController processar actions och broadcastar state updates
- Kontinuerlig check av vinstvillkor

**Fas 5: Avslut**
- Spara slutresultat i databas
- Visa vinnare och highscores
- Session rensas

[![Sekvensdiagram](/diagrams/3.2.2-sequence-diagram.png)](/diagrams/3.2.2-sequence-diagram.png)

<p align="center">
  <a href="/diagrams/3.2.2-sequence-diagram.puml">View PlantUML source</a>
</p>

## 3.2.3 Tillståndsdiagram - Förmågas Livscykel

Detta tillståndsdiagram visar hur förmågor och power-ups fungerar genom hela sin livscykel:

**Insamlingsfas**
- `NotCollected → Collected`: Spelare plockar upp förmåga från labyrinten

**Aktiveringstyper**
- **Auto-aktivering** (t.ex. Speed Boost): Aktiveras direkt vid insamling, tidsbaserad effekt
- **Manuell aktivering** (t.ex. Stun Shot, Confusion Beam): Sparas tills spelare trycker på knapp

**Effekttyper**
- `OpponentStunned`: Fryser motståndare i 2 sekunder, tappar nyckel
- `OpponentConfused`: Inverterar kontroller i 5 sekunder
- `TrapPlaced`: Sätter fälla som aktiveras när motståndare går över

**Cooldown-hantering**
- Efter användning går förmågan i cooldown
- UI visar progress (grå knapp med timer)
- Olika cooldown-tider beroende på förmågans kraft:
  - Stun Shot: 10s
  - Confusion Beam: 15s
  - Trap: 20s
- När cooldown slutar blir förmågan tillgänglig igen

[![Tillståndsdiagram](/diagrams/3.2.3-state-diagram.png)](/diagrams/3.2.3-state-diagram.png)

<p align="center">
  <a href="/diagrams/3.2.3-state-diagram.puml">View PlantUML source</a>
</p>