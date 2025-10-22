# 2.3 Icke-Funktionella Krav

## Översikt

Detta dokument definierar alla icke-funktionella krav för MazeRunner-systemet, som täcker prestanda, kompatibilitet, tillförlitlighet, användbarhet, tillgänglighet och tekniska arkitekturbegränsningar.

---

## Prestandakrav

| ID | Krav | Mål | Risk |
| --- | ----------- | ------ | ---- |
| **IFK001** | Spelinstallationstid från laptop-uppstart till spelbart tillstånd | <2 minuter | Låg |
| **IFK002** | Spelarrörelsens svarstid under normala nätverksförhållanden | <100ms | Hög |
| **IFK003** | Stöd för 4 samtidiga sessioner utan prestandaförsämring | 8 samtidiga spelare | Medel |
| **IFK004** | 90% av spelen slutförs inom 5 minuter, tillåt 7-8 minuter för återstående 10% | 5-8 min intervall | Låg |
| **IFK005** | Kompasshjälpsystem aktiveras efter 5 minuter för att hjälpa spelare | Auto-trigger | Låg |

---

## Kompatibilitetskrav

| ID | Krav | Specifikation | Risk |
| --- | ----------- | ------------- | ---- |
| **IFK006** | Fungera på smartphones 6+ år gamla | Android 7+, iOS 12+ | Hög |
| **IFK007** | Kompatibel med stora webbläsare | Chrome, Firefox, Safari, Edge | Medel |
| **IFK008** | Konsekvent viewport-skalning över olika skärmstorlekar | 4" till 27" skärmar | Medel |
| **IFK009** | Ingen appinstallation krävs - endast webbläsare | Webbaserad åtkomst | Låg |

---

## Tillförlitlighetskrav

| ID | Krav | Mål | Risk |
| --- | ----------- | ------ | ---- |
| **IFK010** | 99% drifttid under 3-timmars Öppet Hus-demonstrationsperioder | <2 min driftstopp | Medel |
| **IFK011** | Graciös hantering av spelarurkopplingar utan systemkrasch | Auto-återhämtning | Hög |
| **IFK012** | Automatisk spelåterhämtning efter tillfälliga nätverksavbrott | Återanslutningslogik | Hög |
| **IFK013** | Ingen dataförlust i normala urkopplingsscenarier | Tillståndsbevarande | Medel |

---

## Användbarhetskrav

| ID | Krav | Mål | Risk |
| --- | ----------- | ------ | ---- |
| **IFK014** | Nya spelare kan börja spela inom 30 sekunder efter anslutning | Introduktionstid | Låg |
| **IFK015** | Spelregler förståeliga utan textinstruktioner | Visuell/intuitiv design | Medel |
| **IFK016** | Åskådarvy engagerande för icke-spelande publik | Publikengagemang | Låg |
| **IFK017** | High score-inmatningssystem liknande flipperspel | Initialer för topp 10 | Låg |
| **IFK018** | Tydlig visuell feedback för all förmågeanvändning och statuseffekter | Visuell tydlighet | Medel |
| **IFK019** | Lärare kan enkelt växla mellan aktiva spelsessioner | Sessionshantering | Låg |

---

## Tillgänglighets- och Designkrav

| ID | Krav | Specifikation | Risk |
| --- | ----------- | ------------- | ---- |
| **IFK020** | Olika avatarformer och mönster, inte bara färger, för spelardistinktion | Multimodal design | Låg |
| **IFK021** | Högkontrast visuell design för synlighet i bullrig miljö | Kontrastförhållanden | Låg |
| **IFK022** | Primärt visuella instruktioner snarare än textbaserad vägledning | Ikonbaserat UI | Låg |
| **IFK023** | Tydlig distinktion mellan spelare och motståndare genom flera visuella ledtrådar | Form + färg + mönster | Låg |

---

## Ljudkrav

| ID | Krav | Prioritet | Anteckningar |
| --- | ----------- | -------- | ----- |
| **IFK024** | Bakgrundsmusik ej nödvändig på grund av bullrig demonstrationsmiljö | Valfri | Låg prioritet |
| **IFK025** | Ljudeffekter sekundär prioritet - visuell feedback är primär | Valfri | Inte väsentlig |
| **IFK026** | Valfria ljudeffekter för handlingar (skjutning, förmågor) men får inte vara väsentliga | Förbättring | Trevligt att ha |

---

## Tekniska Arkitekturkrav

| ID | Krav | Specifikation | Risk |
| --- | ----------- | ------------- | ---- |
| **IFK027** | Klient-server-arkitektur med centraliserad speltillståndshantering | Auktoritativ server | Låg |
| **IFK028** | WebSocket-kommunikation för realtidsuppdateringar | SignalR/WebSocket | Medel |
| **IFK029** | Enkel serverdistribution på standard laptop-hårdvara | Enkel serverinstans | Låg |
| **IFK030** | Minimala externa beroenden (undvik Unity, komplexa spelmotorer) | React + C#-stack | Låg |
| **IFK031** | Ingen autentisering eller användarregistrering krävs - endast anonymt spel | Förenklad åtkomst | Låg |
| **IFK032** | React-frontend med C# ASP.NET Core-backend-implementering | Teknisk stack | Låg |

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

## Riskbedömningssammanfattning

### Högrisk-krav
- **IFK002**: <100ms latens (beror på nätverkskvalitet, äldre enheter)
- **IFK006**: 6+ år gammalt enhetsstöd (begränsad testmöjlighet)
- **IFK011**: Graciös urkopplingshantering (komplexa kantfall)
- **IFK012**: Automatisk återhämtning (kräver robust tillståndshantering)

### Medelrisk-krav
- **IFK003**: 4 samtidiga sessioner (serverlasttestning behövs)
- **IFK007**: Multi-webbläsarkompatibilitet (korswebbläsartestning krävs)
- **IFK008**: Viewport-skalning (responsiv designkomplexitet)
- **IFK010**: 99% drifttid (kräver övervakning och snabb återhämtning)
- **IFK013**: Ingen dataförlust (tillståndssynkroniseringskomplexitet)
- **IFK015**: Intuitiv design (kräver användartestning)
- **IFK018**: Visuell feedback-tydlighet (designiteration behövs)
- **IFK028**: WebSocket-tillförlitlighet (nätverksstabilitetsberoende)

### Lågrisk-krav
- Alla andra krav (IFK001, IFK004, IFK005, IFK009, IFK014, IFK016, IFK017, IFK019-IFK027, IFK029-IFK032)

---

## Validering och Testning

### Prestandatestning
- Lasttestning med 10 samtidiga spelare
- Latensmätning under olika nätverksförhållanden
- Stresstestning på målenheter (6+ år gamla smartphones)

### Kompatibilitetstestning
- Webbläsarkompatibilitetsmatris (Chrome, Firefox, Safari, Edge)
- Enhetstestning (Android 7+, iOS 12+)
- Skärmstorlekstestning (4" till 27")

### Tillförlitlighetstestning
- Urkopplingsscenario-testning
- Nätverksavbrottsåterhämtning
- Långvariga stabilitetstester (3+ timmar)

### Användbarhetstestning
- Introduktionstidsmätning (<30 sekunder)
- Intuitiv designvalidering (inga instruktioner behövs)
- Åskådarvy-engagemangsbedömning

För detaljerade implementeringsprioriteter och beroenden, se [2.4 Användarkrav](acceptance.md).
