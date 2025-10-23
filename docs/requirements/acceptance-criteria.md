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
| 4-riktnings rörelse-stöd | För enkel navigering |
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
| Kostnad (Development Effort) | L: 1, M: 2, H: 3 |
| Värde (Business Value) | L: 1, M: 2, H: 3 |
| Risk (Technical Risk) | L: 1, M: 2, H: 3 |
| KVR Score | Kostnad × Värde × Risk (1-27) |
| Prioritet | Baserad på KVR: 12-27=P1, 6-9=P2, 3-4=P3, 1-2=P4 |

### Kostnad/Värde/Risk Tabell - Funktionella Krav

| ID | Namn | Beskrivning | Kostnad | Värde | Risk | KVR | Prioritet | Beroenden |
|---|---|---|---|---|---|---|---|---|
| FK001 | Två-spelares tävling | Två spelare ansluter och tävlar i samma labyrintinstans | H(3) | H(3) | M(2) | 18 | P1 | IFK002 |
| FK002 | Slumpmässig nyckel | Nyckel spawnas på slumpmässig position | M(2) | H(3) | L(1) | 6 | P2 | FK001, FK014 |
| FK003 | Vinstvillkor | Första spelare som når utgång med nyckel vinner | M(2) | H(3) | L(1) | 6 | P2 | FK001, FK002 |
| FK004 | Realtidssynk <100ms | WebSocket-baserad positionssynkronisering | H(3) | H(3) | H(3) | 27 | P1 | IFK002, IFK028, FK001 |
| FK005 | QR-kod åtkomst | Spelare skannar QR-kod för att ansluta | M(2) | H(3) | L(1) | 6 | P2 | FK024, IFK014 |
| FK006 | Sömneliksir | Fryser motståndaren i 2 sekunder, tvingar nyckelfall | M(2) | M(2) | L(1) | 4 | P3 | FK010, FK011 |
| FK007 | Förvirrningsstråle | Inverterar motståndarens joystick-kontroller | M(2) | M(2) | L(1) | 4 | P3 | FK010, FK011 |
| FK008 | Strategiska fällor | Kan placeras vid utgång eller nyckelplatser | M(2) | M(2) | L(1) | 4 | P3 | FK010, FK011 |
| FK009 | Bedövande projektiler | Synliga projektiler avfyrade mot motståndare | M(2) | M(2) | L(1) | 4 | P3 | FK010, FK011 |
| FK010 | Blandat aktiveringssystem | Power-ups aktiveras automatiskt, strategiska manuellt | M(2) | M(2) | L(1) | 4 | P3 | FK011, FK012 |
| FK011 | Tre förmågeknappar | Mobil (höger sida), tangentbord (JKL) | M(2) | M(2) | M(2) | 8 | P2 | FK027 |
| FK012 | Begränsat inventory | Max 3 olika förmågetyper, påfylls efter användning | M(2) | M(2) | L(1) | 4 | P3 | FK010 |
| FK013 | Fast labyrintlayout | En predefinerad labyrintstruktur | L(1) | H(3) | L(1) | 3 | P3 | FK001 |
| FK014 | Slumpmässig karta | Randomisera nyckel, utgång och power-ups | M(2) | H(3) | L(1) | 6 | P2 | FK002, FK013 |
| FK015 | Begränsad viewport | Fog of war-effekt runt karaktär | M(2) | H(3) | M(2) | 12 | P1 | FK001, FK027 |
| FK016 | Visuell feedback | Indikatorer för actions och effekter | M(2) | H(3) | L(1) | 6 | P2 | FK001, IFK018 |
| FK017 | Auto-avslutning | Spel avslutas vid vinst/urkoppling | M(2) | H(3) | M(2) | 12 | P1 | FK003, IFK011 |
| FK018 | Poängsamlingsobjekt | Äpplen/mynt utspridda i labyrint för high score | M(2) | L(1) | L(1) | 2 | P4 | FK020, FK021 |
| FK019 | Bokstavssamling | Samla bokstäver för hemligt ord | M(2) | L(1) | L(1) | 2 | P4 | FK018 |
| FK020 | Tidsbaserad poängsättning | Snabbare genomförande ger högre poäng | L(1) | L(1) | L(1) | 1 | P4 | FK003 |
| FK021 | High score-topplista | Topp 10-poster och initialer | M(2) | L(1) | L(1) | 2 | P4 | FK018, FK020 |
| FK022 | Bonuspoängsystem | För sidoutmaningar samtidigt med huvudspel | M(2) | L(1) | L(1) | 2 | P4 | FK018, FK019 |
| FK023 | 4 samtidiga sessioner | 8 spelare totalt utan prestandaförsämring | H(3) | H(3) | M(2) | 18 | P1 | FK001, IFK003 |
| FK024 | Auto matchmaking | Automatisk spelarparning | M(2) | H(3) | M(2) | 12 | P1 | FK001, FK005 |
| FK025 | Åskådarvy full karta | Separat skärm med hela labyrinten | M(2) | H(3) | M(2) | 12 | P1 | FK001 |
| FK026 | Lärare sessionväxling | Växla mellan olika aktiva spelsessioner | M(2) | H(3) | L(1) | 6 | P2 | FK023, FK025 |
| FK027 | Enhetsanpassade kontroller | Touchjoystick (mobil) vs tangentbord | M(2) | H(3) | M(2) | 12 | P1 | FK001, IFK006 |
| FK028 | Visuell distinktion | Tydlig skillnad mellan spelaravatarer | M(2) | H(3) | L(1) | 6 | P2 | FK001, IFK020 |
| FK029 | Spelstatusvisning | Timer, förmågor, poäng, inventory | M(2) | M(2) | L(1) | 4 | P3 | FK001 |
| FK030 | 4-riktningsrörelse | Uppför, ner, vänster, höger | L(1) | H(3) | L(1) | 3 | P3 | FK001, FK027 |
| FK031 | Mobilkontroller | Vänster joystick, höger förmågeknappar | M(2) | H(3) | M(2) | 12 | P1 | FK027, FK011 |
| FK032 | Desktop-kontroller | WASD-rörelse, JKL-förmågor | L(1) | H(3) | L(1) | 3 | P3 | FK027, FK011 |
| FK033 | Kompasshjälpsystem | Efter 5 minuter, visa riktning till nyckel | M(2) | M(2) | L(1) | 4 | P3 | FK002 |
| FK034 | Viewport-rättvisa | Samma viewport-storlek oavsett enhetsskärmstorlek | M(2) | H(3) | M(2) | 12 | P1 | FK015, FK027 |
| FK035 | Hastighetsökning power-up | Aktiveras automatiskt vid upplockning | L(1) | L(1) | L(1) | 1 | P4 | FK010 |
| FK036 | Förbättrad syn power-up | Utökad synradie | L(1) | L(1) | L(1) | 1 | P4 | FK015, FK010 |
| FK037 | Resultatskärm | Vinnardeklaration, slutpoäng och tid | M(2) | M(2) | L(1) | 4 | P3 | FK003, FK020 |
| FK038 | Flexibla tidsgränser | 90% slutför inom 5 min, tillåt 7-8 min | L(1) | M(2) | L(1) | 2 | P4 | FK004, IFK004 |

