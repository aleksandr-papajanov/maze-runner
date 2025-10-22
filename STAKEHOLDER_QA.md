1. Spelmekanik och Föremål

- Hur ska spelet vara intuitivt att komma igång med (finns det behov av handledning, introduktionssekvens)?
**Svar**: Spelet ska vara extremt intuitivt - de flesta vet hur man löser en labyrint. Konceptet ska vara enkelt: hitta nyckeln, hitta utgången. Från att skanna en QR-kod till att spela ska ta maximum 1 minut. Inget behov av handledningar eller komplexa förklaringar.

- Vilka specifika föremål/bonusar finns i spelet och hur påverkar de spelarens framsteg (t.ex. acceleration, skydd)?
**Svar**: Hastighetsökning, bättre syn (utökad synradie om dimma av krig implementeras), poängsamlingsobjekt som äpplen/mynt för high score, möjligen bokstavssamling för hemliga ordutmaningar.

- Vilka specifika föremål/handlingar kan användas för att påverka motståndaren (t.ex. sakta ner, blockera, fällor)?
**Svar**: Sömnpotion för att frysa motståndare i 2 sekunder och få dem att tappa nyckeln, förvirringsstrål som vänder om kontroller (vänster blir höger), fällor som kan placeras strategiskt vid utgången, bedövande projektiler.

- Vilka begränsningar/straff läggs på en spelare som påverkas av ett föremål?
**Svar**: Fryseffekter varar cirka 2 sekunder, förvirringsstrål vänder om joystick-kontroller, nyckel tappas när träffad av vissa föremål.

- Hur aktiveras dessa föremål/handlingar? Automatiskt när upphämtade, eller manuellt genom spelarval (med dedikerad knapp)?
**Svar**: Blandad approach - power-ups som hastighetsökning aktiveras automatiskt när man går över dem, strategiska föremål som vapen/fällor aktiveras manuellt med knappar (3 förmåga-knappar på höger sida av mobilskärm).

- Behöver en spelare se att motståndaren har använt ett föremål mot dem, och hur (visuellt, ljud)?
**Svar**: Primärt visuell feedback är viktigt på grund av bullrig miljö (100+ personer). Behöver se projektiler avfyras, splash-effekter när träffad, visuella indikatorer för statuseffekter. Ljudeffekter är sekundära.

- Vilken typ av rörelsemekanik används i labyrinten (tangentbord/piltangenter, svep, klick)?
**Svar**: Mobil: on-screen joystick med vänster tumme, förmågor med höger tumme. Desktop: WASD-tangenter med 4-riktnings rörelse, förmågor med tangentbordstangenter som JKL om mus inte är tillgänglig.

- Hur många föremål kan vara i labyrinten samtidigt?
**Svar**: Begränsat inventarium - kanske 3 olika förmågetyper, använd en och den fylls på efter några sekunder, eller samla nya från labyrinten.

2. Vinstvillkor, Varaktighet och Svårighet

- Vad är det exakta vinstvillkoret? Första att lämna, eller finns det ytterligare kriterier (poäng, samlade föremål)?
**Svar**: Primärt vinstvillkor är första person att nå utgången med nyckeln. Sidouppdrag som att samla bokstäver för ett hemligt ord kan ge bonuspriser, men huvudvinst är att nå utgången först.

- Vad händer när maximal speltid (5 minuter) tar slut? Oavgjort, vinst för den som kommit längst, eller förlust för båda?
**Svar**: Tid är inte en hård deadline. Spelet är designat så att 90% av spelarna slutför inom 5 minuter. För de återstående 10% är det okej om de spelar 7-8 minuter. Efter 5 minuter kan spelare få hjälp som kompassriktning till nyckeln.

- Ska labyrintstorleken vara fast eller dynamiskt genererad? Vilka är förväntade minimum och maximum storlekar?
**Svar**: En fast karta är tillräcklig för MVP. Väggar kan vara samma, men randomisera nyckelplacering, power-ups och utgångsposition. Eftersom de flesta spelare spelar bara en gång är det fortfarande en ny upplevelse varje gång.

- Hur många svårighetsnivåer ska spelet ha?
**Svar**: Inga svårighetsnivåer behövs - håll det enkelt. Samma spel för alla.

- Är slumphändelser tillåtna under spelandet (t.ex. vägar som ändras, nya föremål som spawnar)?
**Svar**: Inte nämnt som krav. Fokusera på kärnmekanik först.

3. Användargränssnitt och Display (UI/UX)

