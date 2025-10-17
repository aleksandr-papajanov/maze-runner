# 3.7 Säkerhet och Validering

## Inmatningsvalidering
- **Rörelsegränser**: Alla spelarpositioner validerade mot labyrintgeometri på C# server
- **Åtgärdshastighetsavgränsning**: Förhindra spam-klickande av förmågor och rörelser
- **Tillståndsintegritet**: Server validerar alla tillståndsändringar innan sändning via SignalR
- **Klientförtroendemodell**: Anta att React-klienter kan vara komprometterade, validera allt server-sida

## Grundläggande Säkerhetsåtgärder
- **Ingen Autentisering Krävs**: Matchar användningsfall för anonymt spelande
- **Sessionisolering**: Spelare kan inte påverka andra spelsessioner
- **Resursskydd**: Förhindra klienter från att överväldiga C# serverresurser
- **Enkelt Anti-Fusk**: Rörelsehastighet och förmåga cooldown-validering

## ASP.NET Core Säkerhetsfunktioner
- **CORS-konfiguration**: Begränsa cross-origin-förfrågningar lämpligt
- **Inmatningssanitisering**: Validera all inkommande data från React-klienter
- **SignalR Säkerhet**: Använd anslutningsbaserad auktorisering för spelsessioner
- **Resursgränser**: Konfigurera lämpliga timeout och meddelandestorleksgränser

Denna systemdesign tillhandahåller en robust grund för att implementera MazeRunner-spelet med React + C# medan enkelhet och tillförlitlighet upprätthålls som primära designmål.