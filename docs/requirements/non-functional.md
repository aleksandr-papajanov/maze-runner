# 2.3 Non-Functional Requirements

## Performance Requirements
- **NFR001**: Game setup time <2 minutes from laptop startup to playable state
- **NFR002**: Player movement response time <100ms under normal network conditions
- **NFR003**: Support 5 concurrent sessions without performance degradation
- **NFR004**: Target 90% of games complete within 5 minutes, allow 7-8 minutes for remaining 10%
- **NFR005**: Compass help system activates after 5 minutes to assist players

## Compatibility Requirements  
- **NFR006**: Function on smartphones 6+ years old (Android 7+, iOS 12+)
- **NFR007**: Compatible with major desktop browsers (Chrome, Firefox, Safari, Edge)
- **NFR008**: Consistent viewport scaling across different screen sizes (4" to 27")
- **NFR009**: No app installation required - web browser only

## Reliability Requirements
- **NFR010**: 99% uptime during 3-hour open house demonstration periods  
- **NFR011**: Graceful handling of player disconnections without system crash
- **NFR012**: Automatic game recovery after temporary network interruptions
- **NFR013**: No data loss during normal disconnect scenarios

## Usability Requirements
- **NFR014**: New players can start playing within 30 seconds of joining
- **NFR015**: Game rules understandable without text instructions (visual/intuitive design)
- **NFR016**: Spectator view engaging for non-playing audience members
- **NFR017**: High score entry system similar to pinball machines (initials for top 10)
- **NFR018**: Clear visual feedback for all ability usage and status effects
- **NFR019**: Teacher can easily switch between active game sessions

## Accessibility and Design Requirements
- **NFR020**: Different avatar shapes and patterns, not just colors, for player distinction
- **NFR021**: High contrast visual design for noisy environment visibility
- **NFR022**: Primarily visual instructions rather than text-based guidance
- **NFR023**: Clear distinction between player and opponent through multiple visual cues

## Audio Requirements
- **NFR024**: Background music not required due to noisy demonstration environment
- **NFR025**: Sound effects secondary priority - visual feedback is primary
- **NFR026**: Optional sound effects for actions (shooting, abilities) but must not be essential

## Technical Architecture Requirements
- **NFR027**: Client-server architecture with centralized game state management  
- **NFR028**: WebSocket communication for real-time updates
- **NFR029**: Single server deployment on standard laptop hardware
- **NFR030**: Minimal external dependencies (avoid Unity, complex game engines)
- **NFR031**: No authentication or user registration required - anonymous gameplay only
- **NFR032**: React frontend with C# backend implementation