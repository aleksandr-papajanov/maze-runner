<p align="center">
  <img src="../../assets/logo.png" alt="Logo" width="100%" />
</p>

# 2.4 Användarkrav

## Användarkrav och Acceptanskriterier

Detta dokument beskriver användarkrav ur slutanvändarnas perspektiv samt acceptanskriterier för projektets framgång.

## Definition av Klart

För att projektet ska anses vara komplett måste följande kriterier uppfyllas:

### Minimum Viable Product (Väsentligt för Öppet Hus-framgång)

| Funktion | Beskrivning |
| -------- | ----------- |
| QR-kod åtkomst | Spelare kan skanna och ansluta inom 1 minut |
| Två spelare kan ansluta | Spelare kan ansluta till spel automatiskt |
| Realtid labyrintnavigering | Synkroniserade positioner för spelare |
| Nyckelsamling och utgång | Funktionell samling och aktivering |
| Åskådarvy | Visar komplett speltillstånd på separat skärm |
| Vinst/förlust | Villkor korrekt upptäckta och visade |
| Grundläggande visuell feedback | För spelaraktioner |
| Lärare sessionväxling | Mellan aktiva spel |

### Förbättrade Funktioner (Bra att Ha - Inte Väsentligt för MVP)

| Funktion | Beskrivning |
| -------- | ----------- |
| Förmågasystem | Sömnpotion, förvirringsstrål, projektiler, fällor |
| Manuell förmåga-aktivering | 3 knappar (mobil) eller JKL-tangenter (desktop) |
| 8-riktnings rörelse-stöd | För förbättrad navigering |
| Poängsamlingssystem | Äpplen/mynt för high score-spårning |
| Bokstavssamlings sidoutmaning | Hemligt ord-slutförande |
| High score topplista | Topp 10 med initialinmatning |
| Kompasshjälpsystem | Efter 5 minuter |
| Flexibla tidsgränser | 5 min mål, 7-8 min maximum |

### Framgångsmått för Öppet Hus-demonstration

| Mått | Mål |
| ---- | --- |
| Engagemang | 80%+ av tilltalade studenter villiga att prova spelet |
| Slutförande | 90%+ av påbörjade spel når naturlig slutsats inom 5-8 minuter |
| Teknisk tillförlitlighet | <5% av spel avslutade på grund av tekniska problem |
| Installationseffektivitet | Demonstration redo inom 2 minuter av ankomst till plats |
| Poängsystem | Spelare kan framgångsrikt ange initialer för high scores |
| Sidoutmaningar | Bokstavssamling och poängsystem fungerar korrekt |
| Sessionhantering | Lärare kan växla mellan spel utan tekniska problem |

---

## Kostnad/Värde/Risk Analys

Bedömningsskala:

| Bedömning | Beskrivning |
| ---------- | ----------- |
| Kostnad (Development Effort) | L: 1-4h, M: 5-12h, H: 13+h |
| Värde (Business Value) | L: Nice-to-have, M: Förbättrar UX, H: Kritisk för MVP |
| Risk (Technical Risk) | L: Väletablerad tech, M: Kräver integration, H: Komplex implementation |
| Prioritet | P1: Kritisk, P2: Hög, P3: Medel, P4: Låg |

### Kostnad/Värde/Risk Tabell - Funktionella Krav

| ID    | Namn                       | Beskrivning                                             | Kostnad | Värde | Risk | Beroenden            |
| ----- | -------------------------- | ------------------------------------------------------- | ------- | ----- | ---- | -------------------- |
| FK001 | Två-spelares tävling       | Två spelare ansluter och tävlar i samma labyrintinstans | H       | H     | M    | SK001, SK002, IFK002 |
| FK002 | Slumpmässig nyckel         | Nyckel spawnas på slumpmässig position                  | M       | H     | L    | FK001, FK014         |
| FK003 | Vinstvillkor               | Första spelare som når utgång med nyckel vinner         | M       | H     | L    | FK001, FK002         |
| FK004 | Realtidssynk <100ms        | WebSocket-baserad positionssynkronisering               | H       | H     | H    | SK002, IFK002, FK001 |
| FK005 | QR-kod åtkomst             | Spelare skannar QR-kod för att ansluta                  | M       | H     | L    | FK024, IFK014        |
| FK013 | Fast labyrintlayout        | En predefinerad labyrintstruktur                        | L       | H     | L    | FK001                |
| FK014 | Slumpmässig karta          | Randomisera nyckel, utgång och power-ups                | M       | H     | L    | FK002, FK013         |
| FK015 | Begränsad viewport         | Fog of war-effekt runt karaktär                         | M       | H     | M    | FK001, FK027         |
| FK016 | Visuell feedback           | Indikatorer för actions och effekter                    | M       | H     | L    | FK001, IFK018        |
| FK017 | Auto-avslutning            | Spel avslutas vid vinst/urkoppling                      | M       | H     | M    | FK003, IFK011        |
| FK023 | 4 samtidiga sessioner      | 8 spelare totalt utan prestandaförsämring               | H       | H     | M    | FK001, IFK003        |
| FK024 | Auto matchmaking           | Automatisk spelarparning                                | M       | H     | M    | FK001, FK005         |
| FK025 | Åskådarvy full karta       | Separat skärm med hela labyrinten                       | M       | H     | M    | FK001, AF003         |
| FK027 | Enhetsanpassade kontroller | Touchjoystick (mobil) vs tangentbord                    | M       | H     | M    | FK001, IFK006        |
| FK028 | Visuell distinktion        | Tydlig skillnad mellan spelaravatarer                   | M       | H     | L    | FK001, IFK020        |
| FK031 | Mobilkontroller            | Vänster joystick, höger förmågeknappar                  | M       | H     | M    | FK027, FK011         |
| FK032 | Desktop-kontroller         | WASD-rörelse, JKL-förmågor                              | L       | H     | L    | FK027, FK011         |

