# 2.5 Interfacespecifikation och Storyboards

## Översikt
Enkla storyboards för otydliga användarfall och ett grundläggande UI‑förslag.

Relaterade användarfall (från Actors/Use Cases):
- UC1: Anslut via QR‑kod (Storyboard 2)
- UC3: Samla nyckel (Storyboard 3)
- UC4: Använd förmågor (Storyboard 1, aktivitetsdiagram)
- UC5: Nå utgång (Storyboard 3)

Relaterade funktionella krav (FK): FK002–FK003, FK005, FK006–FK012, FK027, FK031–FK033.

---

## Förslag på användargränssnitt (UI)

### Spelarvy
- Mobil: on‑screen joystick (vänster), tre förmågeknappar (höger), statusfält (tid, poäng, nyckel, kompass), begränsad sikt (fog of war)
- Desktop: WASD för rörelse, JKL för förmågor, samma statusfält och siktlogik som mobil

![Bild](/diagrams/2.5.1-interface.jpg)

### Åskådarvy
- Full kartöversikt utan fog of war, båda spelare synliga
- Spelarstatus på vänster/höger sida, stor timer upptill, sessionväljare nertill

![Bild](/diagrams/2.5.2-interface.jpg)

## Storyboards (för otydliga användarfall)

### Storyboard 1: Använd förmåga (Sömneliksir) – UC4, FK006–FK012
**Scenario:** P1 ser P2 och använder Sömneliksir för att frysa motståndaren.

1) P1 ser P2 i sin siktcirkel → 2) P1 trycker förmågeknappen → 3) Projektil syns mot P2 → 4) Träff: P2 "fryser" i 2s → 5) P1s knapp visar "10s" cooldown → 6) P2 rör sig igen → 7) Cooldown klar

![Bild](/diagrams/2.5.4-interface.jpg)

### Storyboard 2: QR‑kod → vänteläge → spelstart – UC1, FK005
**Scenario:** Elev skannar QR-kod och kommer in i spel.

1) QR på projektor → 2) Telefon öppnar URL → 3) Vänteskärm "Väntar på motståndare..." → 4) "Motståndare hittad!" → 5) Nedräkning 3‑2‑1 → 6) Spelvy visas

![Bild](/diagrams/2.5.5-interface.jpg)

### Storyboard 3: Hitta nyckel och nå utgången – UC3, UC5, FK002–FK003
**Scenario:** P1 hittar nyckeln, springer mot utgången och vinner.

1) P1 rör sig genom labyrinten (fog of war) → 2) P1 ser nyckelikonen → 3) P1 går över nyckeln, den försvinner och visas i inventariet → 4) Kompass aktiveras och pekar mot utgången → 5) P1 når utgången (markerad dörr/portal) → 6) "Victory!" visas, P2 får "Defeat" → 7) Resultatskärm med tid och poäng

![Bild](/diagrams/2.5.6-interface.jpg)
