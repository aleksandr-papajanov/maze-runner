<p align="center">
  <img src="../../assets/logo.png" alt="Logo" width="100%" />
</p>

# 2.3 Icke-Funktionella Krav

## Översikt

Detta dokument definierar alla icke-funktionella krav för MazeRunner-systemet, organiserade i en enhetlig tabell med prioritet och risk. Kraven täcker prestanda, kompatibilitet, tillförlitlighet, användbarhet, tillgänglighet och tekniska arkitekturbegränsningar.

---

## Icke-Funktionella Krav

### Prestanda

| ID | Namn | Beskrivning |
|---|---|---|
| IFK001 | Snabb installation | Spelinstallationstid från laptop-uppstart till spelbart tillstånd <2 minuter |
| IFK002 | Låg latens | Spelarrörelsens svarstid <100ms under normala nätverksförhållanden |
| IFK003 | Kapacitet | Stöd för 4 samtidiga sessioner (8 spelare) utan prestandaförsämring |
| IFK004 | Speltid | 90% av spelen slutförs inom 5 minuter, tillåt 7-8 minuter för 10% |
| IFK005 | Kompassaktivering | Kompasshjälpsystem aktiveras automatiskt efter 5 minuter |

### Kompatibilitet

| ID | Namn | Beskrivning |
|---|---|---|
| IFK006 | Enhetskompatibilitet | Fungera på smartphones 6+ år gamla (Android 7+, iOS 12+) |
| IFK007 | Webbläsarkompatibilitet | Kompatibel med Chrome, Firefox, Safari, Edge |
| IFK008 | Responsiv viewport | Konsekvent viewport-skalning (4" till 27" skärmar) |
| IFK009 | Friktionsfri åtkomst | Ingen appinstallation krävs - endast webbläsaråtkomst |

### Tillförlitlighet

| ID | Namn | Beskrivning |
|---|---|---|
| IFK010 | Drifttid | 99% drifttid under 3-timmars Öppet Hus-perioder (<2 min driftstopp) |
| IFK011 | Graciös felhantering | Graciös hantering av spelarurkopplingar utan systemkrasch |
| IFK012 | Återanslutning | Automatisk spelåterhämtning efter tillfälliga nätverksavbrott |
| IFK013 | Dataintegritet | Ingen dataförlust i normala urkopplingsscenarier |

### Användbarhet

| ID | Namn | Beskrivning |
|---|---|---|
| IFK014 | Snabb onboarding | Nya spelare kan börja spela inom 30 sekunder efter anslutning |
| IFK015 | Intuitiv design | Spelregler förståeliga utan textinstruktioner |
| IFK016 | Engagerande åskådarvy | Åskådarvy engagerande för icke-spelande publik |
| IFK017 | High score-inmatning | High score-inmatningssystem med initialer (flipperspelsstil) |
| IFK018 | Tydlig feedback | Tydlig visuell feedback för all förmågeanvändning och statuseffekter |
| IFK019 | Sessionshantering | Lärare kan enkelt växla mellan aktiva spelsessioner |

### Tillgänglighet

| ID | Namn | Beskrivning |
|---|---|---|
| IFK020 | Multimodal design | Olika avatarformer och mönster (inte bara färger) för spelardistinktion |
| IFK021 | Högkontrast design | Högkontrast visuell design för synlighet i bullrig miljö |
| IFK022 | Ikonbaserat UI | Primärt visuella instruktioner snarare än textbaserad vägledning |
| IFK023 | Visuell distinktion | Tydlig distinktion genom form, färg och mönster |

### Ljud

| ID | Namn | Beskrivning |
|---|---|---|
| IFK024 | Bakgrundsmusik | Bakgrundsmusik ej nödvändig (bullrig demonstrationsmiljö) |
| IFK025 | Ljudeffekter | Ljudeffekter sekundär prioritet - visuell feedback är primär |
| IFK026 | Valfritt ljud | Valfria ljudeffekter för handlingar (får ej vara väsentliga) |

### Teknisk Arkitektur

