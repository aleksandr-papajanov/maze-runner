<p align="center">
  <img src="../../assets/logo.png" alt="Logo" width="100%" />
</p>

# 2.2 Funktionella Krav

## Översikt

Detta dokument definierar alla funktionella krav för MazeRunner-systemet. Kraven är härledda från intressentintervjuer och användarfallsanalys.

---

## Funktionella Krav

### Kärnspelmekanik

| ID | Namn | Beskrivning |
|---|---|---|
| FK001 | Två-spelares tävling | Två spelare tävlar samtidigt i samma labyrintinstans |
| FK002 | Nyckelsamling | Spelare måste hitta slumpmässigt placerad nyckel innan de når utgången |
| FK003 | Vinstvillkor | Första spelaren som når utgången med nyckeln vinner spelet |
| FK004 | Realtidssynkronisering | Positionssynkronisering <100ms latens |
| FK005 | QR-kodåtkomst | Spelare skannar kod för att gå med i spel inom max 1 minut |

### Förmågesystem

| ID | Namn | Beskrivning |
|---|---|---|
| FK006 | Sömneliksir | Fryser motståndaren i 2 sekunder, tvingar nyckelfall |
| FK007 | Förvirrningsstråle | Inverterar motståndarens joystick-kontroller (5s varaktighet, 15s nedladdning) |
| FK008 | Strategiska fällor | Kan placeras vid utgång eller nyckelplatser (30s timeout, 20s nedladdning) |
| FK009 | Bedövande projektiler | Synliga projektiler avfyrade mot motståndare (2s bedövning, 10s nedladdning) |
| FK010 | Blandat aktiveringssystem | Power-ups aktiveras automatiskt, strategiska föremål manuellt |
| FK011 | Tre förmågeknappar | Mobil (höger sida), tangentbordstangenter (JKL) på dator |
| FK012 | Begränsat inventory | Max 3 olika förmågetyper, påfylls efter användning |

### Labyrint

| ID | Namn | Beskrivning |
|---|---|---|
| FK013 | Fast labyrintlayout | Enda labyrintlayout med fast väggstruktur för konsekvens |
| FK014 | Slumpmässig kartgenerering | Randomisera nyckel, utgång och power-ups |
| FK015 | Begränsad viewport | Begränsad viewport per spelare (dimma av krig-effekt) |
| FK016 | Visuell feedback | Feedback för alla spelaraktioner och förmågeanvändning |
| FK017 | Automatisk spelavslutning | Spel avslutas efter vinst eller spelarurkoppling |

### Poängsystem

| ID | Namn | Beskrivning |
|---|---|---|
| FK018 | Poängsamlingsobjekt | Äpplen/mynt utspridda i labyrint för high score |
| FK019 | Bokstavssamlingsutmaning | Samla bokstäver för hemligt ord |
| FK020 | Tidsbaserad poängsättning | Snabbare genomförande ger högre poäng |
| FK021 | High score-topplista | Topp 10-poster och initialer |
| FK022 | Bonuspoängsystem | Sidoutmaningar samtidigt med huvudspel |

### Sessionshantering

| ID | Namn | Beskrivning |
|---|---|---|
| FK023 | 4 samtidiga sessioner | Stöd för 8 spelare totalt utan prestandaförsämring |
| FK024 | Automatisk matchmaking | Första tillgängliga spelare paras ihop |
| FK025 | Åskådarvy | Visar hela labyrinten och båda spelares positioner |
| FK026 | Lärare sessionväxling | Växla mellan olika aktiva spelsessioner på åskådardisplay |

### Kontroller och Gränssnitt

| ID | Namn | Beskrivning |
|---|---|---|
| FK027 | Enhetsanpassade kontroller | Anpassas till enhetstyp (touch-joystick vs tangentbord) |
| FK028 | Visuell spelardistinktion | Tydlig distinktion mellan spelaravatarer med riktningsindikatorer |
| FK029 | Spelstatusvisning | Timer, förmågor, poäng, inventory |
| FK030 | 4-riktningsrörelse | Uppför, ner, vänster, höger |
| FK031 | Mobilkontroller | Vänster tumme joystick, höger tumme förmågeknappar |
| FK032 | Skrivbordskontroller | WASD-rörelse, JKL-förmågeaktivering |

### Hjälpsystem

| ID | Namn | Beskrivning |
|---|---|---|
| FK033 | Kompasshjälpsystem | Efter 5 minuter, visa riktning till nyckel |
| FK034 | Viewport-rättvisa | Samma viewport-storlek oavsett enhetsskärmstorlek |
| FK035 | Hastighetsökning power-up | Aktiveras automatiskt vid upplockning |
| FK036 | Förbättrad syn power-up | Utökad synradie |
| FK037 | Resultatskärm | Vinnardeklaration, slutpoäng och tid |
| FK038 | Flexibla tidsgränser | 90% slutför inom 5 min, tillåt 7-8 min |

---

## Kravspårbarhet

### Användarfallsmappning

| Användarfall | Relaterade Funktionella Krav |
| ------------ | ---------------------------- |
| UC1: Anslut via QR-kod | FK005 |
| UC2: Navigera labyrint | FK001, FK013, FK014, FK015, FK030 |
| UC3: Samla nyckel | FK002, FK016 |
| UC4: Använd förmågor | FK006-FK012 |
| UC5: Nå utgång | FK003, FK017 |
| UC6: Visa poäng | FK018-FK022, FK029 |
| UC7: Starta session | FK023, FK024 |
| UC8: Övervaka spel | FK025 |
| UC9: Växla sessioner | FK026 |
| UC10: Hantera evenemang | FK023, FK024, FK026 |
| UC11: Titta på spel | FK025 |
| UC12: Matcha spelare | FK024 |
| UC13: Synkronisera tillstånd | FK004 |
| UC14: Hantera urkoppling | FK017 |
| UC15: Slumpa karta | FK014 |
| UC16: Spåra poäng | FK021 |

---

**Totalt**: 38 Funktionella Krav

För prioritering, Kostnad/Värde/Risk-analys och implementeringsplan, se [2.4 Användarkrav](acceptance-criteria.md).
