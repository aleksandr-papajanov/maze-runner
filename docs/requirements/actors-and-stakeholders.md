<p align="center">
  <img src="../../assets/logo.png" alt="Logo" width="100%" />
</p>

# 2.1 Användarkarakteristik - Aktörer

## Primära Aktörer och Användare

### Spelare (Gymnasiestudenter)
- **Ålder:** 16-25 år  
- **Teknisk kompetens:** Grundläggande webbexpertis  
- **Engagemang:** 3-5 minuters sessioner  
- **Beteende:** Digitala infödingar, vana vid smartphone-spel  
- **Förväntningar:** Omedelbar feedback, tydlig visuell kommunikation

**Användarfall (UC):**
1. UC1: Anslut via QR-kod  
2. UC2: Navigera labyrint  
3. UC3: Samla nyckel  
4. UC4: Använd förmågor  
5. UC5: Nå utgång (vinna)  
6. UC6: Ange high score  

---

### Eventorganisatör (Universitetspersonal)
- **Roll:** Josef Hallberg  
- **Ansvar:** Demonstrera system, visa studentarbete  
- **Behov:** Snabb setup, pålitligt system

**Användarfall:**
7. UC7: Starta spelserver  
8. UC8: Aktivera åskådarvy  
9. UC9: Växla sessioner  
10. UC10: Hantera tekniska problem  

---

### Åskådare (Öppet Hus-Deltagare)
- **Beteende:** Observerar tävlingar  
- **Interaktion:** Kan ge råd/uppmuntran

**Användarfall:**
11. UC11: Titta på åskådarvy  

---

### System (Automatisk aktör)
**Användarfall:**
12. UC12: Matcha spelare  
13. UC13: Synkronisera speltillstånd  
14. UC14: Hantera spelarurkoppling  
15. UC15: Randomisera spelkarta  
16. UC16: Detektera vinst  

---

## Användarfallsmatris

| Användarfall | Aktör | Komplexitet | Kräver detaljbeskrivning? | Motivering |
|--------------|-------|-------------|---------------------------|------------|
| UC1: Anslut via QR-kod | Spelare | Medel | **Ja** | Flera kantfall (full session, inkompatibel enhet), kritisk entry point |
| UC2: Navigera labyrint | Spelare | Låg | Nej | Standardrörelse, självförklarande |
| UC3: Samla nyckel | Spelare | Låg | Nej | Enkel collision detection, självförklarande |
| UC4: Använd förmågor | Spelare | Hög | **Ja** | Komplex logik, olika förmågetyper, cooldowns, kantfall |
| UC5: Nå utgång (vinna) | Spelare | Låg | Nej | Enkelt vinstvillkor, självförklarande |
| UC6: Ange high score | Spelare | Låg | Nej | Standard forminteraktion |
| UC7: Starta spelserver | Organizer | Låg | Nej | Teknisk setup, dokumenteras separat |
| UC8: Aktivera åskådarvy | Organizer | Låg | Nej | Enkel aktivering, självförklarande |
| UC9: Växla sessioner | Organizer | Låg | Nej | Alla sessioner visas på en skärm, enkel navigation |
| UC10: Hantera tekniska problem | Organizer | Hög | Nej | Ad-hoc troubleshooting, inte standardiserat |
| UC11: Titta på åskådarvy | Spectator | Låg | Nej | Passiv observation, självförklarande |
| UC12: Matcha spelare | System | Medel | Nej | Automatisk process, täcks av UC1 |
| UC13: Synkronisera tillstånd | System | Hög | Nej | Teknisk implementation, täcks av arkitektur |
| UC14: Hantera urkoppling | System | Hög | **Ja** | Kritisk error handling, exakta timings krävs, flera scenarier |
| UC15: Randomisera karta | System | Låg | Nej | Automatisk process, självförklarande |
| UC16: Detektera vinst | System | Låg | Nej | Enkel condition check, självförklarande |

# 2.2 Användarfalldiagram

## 2.2.1 Övergripande Systeminteraktion

Detta diagram visar alla aktörer och deras användarfall i MazeRunner-systemet:

**Fyra primära aktörer:**
1. **Spelare** (Gymnasiestudenter) - Huvudanvändare som spelar spelet
   - UC1-UC6: Från anslutning till high score-inmatning

2. **Eventorganisatör** (Josef) - Kör demon på öppet hus
   - UC7-UC10: Serverhantering, åskådarvy, troubleshooting

3. **Åskådare** (Publik) - Observerar på storskärm
   - UC11: Passiv observation av alla aktiva sessioner

4. **System** (Automatisk) - Bakgrundsprocesser
   - UC12-UC16: Matchmaking, synkronisering, vinst-detection

