## Additional Questions Based on Expert Interview

5. Technical Implementation and Platform

- What technology stack is preferred for implementation?
**Answer**: Web-based solution preferred for easy setup. Frontend: React, Vue, or Angular. Backend: C# Blazor, Python Flask/Django, or similar. WebSockets for communication. Avoid Unity as it's complex to set up and maintain.

- How should the game handle player disconnections?
**Answer**: If player loses connection, game ends for both players with "Connection lost, game ended" message. Both return to start screen. No winner declared.

- What happens if someone griefs by intentionally disconnecting when losing?
**Answer**: Not a problem - players are friends from high school just having fun. It's not a serious competitive environment.

6. Game Setup and Logistics

- How is matchmaking handled?
**Answer**: Automatic matchmaking - first player ready waits for second player to connect, then game starts automatically. No choosing opponents to reduce complexity.

- Can teacher/demonstrator spectate specific games?
**Answer**: Yes, teacher gets list of ongoing sessions and can select which one to display on projector. Can switch between different active games.

- What is the target setup time from laptop to running demo?
**Answer**: Maximum 2 minutes. Game should run as web service on laptop or as Docker container on web server.

7. Game Content and Themes

- Are there specific visual themes or characters preferred?
**Answer**: Fantasy theme suggested (wizards/warriors on isometric dungeon map). Avatar must match background thematically. Relatively open as long as it's consistent.

- Should there be multiple maps?
**Answer**: One map is sufficient for MVP. Can randomize key, items, and exit positions while keeping walls the same.

- Can players see the key location initially?
**Answer**: No, key location is hidden. Exit is visible but players must find where it is on the map. After 5 minutes, might give compass direction to key as help.

8. Scoring and Competition

- How detailed should the scoring system be?
**Answer**: Time-based scoring for quick completion, plus optional point collection (apples/coins) for higher scores. Possibly letter collection for secret word bonus prizes.

- Should unfairness be avoided (e.g., spawning next to key)?
**Answer**: Perfect fairness not critical since players only play once. Could make map symmetric for fairness, but not essential.

- Is there replay value needed?
**Answer**: No replay value required. Designed for one-time play experience that's engaging enough to be interesting but doesn't need depth for repeated play.

9. Context and Purpose

- Why was MazeRunner chosen over the previous haptic technology demo?
**Answer**: Previous system was cool but required complex hardware setup, driver installations, and was unreliable (broke with OS updates). Wanted something that "always works" - just open laptop and run in 2 minutes.

- What's the main goal for the open house demonstration?
**Answer**: Engage two players, create spectator entertainment, serve as icebreaker for conversations about computer science education. Replace "Are you interested in computer science?" with "Want to play a game?"

- How long should gameplay sessions be?
**Answer**: 5 minutes target, but flexible. 90% should finish within 5 minutes, remaining 10% can play 7-8 minutes. Goal is quick engagement, not extended gameplay.

- Will this project be used for multiple years?
**Answer**: Yes, Josef has been creating new game projects every year for 4 years. Previous games had issues (sync problems, Unity export complexity). Looking for reliable, maintainable solution.