- Ska spelare kunna se varandras positioner på kartan/skärmen? Om ja, hur visas deras position (ikon, markör, minikarta)?
**Svar**: Spelare ser bara en begränsad viewport centrerad på sig själva (mobil visar liten del, dimma av krig möjlig). Åskådarskärm visar full karta med båda spelare synliga. Spelare kan "fuska" genom att titta på den stora skärmen, men detta skapar rolig social interaktion.

- Vilka element måste spelaren se på sin skärm (karta, tidur, statusfält för föremål)?
**Svar**: Spelaravatar med tydlig riktningsindikator (pil eller sprite), joystick-kontroller, 3 förmåga-knappar, inventarium/status, begränsad kartvy centrerad på spelare. Samma viewport-storlek oavsett skärmstorlek för rättvisa.

- Behöver statistik visas i realtid (t.ex. hastighet, procentuell framsteg, använda bonusar)?
**Svar**: Tidurvisning, poängräkning för high score, möjligen kompassriktning till motståndare eller nyckel efter viss tid.

- Hur ska en spelsession presenteras på den stora skärmen (en spelare åt gången, delad skärm, översiktskarta)?
**Svar**: Full översiktskarta som visar båda spelare samtidigt, inte delad skärm (skulle vara för svårt att se). Lärare kan växla mellan olika pågående sessioner om flera spel körs.

- Finns det krav på spelets design/stil (t.ex. retro, minimalistisk, futuristisk)?
**Svar**: Avatar måste matcha miljön tematiskt (t.ex. om trollkarlar, då fängelsemiljö). Fantasytema föreslaget med isometrisk karta. Annars ganska öppet, men behåll konsistens mellan karaktär och bakgrund.

- Krävs ljud (bakgrundsmusik, ljudeffekter för aktivering/interaktion)?
**Svar**: Bakgrundsmusik behövs inte. Ljudeffekter är sekundära på grund av bullrig miljö (100+ personer). Visuell feedback är viktigast, men några ljudeffekter för skjutning/handlingar kan inkluderas.

4. Multiplayer och Tekniska Krav

- Vad är det förväntade maximala antalet par som spelar samtidigt under evenemanget ("öppet hus")?
**Svar**: Maximum 4 samtidiga sessioner (8 spelare totalt). Bara cirka 10 personer kan fysiskt få plats runt båset ändå. Även om 30 sessioner körde skulle det inte vara en tung dataload.

- Är varje par helt oberoende, eller är interaktion/påverkan mellan olika spelpar möjlig?
**Svar**: Varje par är helt oberoende. Ingen interaktion mellan olika spelsessioner.

- Ska mobila enheter stödja fullständigt spelande (med kontroller) eller bara användas för visning/åskådarvy?
**Svar**: Fullständigt spelande på mobil med on-screen joystick och touch-kontroller. Måste fungera på både Android och iOS, inklusive telefoner 6-7 år gamla.

- Vilken serverarkitektur föredras: Client-Server eller Peer-to-Peer (P2P)?
**Svar**: Client-Server med enkel server. Allt speltillstånd hanterat på server och synkroniserat till klienter. Detta förhindrar sync-problem som inträffade i tidigare projekt där beräkningar gjordes på telefoner.

- Behöver spelresultat sparas (för statistik, topplistor och analys)? Om ja, vilken typ av databas föredras?
**Svar**: High score-system där spelare kan ange initialer för topp 10, liknande flipperspel. Visa slutpoäng och tid.

- Krävs någon form av autentisering/registrering av spelare?
**Svar**: Ingen autentisering behövs. Spelare matchas automatiskt - första redo spelare väntar på andra spelare att ansluta, sedan startar spel automatiskt.

- Hur ska spelarpositioner och tillstånd synkroniseras för att minimera effekten av nätverksfördröjning (lag)?
**Svar**: Mycket lite data behöver skickas - bara position och enstaka förmågeanvändning med riktning/hastighet. Server hanterar allt speltillstånd för att säkerställa synkronisering.

- Vad är den minsta uppsättningen funktioner som måste fungera för en framgångsrik demonstration på öppet hus-dagen?
**Svar**: MVP är en karta, nyckelsamling, utgångshittande, grundläggande multiplayer, åskådarvy. Föremål och förmågor är bra-att-ha men inte väsentliga.

