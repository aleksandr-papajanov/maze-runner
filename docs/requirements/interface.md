# 2.5 Interfacespecifikation och Storyboards

## Översikt
Enkla storyboards för otydliga användarfall och ett grundläggande UI‑förslag.

Relaterade användarfall (från Actors/Use Cases):
- UC1: Anslut via QR‑kod (Storyboards 2)
- UC4: Använd förmågor (Storyboard 1, aktivitetsdiagram)
- UC9: Växla sessioner (Storyboard 3)

Relaterade funktionella krav (FK): FK005, FK006–FK012, FK025–FK026, FK027, FK031–FK033.

---

## Förslag på användargränssnitt (UI)

### Spelarvy
- Mobil: on‑screen joystick (vänster), tre förmågeknappar (höger), statusfält (tid, poäng, nyckel, kompass), begränsad sikt (fog of war)
- Desktop: WASD för rörelse, JKL för förmågor, samma statusfält och siktlogik som mobil

**[PLACEHOLDER: Bild 2.5.1 – Spelarvy (mobil + desktop) enkla wireframes]**

### Åskådarvy
- Full kartöversikt utan fog of war, båda spelare synliga
- Spelarstatus på vänster/höger sida, stor timer upptill, sessionväljare nertill

**[PLACEHOLDER: Bild 2.5.2 – Åskådarvy enkel wireframe]**

## Storyboards (för otydliga användarfall)

### Storyboard 1: Använd förmåga (Sömneliksir) – UC4, FK006–FK012
**Scenario:** P1 ser P2 och använder Sömneliksir för att frysa motståndaren.

1) P1 ser P2 i sin siktcirkel → 2) P1 trycker förmågeknappen → 3) Projektil syns mot P2 → 4) Träff: P2 "fryser" i 2s → 5) P1s knapp visar "10s" cooldown → 6) P2 rör sig igen → 7) Cooldown klar

**[PLACEHOLDER: Bild 2.5.4 – 7‑rutor storyboard för förmågeanvändning]**

### Storyboard 2: QR‑kod → vänteläge → spelstart – UC1, FK005
**Scenario:** Elev skannar QR-kod och kommer in i spel.

1) QR på projektor → 2) Telefon öppnar URL → 3) Vänteskärm "Väntar på motståndare..." → 4) "Motståndare hittad!" → 5) Nedräkning 3‑2‑1 → 6) Spelvy visas

**[PLACEHOLDER: Bild 2.5.5 – 6‑rutor storyboard för anslutningsflöde]**

### Storyboard 3: Lärare växlar session i åskådarvy – UC9, FK025–FK026
**Scenario:** Läraren byter mellan aktiva matcher.

1) Visar Spel 1 → 2) Sessionlista öppnas → 3) Välj Spel 2 → 4) Fade → 5) Visar Spel 2 → 6) (Valfritt) Auto‑växla på

**[PLACEHOLDER: Bild 2.5.6 – 6‑rutor storyboard för sessionväxling]**
