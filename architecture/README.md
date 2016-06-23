# Architecture

Everything we build conforms the principles of [service-oriented-architectures](../global-requirements/soa.md).

![architecture diagram][arch-diagram]

## Key Repositories and Services

### idm (Identity Management)

- **Domains:** user data
- **Accountabilities:** SSO, authentication, authorization, user data APIs
- **Endpoint:** https://idm.learnersguild.org
- **Repository:** https://github.com/LearnersGuild/idm

#### idm-jwt-auth (Node.js IDM Helpers)

- **Accountabilities:** SSO for Node.js apps
- **Repository:** https://github.com/LearnersGuild/idm-jwt-auth

### game (Game)

- **Domains:** projects, teams, goals, game statistics
- **Accountabilities:** team assignment, goal assignment, player statistics
- **Endpoint:** https://game.learnersguild.org
- **Repository:** https://github.com/LearnersGuild/game

### echo-chat (Chat, Main UI)

- **Domains:** real-time chat among players
- **Accountabilities:** real-time chat, "launchpad" for other Learners Guild services
- **Endpoint:** https://echo.learnersguild.org
- **Repository:** https://github.com/LearnersGuild/echo-chat
- **Fork of:** [Rocket.Chat][rocket.chat]

#### rocketchat-lg-* (Chat Customizations)

- **Domains:** Rocket.Chat custom packages for LG functionality
- **Accountabilities:** chat single-sign-on, additional `/slash` commands, API extensions
- **Repositories:** https://github.com/LearnersGuild/rocketchat-lg-sso, https://github.com/LearnersGuild/rocketchat-lg-slash-commands, https://github.com/LearnersGuild/rocketchat-lg-api-extensions

### game-cli (Game CLI Commands)

- **Domains:** commands and command-line options
- **Accountabilities:** command-line option parsing, API invocations, and error handling
- **Repository:** https://github.com/LearnersGuild/game-cli


[arch-diagram]: https://www.lucidchart.com/publicSegments/view/701b182a-c988-4eea-8231-ecae99571426/image.png
[rocket.chat]: https://rocket.chat/
