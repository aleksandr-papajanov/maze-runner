<p align="center">
  <img src="../../assets/logo.png" alt="Logo" width="100%" />
</p>

# 2.2 Funktionella Krav

## Översikt

Detta dokument definierar alla funktionella krav för MazeRunner-systemet, organiserade efter kategori och prioritet. Kraven är härledda från intressentintervjuer och användarfallsanalys.

---

## Grundläggande Spelmekanik (Måste Ha - P1)

| ID | Krav | Prioritet | Anteckningar |
| --- | ----------- | -------- | ----- |
| **FK001** | Två spelare tävlar samtidigt i samma labyrintinstans | P1 | Grundläggande flerspelarmekanik |
| **FK002** | Spelare måste hitta slumpmässigt placerad nyckel innan de når utgången | P1 | Primärt spelmål |
| **FK003** | Första spelaren som når utgången med nyckeln vinner spelet | P1 | Vinstvillkor |
| **FK004** | Realtidssynkronisering av spelarpositioner (<100ms latens) | P1 | Kritiskt för rättvist spel |
| **FK005** | QR-kodåtkomst - spelare skannar kod för att gå med i spel inom max 1 minut | P1 | Primär åtkomstmetod |

---

## Förmågesystem (Bör Ha - P2)

| ID | Krav | Prioritet | Anteckningar |
| --- | ----------- | -------- | ----- |
| **FK006** | Sömneliksir - fryser motståndaren i 2 sekunder, tvingar nyckelfall | P2 | Taktisk förmåga |
| **FK007** | Förvirrningsstråle - inverterar motståndarens joystick-kontroller (vänster blir höger) | P2 | 5s varaktighet, 15s nedladdning |
| **FK008** | Strategiska fällor - kan placeras vid utgång eller nyckelplatser | P2 | 30s timeout, 20s nedladdning |
| **FK009** | Bedövande projektiler - synliga projektiler avfyrade mot motståndare | P2 | 2s bedövning, 10s nedladdning |
| **FK010** | Blandat aktiveringssystem - power-ups aktiveras automatiskt vid upplockning, strategiska föremål använder manuella knappar | P2 | UX-designbeslut |
| **FK011** | Tre förmågeknappar på mobil (höger sida), tangentbordstangenter (JKL) på dator | P2 | Multiplattformskontroller |
| **FK012** | Begränsat inventory - max 3 olika förmågetyper, påfylls efter användning eller samlas i labyrint | P2 | Resurshantering |

---

## Spelinnehåll (Måste Ha - P1)

| ID | Krav | Prioritet | Anteckningar |
| --- | ----------- | -------- | ----- |
| **FK013** | Enda labyrintlayout med fast väggstruktur för konsekvens | P1 | Minskar komplexitet |
| **FK014** | Slumpmässig kartgenerering - slumpa nyckelplacering, utgångsposition och power-up positioner varje spel | P1 | Repeterbarhet |
| **FK015** | Begränsad viewport per spelare (dimma av krig-effekt) | P1 | Strategiskt element |
| **FK016** | Visuell feedback för alla spelaraktioner och förmågeanvändning | P1 | Användarupplevelse |
| **FK017** | Automatisk spelavslutning efter vinst eller spelarurkoppling | P1 | Sessionshantering |

---

## Poängsättning och Sidoutmaningar (Bör Ha - P3)

| ID | Krav | Prioritet | Anteckningar |
| --- | ----------- | -------- | ----- |
| **FK018** | Poängsamlingsobjekt (äpplen/mynt) utspridda i labyrint för high score | P3 | Valfritt engagemang |
| **FK019** | Bokstavssamlingsutmaning - samla bokstäver för att stava hemligt ord för bonuspriser | P3 | Sidouppdrag |
| **FK020** | Tidsbaserad poängsättning - snabbare genomförande ger högre poäng | P3 | Tävlingselement |
| **FK021** | High score-topplista med topp 10-poster och initialer (flipperspelsstil) | P3 | Persistens |
| **FK022** | Bonuspoängsystem för att slutföra sidoutmaningar samtidigt som man vinner huvudspel | P3 | Belöningssystem |

---

## Flerspelarstöd (Måste Ha - P1)

| ID | Krav | Prioritet | Anteckningar |
| --- | ----------- | -------- | ----- |
| **FK023** | Stöd för 4 samtidiga spelsessioner (8 spelare totalt) | P1 | Evenemangskarav |
| **FK024** | Automatisk matchmaking - första tillgängliga spelare paras ihop med nästa anslutande spelare | P1 | Förenklad UX |
| **FK025** | Åskådarvy visar hela labyrinten och båda spelarnas positioner på separat skärm | P1 | Publikengagemang |
| **FK026** | Lärare kan växla mellan olika aktiva spelsessioner på åskådardisplay | P1 | Evenemangshantering |

---

## Användargränssnitt (Måste Ha - P1)

| ID | Krav | Prioritet | Anteckningar |
| --- | ----------- | -------- | ----- |
| **FK027** | Kontroller anpassas till enhetstyp (touch-joystick vs tangentbord) | P1 | Multiplattform |
| **FK028** | Tydlig visuell distinktion mellan spelaravatarer med riktningsindikatorer | P1 | Tydlighet |
| **FK029** | Spelstatusvisning (timer, förmågor, poäng, inventory) | P1 | Informationsdesign |
| **FK030** | 8-riktningsrörelse (inte bara 4-riktningar) | P1 | Smidig navigering |
| **FK031** | Mobilkontroller - vänster tumme joystick, höger tumme förmågeknappar | P1 | Mobil UX |
| **FK032** | Skrivbordskontroller - WASD-rörelse, JKL-förmågeaktivering | P1 | Skrivbords-UX |
| **FK033** | Kompasshjälpsystem - efter 5 minuter, visa riktning till nyckel eller motståndare | P1 | Förhindrar frustration |
| **FK034** | Viewport-rättvisa - samma viewport-storlek oavsett enhetsskärmstorlek för rättvist spel | P1 | Tävlingsbalans |

---

## Valfria Funktioner (Kan Ha - P4)

| ID | Krav | Prioritet | Anteckningar |
| --- | ----------- | -------- | ----- |
| **FK035** | Hastighetsökning power-up (aktiveras automatiskt vid upplockning) | P4 | Förbättring |
| **FK036** | Förbättrad syn power-up (utökad synradie) | P4 | Strategiskt alternativ |
| **FK037** | Resultatskärm efter spel med vinnardeklaration, slutpoäng och tid | P4 | Polering |
| **FK038** | Flexibla tidsgränser - 90% slutför inom 5 minuter, tillåt 7-8 minuter för återstående 10% | P4 | UX-övervägande |

---

## Kravspårbarhet

### Användarfallsmappning

| Användarfall | Relaterade Funktionella Krav |
| -------- | ------------------------------ |
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

## Prioritetssammanfattning

- **P1 (Måste Ha)**: 24 krav - Väsentligt för MVP
- **P2 (Bör Ha)**: 7 krav - Förmågesystem (förbättrar spelet)
- **P3 (Kan Ha)**: 5 krav - Poängsystem (tillför djup)
- **P4 (Trevligt att Ha)**: 2 krav - Poleringsfunktioner

**Totalt**: 38 Funktionella Krav

För detaljerad Kostnad/Värde/Risk-analys och implementeringsplan, se [2.4 Användarkrav](acceptance.md).
