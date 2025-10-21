# 2.5 Interfacespecifikation och Storyboards

## Gränssnittsöversikt

MazeRunner har tre primära användargränssnitt:
1. **Spelargränssnitt** (Mobil/Desktop)
2. **Åskådargränssnitt** (Stor Skärm)
3. **Administrationsgränssnitt** (Organisatör)

För detaljerad UI-design, se [Användargränssnittsdesign](../design/ui-design.md).

## Spelargränssnitt (Mobilt)

### Layout och Komponenter
- **Spelområde**: 70% av skärmen - visar begränsad labyrintvy
- **Kontrollerzon (Vänster)**: Virtual joystick för 8-riktningsrörelse
- **Förmågezon (Höger)**: 3 förmåga-knappar vertikalt arrangerade
- **Statusfält (Topp)**: Timer, poäng, mini-inventory

### Kontrollspecifikation
- **Joystick**: Position nedre vänstra hörnet, 120x120px, 8-riktningsrörelse
- **Förmågeknappar**: Position nedre högra hörnet, 60x60px vardera, vertikal stack
- **Desktop**: WASD-rörelse, JKL-förmågeaktivering

## Storyboard: Spelarupplevelelse

```
[Panel 1: Anslutning]
Spelare skannar QR-kod på smartphone
↓
[Panel 2: Väntar]
Väntskärm visas, väntar på motståndare
↓
[Panel 3: Start]
3-2-1 nedräkning, spel börjar
↓
[Panel 4: Spel]
Navigera labyrint, samla föremål, använd förmågor
↓
[Panel 5: Vinst]
Vinnarskärm, poäng, eventuellt ange initialer
```

## Åskådargränssnitt

### Layout
- **Huvudvy**: Full labyrint med båda spelares positioner
- **Spelare 1 Info**: Vänster sidopanel (namn, poäng, status)
- **Spelare 2 Info**: Höger sidopanel (namn, poäng, status)
- **Sessionväljare**: Nedre delen - lista över aktiva spel

## Systembegränsningar och Antaganden

### Tekniska Begränsningar
- **Enkel serverbegränsning**: All spellogik körs på en laptop, ingen distribuerad arkitektur
- **Endast webbteknologi**: React-frontend med C#-backend, inga inhemska mobilappar eller spelmotorer
- **Nätverksberoende**: Kräver stabil wifi-anslutning för realtidsspelande
- **Webbläsarkompatibilitet**: Måste fungera utan moderna JavaScript-funktioner på äldre enheter (6+ år gamla)
- **Undvik Unity**: Uttryckligen undvika Unity på grund av komplexitet och underhållsproblem från tidigare projekt
- **WebSocket-krav**: Realtidskommunikation kräver WebSocket-stöd

## Affärsbegränsningar  
- **Demonstrationskontext**: Optimerad för kortsiktigt engagemang, inte långsiktig retention
- **Noll installation**: Kan inte kräva app-nedladdningar eller kontoskapelse
- **Ingen autentisering krävs**: Endast anonymt spelande - inga användarkonton, inloggningar eller registrering
- **Bullermiljö**: Visuell feedback prioriterad över ljud (100+ personer miljö)
- **Installationsenkelhelt**: Måste vara hanterbar av icke-teknisk universitetspersonal
- **QR-kod åtkomst**: Spelare måste kunna ansluta via QR-kod skanning inom 1 minut maximum
- **Fysiskt utrymme**: Endast ~10 personer kan få plats runt demonstrationsbås
- **Installationstid**: Maximum 2 minuter från laptoppstart till spelbar demo

## Rättvisa och Social Kontext
- **Perfekt rättvisa inte kritisk**: Spelare spelar vanligtvis bara en gång, så mindre obalanser acceptabla
- **Socialt fusk acceptabelt**: Spelare kan "fuska" genom att titta på åskådarskärm - skapar rolig interaktion
- **Inga griefing-bekymmer**: Spelare är gymnasievänner i vänlig miljö, inte konkurrenskraftiga främlingar
- **Symmetrisk karta valfri**: Kunde implementera för rättvisa men inte väsentligt krav
- **Engångsspel**: Inget repris-värde behövs - designad för enkel spelupplevelse

## Huvudantaganden
- **Målgruppsbekantskap**: Användare förstår grundläggande labyrintspelkoncept
- **Enhetstillgänglighet**: Spelare har smartphones eller kan använda tillhandahållna enheter  
- **Network infrastructure**: University provides adequate wifi for concurrent connections
- **Social context**: Competitive gameplay with audience creates natural engagement
- **Friendly environment**: Players are not competitive strangers, reduces need for anti-cheat measures
- **Visual focus**: Noisy environment (100+ people) means visual feedback must be primary communication method