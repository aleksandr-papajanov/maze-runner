<p align="center">
  <img src="../../assets/logo.png" alt="Logo" width="100%" />
</p>

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

## Användargränssnitt (UI)

### Spelarvy
- Mobil: on‑screen joystick (vänster), tre förmågeknappar (höger), statusfält (tid, poäng, nyckel, kompass), begränsad sikt (fog of war)
- Desktop: WASD för rörelse, JKL för förmågor, samma statusfält och siktlogik som mobil

![Device-preview](/diagrams/2.5.1-device-preview.jpg)

### Åskådarvy
- Full kartöversikt utan fog of war, båda spelare synliga
- Spelarstatus på vänster/höger sida, stor timer upptill, sessionväljare nertill

![Screen preview](/diagrams/2.5.2-screen-preview.jpg)

## Storyboards (för otydliga användarfall)

### Storyboard 1: Använd förmåga (Sömneliksir) – UC4, FK006–FK012
**Scenario:** P1 ser P2 och använder Sömneliksir för att frysa motståndaren.

1) P1 (röd) ser P2 (blå) med nyckeln  → 2) P1 trycker Sömneliksir-knappen → 3) P2 fryser (2s), nyckeln faller → 4) P1 plockar upp nyckeln och springer mot utgången

![Storyboard](/diagrams/2.5.4-storyboard.jpg)

### Storyboard 2: QR‑kod → vänteläge → spelstart – UC1, FK005
**Scenario:** Elev skannar QR-kod och kommer in i spel.

1) QR på projektor → 2) Telefon öppnar URL → 3) Vänteskärm "Väntar på motståndare..." → 5) Nedräkning 3‑2‑1 → 6) Spelvy visas

![Storyboard](/diagrams/2.5.5-storyboard.jpg)

### Storyboard 3: Hitta nyckel och nå utgången – UC3, UC5, FK002–FK003
**Scenario:** P1 hittar nyckeln, springer mot utgången och vinner.

1) P1 rör sig genom labyrinten (fog of war) → 2) P1 ser nyckelikonen → 3) P1 går över nyckeln, den försvinner och visas i inventariet → 4) Kompass aktiveras och pekar mot utgången → 5) P1 når utgången (markerad dörr/portal) → 6) "Victory!" visas, P2 får "Defeat" → 7) Resultatskärm med tid och poäng

![Storyboard](/diagrams/2.5.6-storyboard.jpg)
