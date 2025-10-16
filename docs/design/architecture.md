# 3.1 System Architecture

## Overall Architecture
The MazeRunner system follows a client-server architecture with centralized game state management. All game logic executes on a single server to ensure synchronization and prevent the desync issues experienced in previous projects.

**Architecture Pattern**: Client-Server with WebSocket communication
**Deployment Model**: Single server application running on laptop with web-based clients

## Technology Stack
- **Frontend**: React with TypeScript for responsive UI
- **Backend**: C# with ASP.NET Core for game server
- **Communication**: SignalR (WebSocket) for real-time updates, REST API for initial connection
- **Database**: SQLite for high scores and session data
- **Hosting**: Local server on laptop or lightweight cloud deployment

*[PLACEHOLDER: System Architecture Diagram showing client-server interaction, WebSocket connections, and component relationships]*

## Deployment Architecture
- **Development**: Local development environment with React dev server and C# backend
- **Production**: Single executable running both React build and C# server on demonstration laptop
- **Scalability**: Single server instance designed for maximum 10 concurrent players