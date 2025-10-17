# 2.5 Systembegränsningar och Antaganden

## Tekniska Begränsningar
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