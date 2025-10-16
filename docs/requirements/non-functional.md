# 2.3 Non-Functional Requirements

## Performance Requirements
- **NFR001**: Game setup time <2 minutes from laptop startup to playable state
- **NFR002**: Player movement response time <100ms under normal network conditions
- **NFR003**: Support 5 concurrent sessions without performance degradation
- **NFR004**: 90% of games complete within 5 minutes

## Compatibility Requirements  
- **NFR005**: Function on smartphones 6+ years old (Android 7+, iOS 12+)
- **NFR006**: Compatible with major desktop browsers (Chrome, Firefox, Safari, Edge)
- **NFR007**: Consistent viewport scaling across different screen sizes (4" to 27")
- **NFR008**: No app installation required - web browser only

## Reliability Requirements
- **NFR009**: 99% uptime during 3-hour open house demonstration periods  
- **NFR010**: Graceful handling of player disconnections without system crash
- **NFR011**: Automatic game recovery after temporary network interruptions
- **NFR012**: No data loss during normal disconnect scenarios

## Usability Requirements
- **NFR013**: New players can start playing within 30 seconds of joining
- **NFR014**: Game rules understandable without text instructions (visual/intuitive design)
- **NFR015**: Spectator view engaging for non-playing audience members

## Technical Architecture Requirements
- **NFR016**: Client-server architecture with centralized game state management  
- **NFR017**: WebSocket communication for real-time updates
- **NFR018**: Single server deployment on standard laptop hardware
- **NFR019**: React frontend with C# backend implementation