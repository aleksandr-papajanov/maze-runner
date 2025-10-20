# 2.2 Användarfall och Funktionella Krav

## Primära Användningsfall

### AF001: Anslut och Starta Spel
- **Aktör**: Spelare
- **Förvillkor**: QR-kod skannad eller URL besökt
- **Flöde**: 
  1. Spelare kommer åt spel-URL på enhet
  2. System visar vänteskärm
  3. Andra spelare ansluter inom rimlig tid
  4. Spel startar automatiskt med 3-sekunder nedräkning
- **Eftervillkor**: Båda spelare ser labyrint och kan röra sig

### AF002: Navigera och Tävla  
- **Aktör**: Spelare (båda)
- **Förvillkor**: Spelsession aktiv
- **Flöde**:
  1. Spelare rör sig genom labyrint med enhetskontroller
  2. System synkroniserar positioner i realtid  
  3. Spelare söker efter nyckel medan de potentiellt använder förmågor på motståndare
  4. Spelare som hittar nyckel springer mot utgång
- **Eftervillkor**: Vinnaren når utgång eller spel timeout

### AF003: Åskåda Spel
- **Aktör**: Eventorganisatör, Publik
- **Förvillkor**: Spelsession aktiv, åskådarvy aktiverad  
- **Flöde**:
  1. Organisatör väljer aktiv spelsession att visa
  2. Full labyrintvy visas på stor skärm
  3. Publik kan se båda spelares positioner och handlingar
  4. Realtidsuppdateringar bibehåller engagemang
- **Eftervillkor**: Spelslut synligt för alla deltagare

### AF004: Hantera Urkoppling
- **Aktör**: System
- **Förvillkor**: Spelare förlorar nätverksanslutning
- **Flöde**:
  1. System upptäcker spelarurkoppling
  2. Spel avslutas för båda spelare  
  3. Båda spelare återgår till startskärm
  4. Åskådarvy visar lämpligt meddelande
- **Eftervillkor**: System redo för nya spelsessioner

## Sekundära Användningsfall

### AF005: Spåra High Scores  
- **Aktör**: Spelare, System
- **Flöde**: Vinnare anger initialer för topplista, system lagrar topp 10 poäng
- **Prioritet**: Bör Ha

### AF006: Flera Sessionshantering
- **Aktör**: System, Eventorganisatör  
- **Flöde**: Organisatör växlar mellan olika aktiva spel på åskådarvisning
- **Prioritet**: Bör Ha

## Funktionella Krav

### Grundläggande Spelmekanik (Måste Ha)
- **FK001**: Två spelare tävlar samtidigt i samma labyrintinstans
- **FK002**: Spelare måste hitta en slumpmässigt placerad nyckel innan de kan nå utgången
- **FK003**: Första spelaren som når utgången med nyckeln vinner spelet
- **FK004**: Realtidssynkronisering av spelarpositioner (<100ms latens)
- **FK005**: QR-kodåtkomst - spelare skannar kod för att gå med i spel inom max 1 minut

### Förmågesystem (Bör Ha)
- **FK006**: Sömnelixir - fryser motståndaren i 2 sekunder och tvingar dem att tappa nyckeln
- **FK007**: Förvirrningsstråle - vänder på motståndarens joystickkontroller
- **FK008**: Strategiska fällor - kan placeras vid utgång eller nyckelplatser
- **FK009**: Bedövande projektiler - synliga projektiler som kan avfyras mot motståndare
- **FK010**: Blandat aktiveringssystem - power-ups aktiveras automatiskt
- **FK011**: Tre förmågeknappar på mobil (höger sida), tangentbordstangenter (JKL) på dator
- **FK012**: Begränsat inventory - max 3 olika förmågetyper

### Spelinnehåll (Måste Ha)
- **FK013**: En enda labyrintlayout med fast väggstruktur för konsekvens
- **FK014**: Slumpmässig kartgenerering - nyckel, utgång och power-up positioner
- **FK015**: Begränsad viewport per spelare (dimma av krig-effekt)
- **FK016**: Visuell feedback för alla spelaraktioner och förmågeanvändning
- **FK017**: Automatisk spelavslutning efter vinst eller spelarurkoppling

### Flerspelarstöd (Måste Ha)
- **FK023**: Stöd för 5 samtidiga spelsessioner (10 spelare totalt)
- **FK024**: Automatisk matchmaking
- **FK025**: Åskådarvy visar hela labyrinten
- **FK026**: Lärare kan växla mellan olika aktiva spelsessioner

### Användargränssnitt (Måste Ha)
- **FK027**: Kontroller anpassas till enhetstyp (touchjoystick vs tangentbord)
- **FK028**: Tydlig visuell distinktion mellan spelaravatarer
- **FK029**: Spelstatusvisning (timer, förmågor, poäng, inventory)
- **FK030**: 8-riktningsrörelse (inte bara 4-riktningar)

För komplett lista, se [Funktionella Krav](functional.md).