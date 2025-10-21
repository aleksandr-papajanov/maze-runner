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
| UC9: Växla sessioner | Organizer | Medel | **Ja** | Specifikt arbetsflöde, auto-switching logic, UI-detaljer |
| UC10: Hantera tekniska problem | Organizer | Hög | Nej | Ad-hoc troubleshooting, inte standardiserat |
| UC11: Titta på åskådarvy | Spectator | Låg | Nej | Passiv observation, självförklarande |
| UC12: Matcha spelare | System | Medel | Nej | Automatisk process, täcks av UC1 |
| UC13: Synkronisera tillstånd | System | Hög | Nej | Teknisk implementation, täcks av arkitektur |
| UC14: Hantera urkoppling | System | Hög | **Ja** | Kritisk error handling, exakta timings krävs, flera scenarier |
| UC15: Randomisera karta | System | Låg | Nej | Automatisk process, självförklarande |
| UC16: Detektera vinst | System | Låg | Nej | Enkel condition check, självförklarande |

# 2.2 Användarfalldiagram

## Övergripande Systeminteraktion

![Usecase diagram](/diagrams/2.2.1-usecase-diagram.png)

## Spelarinteraktion - Detaljerat


![Usecase diagram](/diagrams/2.2.2-usecase-diagram.png)

---

# 2.3 Detaljerade Användarfall

*Följande användarfall kräver detaljbeskrivning för att undvika tolkningsosäkerhet.*

## UC1: Anslut via QR-kod

**Aktör**: Spelare  
**Syfte**: Snabb anslutning utan URL-inmatning  
**Förvillkor**: Spelserver aktiv, enhet med kamera, <10 spelare

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

## UC9: Växla sessioner

**Aktör**: Eventorganisatör  
**Syfte**: Visa olika aktiva spel på åskådardisplay  
**Förvillkor**: Minst en session aktiv, åskådarvy aktiverad

**Huvudflöde**:
1. Organisatör väljer session
2. System växlar åskådardisplay med fade-effect
3. Åskådarvy visar vald session tills ny session väljs

**Alternativt flöde**:
- Endast en session → växling inaktiverad
- Session avslutas → automatisk switch

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