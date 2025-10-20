# 3. Systemdesign

## Innehållsförteckning
- [3.1 Statisk Design](#31-statisk-design) (Compile-time)
  - [3.1.1 Klassdiagram](design/classes.md)
  - [3.1.2 Moduldiagram](design/architecture.md)
- [3.2 Dynamisk Design](#32-dynamisk-design) (Run-time)
  - [3.2.1 Aktivitetsdiagram](design/behavior.md)
  - [3.2.2 Sekvensdiagram](design/behavior.md#sekvensdiagram)
  - [3.2.3 Tillståndsdiagram](design/behavior.md#tillståndsdiagram)

## Översikt

Denna sektion tillhandahåller omfattande systemdesignspecifikationer för MazeRunner, täcker statisk design (compile-time struktur) och dynamisk design (runtime-beteende).

**Teknisk Stack**: React-frontend med C#-backend, WebSocket-kommunikation, SQLite-databas

## 3.1 Statisk Design

Statisk design beskriver systemets struktur vid kompileringstid (compile-time), inklusive klasser, moduler och deras relationer.

### 3.1.1 Klassdiagram
Se [Klassdiagram](design/classes.md) för detaljerad klassstruktur.

### 3.1.2 Moduldiagram
Se [Moduldiagram och Systemarkitektur](design/architecture.md) för systemarkitektur och modulära komponenter.

## 3.2 Dynamisk Design

Dynamisk design beskriver systemets beteende vid körtid (runtime), inklusive interaktioner, tillståndsövergångar och aktivitetsflöden.

### 3.2.1 Aktivitetsdiagram
### 3.2.2 Sekvensdiagram
### 3.2.3 Tillståndsdiagram

Se [Dynamisk Design och Beteende](design/behavior.md) för aktivitets-, sekvens- och tillståndsdiagram.

För ytterligare designspecifikationer, se också:
- [Användargränssnittsdesign](design/ui-design.md)
- [Datahantering](design/data.md)
- [Felhantering](design/error-handling.md)
- [Säkerhet](design/security.md)