### Icke-Funktionella Krav - Risk Analys

| ID     | Namn                     | Beskrivning                                              | Kostnad | Värde | Risk | Beroenden |
| ------ | ------------------------ | -------------------------------------------------------- | ------- | ----- | ---- | --------- |
| IFK001 | Prestanda                | Systemet ska hantera 10 samtidiga spelare utan lagg      | H       | H     | M    | FK023     |
| IFK002 | Nätverkssynk             | Positionsuppdatering ska ske inom 100ms                  | H       | H     | H    | FK004     |
| IFK003 | Skalbarhet               | Backend ska stödja minst 5 aktiva sessioner              | M       | H     | M    | FK023     |
| IFK006 | Plattformskompatibilitet | Stöd för både desktop och mobil                          | M       | H     | M    | FK027     |
| IFK011 | Stabilitet               | Spel får inte krascha vid abrupt spelavslut              | M       | H     | M    | FK017     |
| IFK014 | Säker åtkomst            | QR-koden ska inte kunna utnyttjas flera gånger           | M       | H     | L    | FK005     |
| IFK018 | UI-responsivitet         | Feedback visas inom 50ms efter spelåtgärd                | M       | H     | M    | FK016     |
| IFK020 | Tillgänglighet           | Spelare ska kunna urskilja figurer även vid färgblindhet | L       | H     | L    | FK028     |

### Prioritetsgrupper och Implementeringsordning

| Sprint | Mål | Viktiga funktioner | Leverabler |
| ------ | --- | ---------------- | ---------- |
| Sprint 1 (P1) | Grundläggande spelbart system | SK001-003, FK001, FK002, FK003, FK004, FK005, FK013, FK014, FK015, FK016, FK017, FK023, FK024, FK025, FK027, FK028, FK031, FK032 | Fullt spelbart två-spelares labyrintspel med åskådarvy |
| Sprint 2 (P2) | Förmågasystem och UX | FK006-FK012, FK026, FK029, FK030, FK034, FK037 | Komplett förmågasystem och förbättrad UX |
| Sprint 3 (P3) | High scores och sidoutmaningar | FK008, FK018, FK020, FK021, FK033, FK035, FK036, FK038 | Komplett poängsystem och progression-mekaniker |
| Sprint 4 (P4) | Extra engagement-funktioner | FK019, FK022 | Bokstavssamlingsutmaning och bonuspoängsystem |

### Kritiska Beroendevägar

| Kedja | Sekvens | Kommentar |
| ------ | ------- | --------- |
| Kärnspelmekanik | SK001 → SK002 → FK001 → FK013 → FK027 → FK002 → FK003 | Måste slutföras sekventiellt för spelbar MVP |
| Realtidssynkronisering | SK002 → FK004 → IFK002 → FK015 → FK025 | IFK002 är hög risk, kräver performance tuning |
| Förmågasystem | FK010 → FK011 → FK012 → FK006/FK007/FK008/FK009 | Individuella förmågor kan utvecklas parallellt efter FK010-FK012 |
| Poängsystem | FK018 → FK020 → FK021 → FK019 → FK022 | Valfri kedja, kan skippas för snabbare release |

### Riskminimeringsstrategi

| Risk | Mitigation | Fallback | Test/Dependency |
| ---- | ---------- | -------- | --------------- |
| IFK002 - Latens <100ms | WebSocket optimering, server-side prediction | Acceptera 100-150ms | Sprint 1, kontinuerlig performance monitoring |
| FK004 - Realtidssynkronisering | Använd beprövad SignalR library | Reducera frekvens till 30Hz | Blockerar FK023 (5 sessioner) |
| IFK006 - Äldre smartphones | Progressiv enhansering, test på äldre enheter | Dokumentera minimum krav (Android 8+, iOS 13+) | Tidigt i Sprint 1 |
| IFK011 - Graciell urkoppling | Heartbeat och timeout-logik | Hårt avslut | Simulera nätverksavbrott |

### Kostnad-Effektivitetsanalys

| Typ | Exempel | Rekommendation |
| --- | ------- | -------------- |
| Högvärde/Låg-kostnad | FK013, FK028, FK030, FK018 | Implementera först eller tidigt |
| Högvärde/Hög-kostnad | FK001, FK004, FK023 | Kritiska investeringar, måste göras |
| Lågvärde/Hög-kostnad | FK019, FK022 | P4, endast om tid |

### Sammanfattning och Rekommendationer

- **Kritisk väg till MVP (8 timmar)**: Arkitektur & WebSocket → Två-spelares kontroller → Labyrint & nyckel & vinst → Synkronisering & åskådarvy  
- **Riskhantering**: Fokusera 40% av utvecklingstiden på IFK002 och FK004; testa äldre enheter; implementera error handling & reconnection  
- **Resursoptimering**: 2 utvecklare × 8 timmar = 16 persontimmar; Sprint 1 (MVP) = 12h, Sprint 2 (Förmågor) = 3h, Sprint 3 (Poäng) = 1h  
- **Framgångskriterier**: Minst FK001-FK005, FK013-FK017, FK023-FK025, FK027-FK028, FK031-FK032 implementerade; IFK002 <100ms; IFK010 99% drifttid; FK026 implementerat