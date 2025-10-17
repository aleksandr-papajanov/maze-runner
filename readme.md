# MazeRunner Projektdokumentation

## 🎯 Projektöversikt

MazeRunner är ett realtid multiplayer labyrintspel designat för universitets öppet hus-evenemang på Luleå Tekniska Universitet (LTU). Spelet tjänar som ett interaktivt demonstrationsverktyg som engagerar gymnasiestudenter samtidigt som det visar upp moderna webbutvecklingskapaciteter.

### Nyckelfunktioner
- **Realtid multiplayer**: Två spelare tävlar samtidigt
- **Plattformsoberoende**: Fungerar på smartphones, surfplattor och desktop-webbläsare
- **Åskådarläge**: Stor skärmdisplay för publikengagemang
- **Snabb installation**: Under 2 minuter från uppstart till spelbart tillstånd
- **Ingen installation**: Webbläsarbaserad, inga app-nedladdningar krävs

## 🛠 Teknisk Stack

- **Frontend**: React med TypeScript
- **Backend**: C# med ASP.NET Core
- **Realtidskommunikation**: SignalR (WebSocket)
- **Databas**: SQLite för high scores
- **Distribution**: Enkel server på laptop

## 📚 Dokumentationsstruktur

### 📋 Kärndokumentation
- **[1. Introduktion](docs/1-introduction.md)** - Projektbakgrund och mål
- **[2. Kravspecifikation](docs/2-requirements-specification.md)** - Systemkrav och användningsfall  
- **[3. Systemdesign](docs/3-system-design.md)** - Teknisk arkitektur och design
- **[4. Projektutförande](docs/4-project-execution.md)** - Projekthantering och tidslinje

### 📖 Stödjande Dokument
- **[Spelvision](game-vision.md)** - Komplett speldesignöversikt
- **[Expertintervju](questions.md)** - Intressent frågor och svar

### 🗂 Detaljerade Moduler
Varje huvuddokument länkar till fokuserade undermoduler:
- **Introduktion**: Bakgrund, mål, omfattning, kontext, begränsningar
- **Krav**: Intressenter, funktionella/icke-funktionella krav, användningsfall
- **Design**: Arkitektur, klasser, beteende, UI, data, säkerhet
- **Utförande**: Teamstruktur, tidslinje, risker, kvalitetssäkring

## 🚀 Snabbstart

### För Granskare
1. Börja med [Spelvision](game-vision.md) för fullständig förståelse
2. Granska [Introduktion](docs/1-introduction.md) för projektkontext
3. Undersök [Krav](docs/2-requirements-specification.md) för detaljerade specifikationer
4. Studera [Systemdesign](docs/3-system-design.md) för teknisk arkitektur

### För Utvecklare
1. Granska [Systemarkitektur](docs/design/architecture.md) för teknisk översikt
2. Studera [Klassstruktur](docs/design/classes.md) för implementeringsdetaljer
3. Kontrollera [UI-design](docs/design/ui-design.md) för gränssnittsspecifikationer
4. Undersök [Datahantering](docs/design/data.md) för databasschema

### För Projektledare
1. Granska [Projekttidslinje](docs/execution/timeline.md) för schemaläggning
2. Studera [Riskhantering](docs/execution/risk-management.md) för potentiella problem
3. Kontrollera [Resurskrav](docs/execution/resources.md) för planering
4. Undersök [Kvalitetssäkring](docs/execution/quality-assurance.md) för standarder

## 👥 Teaminformation

- **Teamstorlek**: 2 medlemmar
- **Projektvaraktighet**: 8 timmars dokumentationsfas
- **Metodik**: Kollaborativ ansats med delade ansvarsområden
- **Intressent**: Josef Hallberg (LTU Datavetenskap Avdelning)

### Arbetsansats
- **Kollaborativ Utveckling**: Båda medlemmar arbetar tillsammans på alla projektaspekter utan hierarki
- **Delade Ansvarsområden**: Gemensamt arbete med kravanalys, systemdesign och kvalitetssäkring
- **Kamratgranskning**: Kontinuerlig samarbete med ömsesidig granskning av alla leverabler
- **Jämn Bidrag**: Båda medlemmar bidrar lika till alla dokumentationsområden

## 📄 Licens

Detta projekt utvecklas som en del av en universitetskurs på Luleå Tekniska Universitet (LTU).

---

**Senast Uppdaterad**: Oktober 2025  
**Kurs**: Mjukvaruteknik  
**Institution**: Luleå Tekniska Universitet

## Laboratoriemål
Att demonstrera förståelse av mjukvarudesignprinciper genom att skapa ett välstrukturerat, dokumenterat och testat system.