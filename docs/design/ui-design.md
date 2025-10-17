# 3.4 Användargränssnittsdesign

## Spelargränssnitt (Mobil/Desktop)

### Kärn React-komponenter
- **GameViewport**: Begränsad labyrintvy centrerad på spelare
- **MovementControls**: 8-riktnings rörelsehantering
  - Mobil: On-screen joystick (vänster tumme)
  - Desktop: WASD-tangenter med full 8-riktnings rörelse
- **AbilityBar**: 3 förmåga-knappar (höger sida på mobil, JKL-tangenter på desktop)
- **StatusDisplay**: Tidur, poäng, inventarieindikatorer, kompasshjälp
- **PlayerAvatar**: Tydlig riktningsindikator (pil eller sprite som visar vändriktning)
- **ConnectionStatus**: Nätverksstatus och spelmeddelanden

### Kontrollayout Specifikationer
- **Mobillayout**: Vänster tumme för joystick-rörelse, höger tumme för förmåga-aktivering
- **Desktoplayout**: WASD för rörelse, JKL-tangenter för förmågor (om mus inte tillgänglig)
- **8-Riktnings Rörelse**: Full diagonal rörelsehantering (inte begränsad till 4 riktningar)
- **Förmåga-aktivering**: Manuell aktivering för strategiska föremål, auto-upphämtning för power-ups

### Hjälp- och Stödsystem
- **Kompasshjälp**: Efter 5 minuter, visa riktningsindikatorer till nyckel eller motståndare
- **Visuell Feedback**: Projektilspår, splash-effekter, statuseffektindikatorer
- **Inventarievisning**: Visa nuvarande förmågor och cooldown-tidtagare

### Responsiv Design Krav
- Minimum skärmstorlek: 4 tum (320x568px)  
- Maximum skärmstorlek: 27 tum (2560x1440px)
- Konsekvent spelupport viewport-ratio över alla enheter
- Touch-vänliga knappstorlekar (minimum 44px touch-mål)

*[PLACEHOLDER: Mobil UI-mockup som visar joystick-kontroller, förmåga-knappar och spelviewport]*

*[PLACEHOLDER: Desktop UI-mockup som visar tangentbordskontroller och större spelområde]*

## Åskådargränssnitt (Stor Skärm)

### Displayelement
- **Full labyrintöversikt** med båda spelare synliga samtidigt
- **Spelarstatusinformation** (namn, poäng, nuvarande förmågor, inventarie)
- **Speltidur och sessionsinformation** med flexibel tidsvisning
- **Vinnarförkunnan och firande-effekter** med slutpoäng
- **Sessionsväljare** för växling mellan flera samtidiga spel
- **Aktiva spellista** som visar alla pågående sessioner med spelarantal
- **Kompassindikatorer** när hjälpsystem är aktivt (efter 5 minuter)

### Lärarkontroller
- **Sessionväxling**: Dropdown eller lista för att välja vilket spel som ska visas
- **Spelöversikt**: Snabb status för alla aktiva sessioner
- **Poängvisning**: Realtidspoäng inklusive sidoutmaningar (bokstäver, poäng)
- **Help activation**: Visual indication when compass help is provided to players

*[PLACEHOLDER: Spectator view mockup showing complete maze, both players, and status information]*

## Visual Design Principles
- **High Contrast**: Clear distinction between players, walls, items, and background
- **Minimal Text**: Rely on icons and visual cues rather than written instructions
- **Consistent Theme**: Fantasy/dungeon aesthetic with matching characters and environment  
- **Accessibility**: Different shapes and patterns, not just colors, for key elements

## React Component Structure
```
App
├── GameContainer
│   ├── PlayerView
│   │   ├── MazeCanvas
│   │   ├── ControlPanel
│   │   └── StatusBar
│   └── SpectatorView
│       ├── FullMazeView
│       └── SessionSelector
└── ConnectionManager
```