# 2.2 Funktionella Krav

## Grundläggande Spelmekanik (Måste Ha)
- **FK001**: Två spelare tävlar samtidigt i samma labyrintinstans
- **FK002**: Spelare måste hitta en slumpmässigt placerad nyckel innan de kan nå utgången
- **FK003**: Första spelaren som når utgången med nyckeln vinner spelet
- **FK004**: Realtidssynkronisering av spelarpositioner (<100ms latens)
- **FK005**: QR-kodåtkomst - spelare skannar kod för att gå med i spel inom max 1 minut

## Förmågesystem (Bör Ha - Trevligt att Ha, Inte Nödvändigt för MVP)
- **FK006**: Sömnelixir - fryser motståndaren i 2 sekunder och tvingar dem att tappa nyckeln
- **FK007**: Förvirrningsstråle - vänder på motståndarens joystickkontroller (vänster blir höger)
- **FK008**: Strategiska fällor - kan placeras vid utgång eller nyckelplatser
- **FK009**: Bedövande projektiler - synliga projektiler som kan avfyras mot motståndare
- **FK010**: Blandat aktiveringssystem - power-ups aktiveras automatiskt vid upplockning, strategiska föremål använder manuella knappar
- **FK011**: Tre förmågeknappar på mobil (höger sida), tangentbordstangenter (JKL) på dator
- **FK012**: Begränsat inventory - max 3 olika förmågetyper, påfylls efter användning eller samlas i labyrinten

## Spelinnehåll (Måste Ha)
- **FK013**: En enda labyrintlayout med fast väggstruktur för konsekvens
- **FK014**: Slumpmässig kartgenerering - slumpa nyckelplacering, utgångsposition och power-up positioner varje spel
- **FK015**: Begränsad viewport per spelare (dimma av krig-effekt)
- **FK016**: Visuell feedback för alla spelaraktioner och förmågeanvändning
- **FK017**: Automatisk spelavslutning efter vinst eller spelarurkoppling

## Poängsättning och Sidoutmaningar (Bör Ha)
- **FK018**: Poängsamlingsobjekt (äpplen/mynt) utspridda i labyrinten för high score
- **FK019**: Bokstavssamlingsutmaning - samla bokstäver för att stava hemligt ord för bonuspriser
- **FK020**: Tidsbaserad poängsättning - snabbare genomförande ger högre poäng
- **FK021**: High score-topplista med topp 10-poster och initialer (flipperspelsstil)
- **FK022**: Bonuspoängsystem för att slutföra sidoutmaningar samtidigt som man vinner huvudspelet

## Flerspelarstöd (Måste Ha)  
- **FK023**: Stöd för 5 samtidiga spelsessioner (10 spelare totalt)
- **FK024**: Automatisk matchmaking - första tillgängliga spelare paras ihop med nästa anslutande spelare
- **FK025**: Åskådarvy visar hela labyrinten och båda spelarnas positioner på separat skärm
- **FK026**: Lärare kan växla mellan olika aktiva spelsessioner på åskådardisplay

## Användargränssnitt (Måste Ha)
- **FK027**: Kontroller anpassas till enhetstyp (touchjoystick vs tangentbord)
- **FK028**: Tydlig visuell distinktion mellan spelaravatarer med riktningsindikatorer
- **FK029**: Spelstatusvisning (timer, förmågor, poäng, inventory)
- **FK030**: 8-riktningsrörelse (inte bara 4-riktningar)
- **FK031**: Mobilkontroller - vänster tumme joystick, höger tumme förmågeknappar
- **FK032**: Skrivbordskontroller - WASD-rörelse, JKL-förmågeaktivering
- **FK033**: Kompasshjälpsystem - efter 5 minuter, visa riktning till nyckel eller motståndare
- **FK034**: Viewport-rättvisa - samma viewport-storlek oavsett enhetsskärmstorlek för rättvist spel

## Valfria Funktioner (Bör Ha)
- **FK035**: Hastighetsökning power-up (aktiveras automatiskt vid upplockning)
- **FK036**: Förbättrad syn power-up (utökad vyradie)
- **FK037**: Resultatskärm efter spel med vinnardeklaration, slutpoäng och tid
- **FK038**: Flexibla tidsgränser - 90% slutför inom 5 minuter, tillåt 7-8 minuter för återstående 10%