### Kostnad/Värde/Risk Tabell - Icke-Funktionella Krav

| ID | Namn | Beskrivning | Kostnad | Värde | Risk | KVR | Prioritet | Beroenden |
| ------ | ---------------------------- | ------------------------------------------------------------ | ------- | ----- | ---- | --- | --------- | ------------- |
| IFK001 | Snabb installation | Spelinstallationstid från laptop-uppstart <2 minuter | M(2) | H(3) | L(1) | 6 | P2 | IFK029 |
| IFK002 | Låg latens | Spelarrörelsens svarstid <100ms | H(3) | H(3) | H(3) | 27 | P1 | FK004, IFK028 |
| IFK003 | Kapacitet | Stöd för 4 samtidiga sessioner (8 spelare) | M(2) | H(3) | M(2) | 12 | P1 | FK023 |
| IFK004 | Speltid | 90% av spelen slutförs inom 5 minuter | L(1) | M(2) | L(1) | 2 | P4 | FK038 |
| IFK005 | Kompassaktivering | Kompasshjälpsystem aktiveras automatiskt efter 5 minuter | L(1) | M(2) | L(1) | 2 | P4 | FK033 |
| IFK006 | Enhetskompatibilitet | Fungera på smartphones 6+ år gamla (Android 7+, iOS 12+) | M(2) | H(3) | H(3) | 18 | P1 | FK027 |
| IFK007 | Webbläsarkompatibilitet | Kompatibel med Chrome, Firefox, Safari, Edge | M(2) | H(3) | M(2) | 12 | P1 | IFK032 |
| IFK008 | Responsiv viewport | Konsekvent viewport-skalning (4" till 27" skärmar) | M(2) | H(3) | M(2) | 12 | P1 | FK034 |
| IFK009 | Friktionsfri åtkomst | Ingen appinstallation krävs - endast webbläsaråtkomst | L(1) | H(3) | L(1) | 3 | P3 | FK005 |
| IFK010 | Drifttid | 99% drifttid under 3-timmars Öppet Hus-perioder | M(2) | H(3) | M(2) | 12 | P1 | IFK011 |
| IFK011 | Graciös felhantering | Graciös hantering av spelarurkopplingar utan systemkrasch | M(2) | H(3) | H(3) | 18 | P1 | FK017 |
| IFK012 | Återanslutning | Automatisk spelåterhämtning efter tillfälliga nätverksavbrott| H(3) | M(2) | H(3) | 18 | P1 | IFK011 |
| IFK013 | Dataintegritet | Ingen dataförlust i normala urkopplingsscenarier | M(2) | M(2) | M(2) | 8 | P2 | IFK011 |
| IFK014 | Snabb onboarding | Nya spelare kan börja spela inom 30 sekunder | L(1) | H(3) | L(1) | 3 | P3 | FK005 |
| IFK015 | Intuitiv design | Spelregler förståeliga utan textinstruktioner | M(2) | H(3) | M(2) | 12 | P1 | IFK022 |
| IFK016 | Engagerande åskådarvy | Åskådarvy engagerande för icke-spelande publik | M(2) | M(2) | L(1) | 4 | P3 | FK025 |
| IFK017 | High score-inmatning | High score-inmatningssystem med initialer (flipperspelsstil) | M(2) | L(1) | L(1) | 2 | P4 | FK021 |
| IFK018 | Tydlig feedback | Tydlig visuell feedback för all förmågeanvändning | M(2) | H(3) | M(2) | 12 | P1 | FK016 |
| IFK019 | Sessionshantering | Lärare kan enkelt växla mellan aktiva spelsessioner | L(1) | M(2) | L(1) | 2 | P4 | FK026 |
| IFK020 | Multimodal design | Olika avatarformer och mönster (inte bara färger) | M(2) | H(3) | L(1) | 6 | P2 | FK028 |
| IFK021 | Högkontrast design | Högkontrast visuell design för synlighet i bullrig miljö | M(2) | H(3) | L(1) | 6 | P2 | IFK020 |
| IFK022 | Ikonbaserat UI | Primärt visuella instruktioner snarare än textbaserad | M(2) | H(3) | L(1) | 6 | P2 | IFK015 |
| IFK023 | Visuell distinktion | Tydlig distinktion genom form, färg och mönster | M(2) | H(3) | L(1) | 6 | P2 | IFK020, FK028 |
| IFK024 | Bakgrundsmusik | Bakgrundsmusik ej nödvändig (bullrig demonstrationsmiljö) | L(1) | L(1) | L(1) | 1 | P4 | - |
| IFK025 | Ljudeffekter | Ljudeffekter sekundär prioritet - visuell feedback är primär | L(1) | L(1) | L(1) | 1 | P4 | - |
| IFK026 | Valfritt ljud | Valfria ljudeffekter för handlingar (får ej vara väsentliga) | L(1) | L(1) | L(1) | 1 | P4 | - |
| IFK027 | Serverarkitektur | Klient-server-arkitektur med centraliserad speltillstånd | M(2) | H(3) | L(1) | 6 | P2 | IFK028 |
| IFK028 | WebSocket-kommunikation | WebSocket-kommunikation (SignalR) för realtidsuppdateringar | M(2) | H(3) | M(2) | 12 | P1 | IFK002 |
| IFK029 | Enkel serverdistribution | Enkel serverdistribution på standard laptop-hårdvara | L(1) | H(3) | L(1) | 3 | P3 | IFK001 |
| IFK030 | Minimala beroenden | Minimala externa beroenden (React + C#) | L(1) | H(3) | L(1) | 3 | P3 | IFK032 |
| IFK031 | Anonym åtkomst | Ingen autentisering eller användarregistrering | L(1) | H(3) | L(1) | 3 | P3 | FK005 |
| IFK032 | Teknologistack | React-frontend med C# ASP.NET Core-backend | M(2) | H(3) | L(1) | 6 | P2 | IFK030 |

---

## Prioritetssammanfattning

### Funktionella Krav
- **P1 (Måste Ha)**: 24 krav - Väsentligt för MVP (FK001-FK005, FK013-FK017, FK023-FK034)
- **P2 (Bör Ha)**: 7 krav - Förmågesystem (FK006-FK012)
- **P3 (Kan Ha)**: 5 krav - Poängsystem (FK018-FK022)
- **P4 (Trevligt att Ha)**: 2 krav - Poleringsfunktioner (FK035-FK038)

**Totalt**: 38 Funktionella Krav

### Icke-Funktionella Krav
- **P1 (Måste Ha)**: 21 krav - Kärnprestanda, kompatibilitet, tillförlitlighet och UX (IFK001-IFK003, IFK006-IFK011, IFK014-IFK015, IFK018, IFK020-IFK023, IFK027-IFK032)
- **P2 (Bör Ha)**: 6 krav - Förbättrad användarupplevelse och återhämtning (IFK004-IFK005, IFK012-IFK013, IFK016, IFK019)
- **P3 (Kan Ha)**: 1 krav - High score-funktion (IFK017)
- **P4 (Trevligt att Ha)**: 4 krav - Ljudfunktioner (IFK024-IFK026)

**Totalt**: 32 Icke-Funktionella Krav

---

### Prioritetsgrupper och Implementeringsordning

| Sprint | Mål | Viktiga funktioner | Leverabler |
|---|---|---|---|
| Sprint 1 (P1) | Grundläggande spelbart system | FK001-FK005, FK013-FK017, FK023-FK034, IFK001-IFK003, IFK006-IFK011, IFK014-IFK015, IFK018, IFK020-IFK023, IFK027-IFK032 | Fullt spelbart två-spelares labyrintspel med åskådarvy |
| Sprint 2 (P2) | Förmågesystem och UX | FK006-FK012, FK026, FK029, IFK004-IFK005, IFK012-IFK013, IFK016, IFK019 | Komplett förmågesystem och förbättrad UX |
| Sprint 3 (P3) | High scores och sidoutmaningar | FK018-FK022, IFK017 | Komplett poängsystem och progression-mekaniker |
| Sprint 4 (P4) | Extra engagement-funktioner | FK035-FK038, IFK024-IFK026 | Power-ups, resultatskärm och ljudfunktioner |

### Kritiska Beroendevägar

| Kedja | Sekvens | Kommentar |
|---|---|---|
| Kärnspelmekanik | FK001 → FK013 → FK027 → FK002 → FK003 | Måste slutföras sekventiellt för spelbar MVP |
| Realtidssynkronisering | FK004 → IFK002 → IFK028 → FK015 → FK025 | IFK002 är hög risk, kräver performance tuning |
| Förmågesystem | FK010 → FK011 → FK012 → FK006/FK007/FK008/FK009 | Individuella förmågor kan utvecklas parallellt efter FK010-FK012 |
| Poängsystem | FK018 → FK020 → FK021 → FK019 → FK022 | Valfri kedja, kan skippas för snabbare release |
| Sessionshantering | FK023 → FK024 → FK025 → FK026 | Kritiskt för Öppet Hus-demonstration |

---

## Riskbedömningssammanfattning

### Högrisk-krav (Kräver omfattande testning)

**Funktionella Krav:**
- **FK004**: Realtidssynkronisering <100ms latens (nätverkskvalitet, äldre enheter, komplex implementation)

**Icke-Funktionella Krav:**
- **IFK002**: <100ms latens (nätverkskvalitet, äldre enheter)
- **IFK006**: 6+ år gammalt enhetsstöd (begränsad testmöjlighet)
- **IFK011**: Graciös urkopplingshantering (komplexa kantfall)
- **IFK012**: Automatisk återhämtning (robust tillståndshantering)

### Medelrisk-krav (Kräver noggrann design)

**Funktionella Krav:**
- **FK001**: Två-spelares tävling (grundläggande flerspelarmekanik)
- **FK015**: Begränsad viewport (fog of war-implementation)
- **FK017**: Automatisk spelavslutning (sessionshantering)
- **FK023**: 4 samtidiga sessioner (serverlasttestning)
- **FK024**: Automatisk matchmaking (spelarparningslogik)
- **FK025**: Åskådarvy full karta (synkronisering)
- **FK027**: Enhetsanpassade kontroller (multiplattform UX)
- **FK031**: Mobilkontroller (touch-baserad UX)
- **FK034**: Viewport-rättvisa (responsiv design)

**Icke-Funktionella Krav:**
- **IFK003**: 4 samtidiga sessioner (serverlasttestning)
- **IFK007**: Multi-webbläsarkompatibilitet (korswebbläsartestning)
- **IFK008**: Viewport-skalning (responsiv designkomplexitet)
- **IFK010**: 99% drifttid (övervakning och återhämtning)
- **IFK013**: Ingen dataförlust (tillståndssynkronisering)
- **IFK015**: Intuitiv design (användartestning)
- **IFK018**: Visuell feedback-tydlighet (designiteration)
- **IFK028**: WebSocket-kommunikation (nätverkslager-stabilitet)

---

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

- **Kritisk väg till MVP**: Realtidssynkronisering → Kärnspelmekanik → Sessionshantering → Åskådarvy
- **Riskhantering**: Fokusera 40% av utvecklingstiden på IFK002 och FK004; testa äldre enheter; implementera error handling & reconnection
- **Resursoptimering**: 2 utvecklare × 8 timmar = 16 persontimmar per dag; Sprint 1 (MVP) = 12h, Sprint 2 (Förmågor) = 3h, Sprint 3 (Poäng) = 1h
- **Framgångskriterier MVP**: FK001-FK005, FK013-FK017, FK023-FK028, FK030-FK032 implementerade; IFK002 <100ms; IFK010 99% drifttid