**Include-relationer** visar beroenden:
- UC1 (Anslut) → UC12 (Matcha spelare): Automatisk matchmaking vid anslutning
- UC2-UC4 (Spelhandlingar) → UC13 (Synkronisera): All interaktion kräver realtidssynk
- UC5 (Nå utgång) → UC16 (Detektera vinst): System kontrollerar vinstvillkor

[![Usecase diagram](/diagrams/2.2.1-usecase-diagram.png)](/diagrams/2.2.1-usecase-diagram.png)

<p align="center">
  <a href="/diagrams/2.2.1-usecase-diagram.puml">View PlantUML source</a>
</p>

## 2.2.2 Spelarinteraktion - Detaljerat

Detta diagram fokuserar på spelarens användarfall med implementationsdetaljer:

**UC2: Navigera labyrint**
- **UC2.1**: Mobil kontroller (on-screen joystick, vänster tumme)
- **UC2.2**: Desktop kontroller (WASD/piltangenter)
- **UC2.3**: Fog of war (cirkulär viewport, begränsad sikt)

**UC4: Använd förmågor** (Fyra typer)
- **UC4.1 - Stun Shot**: Fryser motståndare 2 sekunder, tvingar tappa nyckel, 10s cooldown
- **UC4.2 - Förvirringsstrål**: Inverterar kontroller (vänster→höger), 15s cooldown
- **UC4.3 - Placera fälla**: Aktiveras när motståndare går över, 20s cooldown
- **UC4.4 - Hastighetsökning**: Auto-aktiveras vid insamling, tidsbaserad effekt

**UC5: Nå utgång**
- **Include UC3**: Måste ha samlat nyckel först
- **Extend UC6**: Valfri high score-inmatning efter vinst

**UML-relationer:**
- **Generalization** (`<|--`): UC2.1 och UC2.2 är specialiseringar av UC2
- **Include** (`..>`): Obligatoriskt beroende (måste ha nyckel för att vinna)
- **Extend** (`..>`): Valfri funktion (high score är frivillig)

[![Usecase diagram](/diagrams/2.2.2-usecase-diagram.png)](/diagrams/2.2.2-usecase-diagram.png)

<p align="center">
  <a href="/diagrams/2.2.2-usecase-diagram.puml">View PlantUML source</a>
</p>

---

# 2.3 Detaljerade Användarfall

*Följande användarfall kräver detaljbeskrivning för att undvika tolkningsosäkerhet.*

## UC1: Anslut via QR-kod

**Aktör**: Spelare  
**Syfte**: Snabb anslutning utan URL-inmatning  
**Förvillkor**: Spelserver aktiv, enhet med kamera, <8 spelare

**Huvudflöde**:
1. Spelare skannar QR-kod eller öppnar URL
2. System visar vänterum "Väntar på motståndare..."
3. System matchar spelare (UC12)
4. Spel börjar när match fullständig

**Alternativt flöde**:
- Session full → meddelande, auto-retry
- Inkompatibel webbläsare → felmeddelande

**Eftervillkor**: Spelare ansluten och väntar i session

---

## UC4: Använd förmågor

**Aktör**: Spelare  
**Syfte**: Taktiska verktyg mot motståndare  
**Förvillkor**: Aktiv spelsession, förmåga i inventory, ej på cooldown

**Huvudflöde**:
1. Spelare aktiverar förmåga
2. System kontrollerar cooldown och inventory
3. Effekt appliceras (t.ex. Stun Shot, Förvirringsstrål)
4. Cooldown startas, speltillstånd synkroniseras (UC13)

**Sub-Use Cases**:
- **UC4.1: Stun Shot** → Fryser motståndare 2s, tappar nyckel
- **UC4.2: Förvirringsstrål** → Vänder kontroller 5s
- **UC4.3: Placera fälla** → 30s timeout, 20s cooldown
- **UC4.4: Hastighetsökning** → +50% speed, 5s duration

**Alternativt flöde**: Cooldown → feedback utan effekt

---

## UC14: Hantera spelarurkoppling

**Aktör**: System  
**Syfte**: Säker avslut vid nätverksproblem  
**Förvillkor**: Spelare i aktiv session, WebSocket-anslutning

**Huvudflöde**:
1. Heartbeat-ping från klient (30s intervall)
2. Missad pong → start reconnection grace period (10s)
3. Återanslutning lyckas → speltillstånd återställs
4. Misslyckad → session avslutas, resurser frigörs

**Alternativt flöde**:

Båda spelare kopplar ur → session avslutas direkt

Urkoppling under matchmaking → tas bort från kö

Eftervillkor: Session avslutad eller spel fortsätter normalt