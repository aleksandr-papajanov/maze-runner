# MazeRunner Spel - Komplett Vision

## Spelöversikt

MazeRunner är ett enkelt, webbaserat multiplayer labyrintspel designat som ett interaktivt demonstrationsverktyg för universitets öppet hus-evenemang. Spelet skapar en engagerande "isbrytare"-upplevelse som får gymnasiestudenter entusiastiska över datavetenskap samtidigt som det visar upp studentarbete.

## Kärnspelupplevelse

### Den Grundläggande Spelcykeln
1. **Snabb Installation**: Studenter skannar en QR-kod eller besöker en URL på sina telefoner/laptops
2. **Omedelbar Matchning**: Första spelare väntar, andra spelare ansluter → spel startar automatiskt  
3. **5-Minuters Äventyr**: Spelare springer genom en labyrint för att hitta en nyckel och fly
4. **Åskådarspänning**: Publiken tittar på en stor skärm, hejar och ger tips
5. **Enkel Slutsats**: Vinnarfirande, valfri high score-inmatning, tillbaka till start

### Vad Spelare Ser och Gör

**På Din Enhet (Telefon/Laptop)**:
- Uppifrån-vy av din karaktär i labyrinten
- Du ser bara en liten del runt din karaktär (som en strålkastare i mörkret)
- Karaktären vänder sig mot riktningen du rör dig (viktigt för att sikta förmågor)
- Enkla kontroller: Piltangenter/WASD på dator, on-screen joystick på telefon
- 3 förmåga-knappar på höger sida av skärmen

**På Den Stora Skärmen (Åskådarvy)**:
- Full labyrintöversikt som visar båda spelare
- Alla kan se hela layouten, nyckelposition, utgångsposition
- Perfekt för publiken att heja: "Nyckeln är bakom dig!" eller "Akta dig, de kommer!"

## Karaktär och Värld

### Visuell Stil
- **Uppifrån-perspektiv** (som klassiska arkadspel)
- **Fantasytema föredras**: Trollkarlar eller krigare som rör sig genom en fängelsestil-labyrint
- **Enkel men tydlig grafik**: Lätt att särskilja din karaktär från motståndare
- **Konsekvent tema**: Om karaktärer är trollkarlar, ser labyrinten ut som en fängelse (inte modern byggnad)

### Din Karaktär
- Antingen en detaljerad animerad sprite med ben/rörelse ELLER en enkel geometrisk form med riktningspil
- Olika visuellt utseende från motståndare (olika färg OCH olika form - viktigt för tillgänglighet)
- Tydlig indikation av vilken riktning du vänder mot (påverkar var du skjuter förmågor)

## Kärnspelmekanik

### Målet
**Vinstvillkor**: Hitta nyckeln, nå sedan utgången först
- **Nyckel**: Gömd någonstans i labyrinten, position randomiserad varje spel
- **Utgång**: Synlig för alla, men du behöver nyckeln för att använda den
- **Strategielement**: Du kan campa vid utgången och bakhålla nyckelinnehavaren!

### Rörelse och Syn
- **Dimma av Krig**: Du ser bara ett cirkulärt område runt din karaktär
- **Kanske**: 5-sekunder full-kart förhandsvisning i början, sedan dimma slår in
- **Rättvist Spel**: Alla enheter visar ungefär samma mängd av labyrinten (samma "viewport")

### Stridsystem - Den Roliga Delen!
Spelare kan använda förmågor för att stoppa varandra:

**Förmågetyper**:
1. **Stun Shot**: Frys motståndare i 2 sekunder, de tappar nyckeln
2. **Förvirringsstrål**: Vänd om motståndarens kontroller (vänster blir höger, etc.)
3. **Hastighetsökning**: Rör dig snabbare under kort tid (auto-aktiveras när upphämtad)

**Förmågeanvändning**:
- 3 förmåga-platser, var och en med olika cooldown/användningsregler
- Vissa aktiveras automatiskt när du går över dem (hastighetsökning)
- Andra sparar du och använder strategiskt (stun shot, förvirringsstrål)
- Visuell feedback: Se projektiler flyga, se träffeffekter, vet om du träffade/missade

**Strategiska Element**:
- Göm dig nära utgången och bakhåll nyckelinnehavaren
- Sätt fällor vid flaskhalsar
- Jaga personen med nyckeln med kompassriktning (given efter viss tid)

## Föremål och Power-ups

### Samlarobjekt
- **Bonuspoäng**: Äpple/mynt-liknande objekt spridda runt labyrinten för high score
- **Power-ups**: Hastighetsökning, bättre syn, extra förmågor
- **Hemliga Bokstäver**: Valfri sidouppdrag för att stava ett dagligt ord för priser

### Risk vs Belöning
- Att samla bonusobjekt gör dig sårbar (tar tid, exponerar position)
- Nyckelinnehavare är synlig för andra genom kompasstips efter tid passerar
- Smarta spelare balanserar hastighet, strid och insamling

