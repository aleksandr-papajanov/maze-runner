# 2.4 Användningsfall

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