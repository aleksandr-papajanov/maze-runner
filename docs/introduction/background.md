# 1.1 Bakgrund

Kort övergripande beskrivning av teknikområdet och tekniker som används i projektet.

## Teknikområde

MazeRunner är ett webbaserat multiplayer labyrintspel designat för universitets öppet hus-demonstrationer på Luleå Tekniska Universitet (LTU). Projektet använder moderna webbteknologier för att skapa en interaktiv spelupplevelse:

- **Frontend-teknologi**: React med TypeScript för responsivt användargränssnitt
- **Backend-teknologi**: C# med ASP.NET Core för spelserver och logik
- **Realtidskommunikation**: SignalR/WebSocket för multiplayer-synkronisering
- **Datalagring**: SQLite för high scores och sessionsdata

## Teknisk Kontext

Det nuvarande hårdvarubaserade demonstrationssystemet (haptisk teknologi) har visat sig opålitligt på grund av komplexa installationskrav, driverkompabilitetsproblem och frekventa tekniska fel. Huvudproblem med det tidigare systemet inkluderar:

- **Komplex hårdvaruinstallation**: Krävde specialiserad hårdvara och driverinstallationer
- **Tillförlitlighetsproblem**: Gick ofta sönder med operativsystemuppdateringar  
- **Installationstid**: Tog betydande tid att konfigurera och felsöka
- **Underhållsbörda**: Krävde konstant teknisk support och uppdateringar

## Lösningsfilosofi

MazeRunner förkroppsligar en "fungerar alltid"-filosofi, prioriterar tillförlitlighet och enkelhet över teknisk komplexitet. En enkel webbaserad lösning behövs som kan installeras under 2 minuter och fungerar konsekvent över olika enheter och miljöer.

## Långsiktig Vision

Josef Hallberg har utvecklat interaktiva demonstrationsspel för LTU öppet hus-evenemang i 4 på varandra följande år. Tidigare projekt stötte på synkroniseringsproblem och Unity-exportkomplexitet. MazeRunner är designat för flerårig användning med minimal underhåll, transformerar den typiska "Är du intresserad av datavetenskap?"-ansatsen till "Vill du spela ett spel?"