# 3.3 Dynamisk Design (Runtime-beteende)

## Nyckel Beteendemönster

### Spelsession Livscykel
```
Väntar → Aktiv → Pausad → Avslutad → Upprensning
```

### Spelaranslutningsstatus  
```
Ansluter → Redo → Spelar → Urkopplad
```

### Föremålsanvändningsflöde
```
Tillgänglig → Samlad → Aktiverad → Effekt Tillämpad → Cooldown → Tillgänglig
```

*[PLACEHOLDER: Aktivitetsdiagram som visar komplett spelsessionsflöde från spelaranslutning till spelslutförande]*

*[PLACEHOLDER: Sekvensdiagram som visar realtid spelarrörelsessynkronisering mellan klienter och server]*

*[PLACEHOLDER: Tillståndsdiagram som visar spelsessionsstatus och övergångar]*

## Kritiska Interaktioner

### Realtid Rörelsesynkronisering
1. Spelarinmatning upptäckt i React-komponent
2. Rörelsebegäran skickad till C# server via SignalR
3. Server validerar rörelse mot labyrintgränser och spelregler
4. Server uppdaterar spelarposition i speltillstånd
5. Server sänder positionsuppdatering till alla klienter i session via SignalR
6. React-komponenter renderar uppdaterade positioner smidigt

### Förmågeanvändningssekvens  
1. Spelare aktiverar förmåga via React UI-knapp
2. Klient skickar förmågebegäran med mål/riktning till C# server
3. Server validerar förmågotillgänglighet och cooldown-status
4. Server bearbetar förmågeeffekt (t.ex. bedova motståndare, tappa nyckel)
5. Server uppdaterar berörda spelares tillstånd
6. Server sänder förmågeanimation och effekter via SignalR
7. React-komponenter visar visuell feedback och uppdaterar UI i enlighet