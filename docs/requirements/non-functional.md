# 2.3 Icke-Funktionella Krav

## Prestandakrav
- **IFK001**: Speluppsättningstid <2 minuter från laptopuppstart till spelbart tillstånd
- **IFK002**: Spelarrörelsens svarstid <100ms under normala nätverksförhållanden
- **IFK003**: Stöd för 5 samtidiga sessioner utan prestandaförsämring
- **IFK004**: Mål att 90% av spelen slutförs inom 5 minuter, tillåt 7-8 minuter för återstående 10%
- **IFK005**: Kompasshjälpsystem aktiveras efter 5 minuter för att hjälpa spelare

## Kompatibilitetskrav  
- **IFK006**: Fungera på smartphones 6+ år gamla (Android 7+, iOS 12+)
- **IFK007**: Kompatibel med stora webbbläsare (Chrome, Firefox, Safari, Edge)
- **IFK008**: Konsekvent viewport-skalning över olika skärmstorlekar (4" till 27")
- **IFK009**: Ingen appinstallation krävs - endast webbbläsare

## Tillförlitlighetskrav
- **IFK010**: 99% drifttid under 3-timmars öppet hus-demonstrationsperioder  
- **IFK011**: Graciell hantering av spelarurkopplingar utan systemkrasch
- **IFK012**: Automatisk spelåterhämtning efter tillfälliga nätverksavbrott
- **IFK013**: Ingen dataförlust vid normala urkopplingsscenarier

## Användbarhetskrav
- **IFK014**: Nya spelare kan börja spela inom 30 sekunder efter anslutning
- **IFK015**: Spelregler förståeliga utan textinstruktioner (visuell/intuitiv design)
- **IFK016**: Åskådarvy engagerande för icke-spelande publik
- **IFK017**: High score-inmatningssystem liknande flipperspel (initialer för topp 10)
- **IFK018**: Tydlig visuell feedback för all förmågeanvändning och statuseffekter
- **IFK019**: Lärare kan enkelt växla mellan aktiva spelsessioner

## Tillgänglighets- och Designkrav
- **IFK020**: Olika avatarformer och mönster, inte bara färger, för spelardistinktion
- **IFK021**: Högkontrast visuell design för synlighet i bullrig miljö
- **IFK022**: Primärt visuella instruktioner snarare än textbaserad vägledning
- **IFK023**: Tydlig distinktion mellan spelare och motståndare genom flera visuella ledtrådar

## Ljudkrav
- **IFK024**: Bakgrundsmusik ej nödvändig på grund av bullrig demonstrationsmiljö
- **IFK025**: Ljudeffekter sekundär prioritet - visuell feedback är primär
- **IFK026**: Valfria ljudeffekter för handlingar (skjutning, förmågor) men får inte vara väsentliga

## Tekniska Arkitekturkrav
- **IFK027**: Klient-server-arkitektur med centraliserad spelstatushantering  
- **IFK028**: WebSocket-kommunikation för realtidsuppdateringar
- **IFK029**: Enkel serverdistribution på standard laptop-hårdvara
- **IFK030**: Minimala externa beroenden (undvik Unity, komplexa spelmotorer)
- **IFK031**: Ingen autentisering eller användarregistrering krävs - endast anonymt spel
- **IFK032**: React-frontend med C#-backend-implementering