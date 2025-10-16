# 3.3 Dynamic Design (Runtime Behavior)

## Key Behavioral Patterns

### Game Session Lifecycle
```
Waiting → Active → Paused → Finished → Cleanup
```

### Player Connection States  
```
Connecting → Ready → Playing → Disconnected
```

### Item Usage Flow
```
Available → Collected → Activated → Effect Applied → Cooldown → Available
```

*[PLACEHOLDER: Activity Diagram showing complete game session flow from player join to game completion]*

*[PLACEHOLDER: Sequence Diagram showing real-time player movement synchronization between clients and server]*

*[PLACEHOLDER: State Diagram showing game session states and transitions]*

## Critical Interactions

### Real-Time Movement Synchronization
1. Player input detected in React component
2. Movement request sent to C# server via SignalR
3. Server validates move against maze boundaries and game rules
4. Server updates player position in game state
5. Server broadcasts position update to all clients in session via SignalR
6. React components render updated positions smoothly

### Ability Usage Sequence  
1. Player activates ability via React UI button
2. Client sends ability request with target/direction to C# server
3. Server validates ability availability and cooldown status
4. Server processes ability effect (e.g., stun opponent, drop key)
5. Server updates affected players' states
6. Server broadcasts ability animation and effects via SignalR
7. React components display visual feedback and update UI accordingly