## Teknisk Upplevelse

### Enhetskompatibilitet
**Fungerar på Allt**:
- Moderna smartphones (Android/iOS, även 6-7 år gamla)
- Laptops och desktops (Windows/Mac/Linux)
- Surfplattor och andra touch-enheter

**Kontroller Anpassar sig till Enhet**:
- **Telefon**: On-screen joystick (vänster tumme) + förmåga-knappar (höger sida)
- **Dator**: WASD-rörelse + tangentbordsgenvägar för förmågor
- **Flexibel**: Kan använda mus, trackpad eller endast tangentbord beroende på installation

### Prestandakrav
- **Snabb uppstart**: Från QR-kod skanning till spelande under 1 minut
- **Smidigt spelande**: <100ms svarstid för rörelser
- **Tillförlitlig**: Fungerar även med fläckig wifi, hanterar urkopplingar graciellt
- **Skalbar**: Stödjer 4 samtidiga spel (8 spelare) utan problem

## Social och Åskådarupplevelse

### "E-sport"-elementet
- **Stor skärm drama**: Publiken ser allt, spelare gör det inte
- **Naturlig kommentar**: "Han är precis bakom dig!" "Nyckeln är där borta!"
- **Spänningsbyggande**: Täta lopp till utgången, sista sekunden förmågeanvändning
- **Snabb omvändning**: Spel slutar snabbt nog för att hålla publiken engagerad

### Utbildningsvärde
- **Studentshowcase**: "Detta spel skapades av studenter i sitt 3:e år"
- **Teknikdemonstration**: Visar webbutveckling, realtidsnätverkande, speldesign
- **Samtalsstartare**: Får studenter att prata om programmering och spelutveckling
- **Tillgänglighet**: Inget behov att förklara komplexa regler - alla förstår "hitta nyckel, nå utgång"

## Spelflöde och Timing

### Typisk Spelsession (3-5 minuter)
1. **0-30 sekunder**: Spelare ansluter, kort instruktionsskärm, nedräkning
2. **30 sekunder - 3 minuter**: Kärnspelande - utforskning, hitta nyckel, strid
3. **3-5 minuter**: Slutspel - nyckelinnehavare springer mot utgång, slutliga konfrontationer
4. **Valfritt**: Övertidsassistans (kompass till nyckel) om spel körs länge

### Slutvillkor
- **Seger**: Första spelare att lämna med nyckel vinner
- **Anslutningsförlust**: Spel slutar, båda spelare återgår till startskärm
- **Tidsgräns**: Mjuk gräns med assistans, inte hård avklippning
- **Resultat**: Tydlig vinnare/förlorare skärm, poängvisning, valfri high score-inmatning

## Varför Denna Design Fungerar

### För Universitetet (Josefs Mål)
- **Tillförlitlig**: Ingen hårdvaruinstallation, inga driverproblem, bara öppna webbläsare
- **Portabel**: Körs på en laptop, fungerar var som helst med wifi
- **Underhållbar**: Webbteknologi, enkla uppdateringar, bekant för studenter
- **Skalbar**: Flera spel som körs samtidigt utan problem

### För Gymnasiestudenter
- **Omedelbart bekant**: Labyrintspel är universellt förstådda
- **Social upplevelse**: Roligt att spela med vänner, roligt att titta på andra
- **Snabb tillfredsställelse**: Snabba spel, omedelbar feedback, tydliga vinnare
- **Låg barriär**: Ingen app-nedladdning, ingen kontoskapelse, bara skanna och spela

### För Publiken
- **Visuell spänning**: Kan se hela spelet utvecklas på stor skärm
- **Deltagande**: Naturlig impuls att hjälpa och heja på spelare
- **Förståelse**: Lätt att följa vad som händer, tydliga mål
- **Reprisbarhet**: Varje spel är olika på grund av randomiserade element

## Utvecklingsprioriteringar

### Måste Ha (Minimum Viable Product)
1. Grundläggande labyrintnavigering med dimma av krig
2. Nyckelspawning och insamling
3. Utgångsaktivering med nyckel
4. Enkel stun-förmåga
5. Åskådarvy på separat skärm
6. Vinst/förlust-villkor

### Bör Ha (Förbättrad Upplevelse)
1. Flera förmågetyper
2. Visuella effekter för förmågor
3. Bonuspoänginsamling
4. High score-system
5. Mobiloptimerade kontroller

### Kunde Ha (Fina Tillägg)
1. Flera labyrintlayouter
2. Daglig ordsamlingsuppdrag
3. Animerade karaktärsprites
4. Ljudeffekter (där lämpligt)
5. Avancerade power-ups

Denna vision ger oss ett tydligt mål: skapa en enkel, tillförlitlig, engagerande multiplayer-upplevelse som fungerar perfekt för sitt avsedda syfte - att få gymnasiestudenter entusiastiska över datavetenskap genom hands-on spel!