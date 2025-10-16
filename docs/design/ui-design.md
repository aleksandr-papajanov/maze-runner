# 3.4 User Interface Design

## Player Interface (Mobile/Desktop)

### Core React Components
- **GameViewport**: Limited maze view centered on player
- **MovementControls**: 8-directional movement support
  - Mobile: On-screen joystick (left thumb)
  - Desktop: WASD keys with full 8-directional movement
- **AbilityBar**: 3 ability buttons (right side on mobile, JKL keys on desktop)
- **StatusDisplay**: Timer, score, inventory indicators, compass help
- **PlayerAvatar**: Clear direction indicator (arrow or sprite showing facing direction)
- **ConnectionStatus**: Network status and game messages

### Control Layout Specifications
- **Mobile Layout**: Left thumb for joystick movement, right thumb for ability activation
- **Desktop Layout**: WASD for movement, JKL keys for abilities (if mouse unavailable)
- **8-Directional Movement**: Full diagonal movement support (not limited to 4 directions)
- **Ability Activation**: Manual activation for strategic items, auto-pickup for power-ups

### Help and Assistance Systems
- **Compass Help**: After 5 minutes, display directional indicators to key or opponent
- **Visual Feedback**: Projectile trails, splash effects, status effect indicators
- **Inventory Display**: Show current abilities and cooldown timers

### Responsive Design Requirements
- Minimum screen size: 4 inches (320x568px)  
- Maximum screen size: 27 inches (2560x1440px)
- Consistent gameplay viewport ratio across all devices
- Touch-friendly button sizes (minimum 44px touch targets)

*[PLACEHOLDER: Mobile UI mockup showing joystick controls, ability buttons, and game viewport]*

*[PLACEHOLDER: Desktop UI mockup showing keyboard controls and larger game area]*

## Spectator Interface (Large Screen)

### Display Elements
- **Full maze overview** with both players visible simultaneously
- **Player status information** (names, scores, current abilities, inventory)
- **Game timer and session information** with flexible time display
- **Winner announcement and celebration effects** with final scores
- **Session selector** for switching between multiple concurrent games
- **Active games list** showing all ongoing sessions with player counts
- **Compass indicators** when help system is active (after 5 minutes)

### Teacher Controls
- **Session switching**: Dropdown or list to select which game to display
- **Game overview**: Quick status of all active sessions
- **Score display**: Real-time scoring including side challenges (letters, points)
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