| ID | Namn | Beskrivning |
|---|---|---|
| IFK027 | Serverarkitektur | Klient-server-arkitektur med centraliserad speltillståndshantering |
| IFK028 | WebSocket-kommunikation | WebSocket-kommunikation (SignalR) för realtidsuppdateringar |
| IFK029 | Enkel serverdistribution | Enkel serverdistribution på standard laptop-hårdvara |
| IFK030 | Minimala beroenden | Minimala externa beroenden (React + C#, undvik Unity/komplexa motorer) |
| IFK031 | Anonym åtkomst | Ingen autentisering eller användarregistrering - endast anonymt spel |
| IFK032 | Teknologistack | React-frontend med C# ASP.NET Core-backend-implementering |

---

## Kravspårbarhet

### Användarfallsmappning

| Användarfall | Relaterade Icke-Funktionella Krav |
| ------------ | --------------------------------- |
| UC1: Anslut via QR-kod | IFK006, IFK007, IFK009, IFK014, IFK022, IFK031 |
| UC2: Navigera labyrint | IFK002, IFK004, IFK006, IFK007, IFK008, IFK015, IFK020, IFK021, IFK022, IFK023, IFK028 |
| UC3: Samla nyckel | IFK005 |
| UC4: Använd förmågor | IFK015, IFK018 |
| UC5: Nå utgång | IFK004 |
| UC6: Visa poäng | IFK017 |
| UC7: Starta session | IFK001, IFK003, IFK010 |
| UC8: Övervaka spel | IFK016, IFK021 |
| UC9: Växla sessioner | IFK019 |
| UC10: Hantera evenemang | IFK001, IFK003, IFK010, IFK029 |
| UC11: Titta på spel | IFK016 |
| UC13: Synkronisera tillstånd | IFK002, IFK012, IFK027, IFK028 |
| UC14: Hantera urkoppling | IFK011, IFK012, IFK013 |
| UC16: Spåra poäng | IFK017 |

---

## Systembegränsningar

### Tekniska Begränsningar
- **Enkel Serverbegränsning**: All spellogik körs på en laptop
- **Endast Webbteknologi**: React-frontend med C#-backend, inga inhemska mobilappar
- **Nätverksberoende**: Kräver stabil WiFi-anslutning för realtidsspelande
- **Webbläsarkompatibilitet**: Måste fungera på äldre enheter (6+ år gamla)

### Miljömässiga Begränsningar
- **Bullrig Miljö**: Öppet Hus-miljö med många distraktioner
- **Stor Publik**: Åskådarvy måste vara synlig och engagerande
- **Tidsbegränsning**: Snabb installation (<2 minuter) krävs för demonstrationer
- **Enhetsvariation**: Studenter tar med olika telefoner och surfplattor (iOS/Android, gamla/nya)

### Affärsbegränsningar
- **Ingen Installation**: Friktionsfri åtkomst endast via QR-kod/URL
- **Ingen Registrering**: Anonymt spelande utan användarkonton
- **Evenemangslängd**: 3-timmars demonstrationsfönster som kräver hög tillförlitlighet
- **Budget**: Enkel teknisk stack för att minimera komplexitet och kostnad

---

---

**Totalt**: 32 Icke-Funktionella Krav

## Validering och Testning

### Prestandatestning
- Lasttestning med 8 samtidiga spelare (4 sessioner)
- Latensmätning under olika nätverksförhållanden (<100ms mål)
- Stresstestning på målenheter (6+ år gamla smartphones)
- Minnesprofiliering och CPU-användning

### Kompatibilitetstestning
- Webbläsarkompatibilitetsmatris (Chrome, Firefox, Safari, Edge)
- Enhetstestning (Android 7+, iOS 12+)
- Skärmstorlekstestning (4" till 27")
- Cross-platform kontrollertestning (touch vs tangentbord)

### Tillförlitlighetstestning
- Urkopplingsscenario-testning (graciös degradering)
- Nätverksavbrottsåterhämtning (automatisk reconnect)
- Långvariga stabilitetstester (3+ timmar kontinuerlig drift)
- Sessionväxlingsstabilitet

### Användbarhetstestning
- Introduktionstidsmätning (<30 sekunder från QR-kod till spel)
- Intuitiv designvalidering (inga instruktioner behövs)
- Åskådarvy-engagemangsbedömning
- Tillgänglighetstestning (färgblindhetssimulering)

### Säkerhet och Validering
- Input-validering för spelarens kontroller
- Server-side spelavslutningsvalidering
- Förhindra manipulation av high scores
- Session timeout-hantering

---

För prioritering, riskbedömning och implementeringsplan, se [2.4 Användarkrav](acceptance.md).
