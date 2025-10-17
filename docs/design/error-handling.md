# 3.6 Felhantering och Gränsfall

## Anslutningsproblem
- **Spelarurkoppling**: Omedelbar spelterminering, återvänd båda spelare till lobby
- **Serverurkoppling**: React-klient visar anslutning förlorad meddelande, automatisk återanslutningsförsök
- **Lag-kompensation**: Klient-sida prediktion med server-reconciliation
- **Timeout-hantering**: 30-sekunder inaktivitetstimeout, automatisk spelförlust

## Spellogik Gränsfall  
- **Samtidig Nyckelsamling**: C# server tidsstämpel bestämmer vinnare
- **Förmågekonflikter**: Server bearbetar i mottagen ordning, senare åtgärder kan misslyckas
- **Labyrintgränsproblem**: Server validerar alla rörelser, avvisar ogiltiga positioner
- **Utgång Utan Nyckel**: Server förhindrar utgångsaktivering, visar lämpligt meddelande

## Systemresurshantering
- **Minnesupprensning**: Automatisk sessionupprensning efter spelslutförande
- **Anslutningsgränser**: Maximum 10 samtidiga spelare, ytterligare anslutningar köade
- **CPU-lastbalansering**: Spellogik optimerad för enkeltrådig utförande
- **Graciell Försämring**: Reducerad uppdateringsfrekvens under höga lastförhållanden

*[PLACEHOLDER: Felhanteringsflödesdiagram som visar beslutstrad för olika felscenarier]*

## SignalR-Specifik Felhantering
- **Anslutningsåterförsökslogik**: Automatisk återanslutning med exponentiell backoff
- **Meddelandebekräftelse**: Kritiska spelhändelser kräver klientbekräftelse
- **Heartbeat-övervakning**: Regelbunden ping/pong för att upptäcka inaktiva anslutningar
- **Graciell Fallback**: Försämra till polling om WebSocket misslyckas