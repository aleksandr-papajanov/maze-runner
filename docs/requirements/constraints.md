# 2.5 System Constraints and Assumptions

## Technical Constraints
- **Single server limitation**: All game logic runs on one laptop, no distributed architecture
- **Web technology only**: React frontend with C# backend, no native mobile apps or game engines
- **Network dependency**: Requires stable wifi connection for real-time gameplay
- **Browser compatibility**: Must work without modern JavaScript features on older devices (6+ years old)
- **Avoid Unity**: Explicitly avoid Unity due to complexity and maintenance issues from previous projects
- **WebSocket requirement**: Real-time communication requires WebSocket support

## Business Constraints  
- **Demonstration context**: Optimized for short-term engagement, not long-term retention
- **Zero installation**: Cannot require app downloads or account creation
- **No authentication required**: Anonymous gameplay only - no user accounts, logins, or registration
- **Noise environment**: Visual feedback prioritized over audio (100+ people environment)
- **Setup simplicity**: Must be operable by non-technical university staff
- **QR code access**: Players must be able to join via QR code scan within 1 minute maximum
- **Physical space**: Only ~10 people can fit around demonstration booth
- **Setup time**: Maximum 2 minutes from laptop startup to playable demo

## Fairness and Social Context
- **Perfect fairness not critical**: Players typically play only once, so minor imbalances acceptable
- **Social cheating acceptable**: Players can "cheat" by looking at spectator screen - creates fun interaction
- **No griefing concerns**: Players are high school friends in friendly environment, not competitive strangers
- **Symmetrical map optional**: Could implement for fairness but not essential requirement
- **One-time play**: No replay value needed - designed for single play experience

## Key Assumptions
- **Target audience familiarity**: Users understand basic maze game concepts
- **Device availability**: Players have smartphones or can use provided devices  
- **Network infrastructure**: University provides adequate wifi for concurrent connections
- **Social context**: Competitive gameplay with audience creates natural engagement
- **Friendly environment**: Players are not competitive strangers, reduces need for anti-cheat measures
- **Visual focus**: Noisy environment (100+ people) means visual feedback must be primary communication method