- Finns det tillgänglighetskrav för spelare med funktionsvariationer (t.ex. färgblindhet, motoriska begränsningar)?
**Svar**: Inga speciella tillgänglighetsfunktioner krävs för detta sammanhang. Men bra designpraxis: olika avatarformer (inte bara färger) för spelare, hög kontrast, primärt visuella instruktioner snarare än text, tydlig distinktion mellan spelare och motståndare.

## Ytterligare Frågor Baserade på Expertintervju

5. Teknisk Implementering och Plattform

- Vilken teknisk stack föredras för implementering?
**Svar**: Webbaserad lösning föredras för enkel installation. Frontend: React, Vue eller Angular. Backend: C# Blazor, Python Flask/Django eller liknande. WebSockets för kommunikation. Undvik Unity eftersom det är komplext att installera och underhålla.

- Hur ska spelet hantera spelarurkopplingar?
**Svar**: Om spelare förlorar anslutning slutar spel för båda spelare med "Anslutning förlorad, spel avslutat"-meddelande. Båda återgår till startskärm. Ingen vinnare förklaras.

- Vad händer om någon griefare genom att medvetet koppla ur när de förlorar?
**Svar**: Inte ett problem - spelare är vänner från gymnasium som bara har kul. Det är inte en seriös konkurrenskraftig miljö.

6. Spelinstallation och Logistik

- Hur hanteras matchmaking?
**Svar**: Automatisk matchmaking - första redo spelare väntar på andra spelare att ansluta, sedan startar spel automatiskt. Inget val av motståndare för att minska komplexitet.

- Kan lärare/demonstratör åskåda specifika spel?
**Svar**: Ja, lärare får lista över pågående sessioner och kan välja vilken som ska visas på projektor. Kan växla mellan olika aktiva spel.

- Vad är målinstallationstiden från laptop till körande demo?
**Svar**: Maximum 2 minuter. Spel ska köras som webbtjänst på laptop eller som Docker-container på webbserver.

7. Spelinnehåll och Teman

- Finns det specifika visuella teman eller karaktärer som föredras?
**Svar**: Fantasytema föreslaget (trollkarlar/krigare på isometrisk fängelsekarta). Avatar måste matcha bakgrund tematiskt. Relativt öppet så länge det är konsekvent.

- Ska det finnas flera kartor?
**Svar**: En karta är tillräcklig för MVP. Kan randomisera nyckel-, föremåls- och utgångspositioner medan väggar hålls samma.

- Kan spelare se nyckelplatsen initialt?
**Svar**: Nej, nyckelplats är gömd. Utgång är synlig men spelare måste hitta var den är på kartan. Efter 5 minuter kan kompassriktning till nyckel ges som hjälp.

8. Poängsättning och Tävling

- Hur detaljerat ska poängsystemet vara?
**Svar**: Tidsbaserad poängsättning för snabb slutförande, plus valfri poängsamling (äpplen/mynt) för högre poäng. Möjligen bokstavssamling för hemliga ord bonuspriser.

- Ska orättvisa undvikas (t.ex. spawna bredvid nyckel)?
**Svar**: Perfekt rättvisa inte kritisk eftersom spelare bara spelar en gång. Kunde göra karta symmetrisk för rättvisa, men inte väsentligt.

- Behövs reprisvärde?
**Svar**: Inget reprisvärde krävs. Designad för engångsspelupplevelse som är engagerande nog att vara intressant men behöver inte djup för upprepat spelande.

9. Kontext och Syfte

- Varför valdes MazeRunner över den tidigare haptiska teknologidemon?
**Svar**: Tidigare system var coolt men krävde komplex hårdvaruinstallation, driverinstallationer och var opålitligt (gick sönder med OS-uppdateringar). Ville ha något som "alltid fungerar" - bara öppna laptop och kör på 2 minuter.

- Vad är huvudmålet för öppet hus-demonstrationen?
**Svar**: Engagera två spelare, skapa åskådarunderhållning, tjäna som isbrytare för konversationer om datavetenskapsutbildning. Ersätta "Är du intresserad av datavetenskap?" med "Vill du spela ett spel?"

- Hur långa ska spelandet-sessioner vara?
**Svar**: 5 minuters mål, men flexibelt. 90% ska slutföra inom 5 minuter, återstående 10% kan spela 7-8 minuter. Målet är snabbt engagemang, inte utökat spelande.

- Kommer detta projekt användas i flera år?
**Svar**: Ja, Josef har skapat nya spelprojekt varje år i 4 år. Tidigare spel hade problem (sync-problem, Unity export-komplexitet). Söker tillförlitlig, underhållbar lösning.
