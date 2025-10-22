<p align="center">
  <img src="../../assets/logo.png" alt="Logo" width="100%" />
</p>

# 1.1 Bakgrund

## Projektets Ursprung

MazeRunner-projektet initierades av Josef Hallberg, universitetslektor vid Luleå Tekniska Universitet, som ett svar på behovet av ett tillförlitligt och engagerande demonstrationsverktyg för öppet hus-evenemang. Projektet bygger på hans 4-åriga erfarenhet av att utveckla interaktiva demonstrationsspel för att engagera gymnasiestudenter i datavetenskap.

### Initiala Diskussioner och Problemidentifiering

Under förberedelserna för öppet hus 2025 identifierades flera kritiska problem med befintliga demonstrationssystem:

**Tidigare System - Haptisk Teknologi:**
- Krävde komplex hårdvaruinstallation med specialiserad utrustning
- Frekventa drivrutinskonflikter vid operativsystemuppdateringar
- Opålitlig drift under demonstrationer (systemkraschar mitt i presentationer)
- Lång installations- och felsökningstid (flera timmar)
- Hög underhållsbörda som krävde konstant teknisk support

**Josef Hallbergs tidigare spelprototyper:**
- Stötte på synkroniseringsproblem vid multiplayer-implementering
- Unity-exportkomplexitet gjorde distribution svår
- Begränsad plattformskompatibilitet

Dessa erfarenheter ledde till en tydlig kravbild: ett system som "alltid fungerar" och prioriterar tillförlitlighet över teknisk komplexitet.

## Projektets Vision

Huvudmålet formulerades som att transformera det traditionella öppet hus-samtalet från "Är du intresserad av datavetenskap?" till "Vill du spela ett spel?" - en mer naturlig och engagerande ingång till diskussioner om utbildningen.

**Kärnidé:**
- Ett webbaserat multiplayer labyrintspel där två gymnasiestudenter tävlar
- Publiken följer på storskärm och hejar på sina favoriter
- Snabba spelsessioner (5 minuter) skapar kontinuerligt flöde av nya spelare
- Demonstrerar moderna webbutvecklingstekniker genom studentskapad mjukvara

## Teknikval och Lösningsansats

Efter intressentintervju med Josef Hallberg fastställdes följande tekniska riktlinjer:

**Teknisk Stack:**
- **Frontend**: React med TypeScript för responsivt användargränssnitt
- **Backend**: C# med ASP.NET Core för spelserver och logik
- **Realtidskommunikation**: SignalR/WebSocket för multiplayer-synkronisering
- **Datalagring**: SQLite för high scores och sessionsdata

**Design-filosofi:**
- Webbaserad lösning eliminerar installationsproblem
- Klient-server arkitektur förhindrar synkroniseringsproblem (allt speltillstånd på server)
- Ingen app-nedladdning krävs - bara skanna QR-kod och spela
- Fungerar på 6-7 år gamla smartphones och moderna webbläsare

**Praktiska Krav:**
- Installation från laptop till körande demo: under 2 minuter
- Stödja 4 samtidiga spelsessioner (8 spelare totalt)
- Fungera konsekvent över olika enheter och plattformar
- Minimal underhållsbörda för långsiktig användning (4+ år)

## Användningskontext

**Målgrupp:**
- **Primära spelare**: Gymnasiestudenter (16-25 år) som besöker öppet hus
- **Åskådare**: Föräldrar, vänner och andra besökare som tittar på storskärm
- **Demonstratör**: Josef Hallberg och andra universitetslärare

**Typiskt Scenario:**
1. Student skannar QR-kod med mobil eller laptop
2. Matchas automatiskt med annan redo spelare
3. 5-minuters labyrintäventyr där de tävlar om att hitta nyckel och nå utgång
4. Publiken ser hela spelet på storskärm och hejar
5. Vinnare får ange initialer i high score-lista
6. Naturligt samtal om programmering och datavetenskap följer

Denna bakgrund etablerar MazeRunner som en praktisk, tillförlitlig lösning som kombinerar underhållning med utbildningsdemonstration, designad för att engagera nästa generation datavetare.