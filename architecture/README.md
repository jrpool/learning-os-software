# Architecture

Everything we build conforms the principles of [service-oriented-architectures](../global-requirements/soa.md).

![architecture diagram][arch-diagram]

## Services

### Identity Management

- **Domains:** user data
- **Accountabilities:** SSO, authentication, authorization, user data APIs
- **Endpoint:** https://idm.learnersguild.org
- **Repository:** https://github.com/LearnersGuild/idm

### Chat

- **Domains:** real-time chat among players
- **Accountabilities:** real-time chat, "launchpad" for other Learners Guild services
- **Endpoint:** https://chat.learnersguild.org
- **Repository:** https://github.com/LearnersGuild/Rocket.Chat
- **Powered by:** [Rocket.Chat][rocket.chat]

#### Chat Customizations

- **Domains:** Rocket.Chat custom packages for LG functionality
- **Accountabilities:** chat single-sign-on, additional /slash commands
- **Repositories:** https://github.com/LearnersGuild/rocketchat-lg-sso, https://github.com/LearnersGuild/rocketchat-lg-slash-commands

### Game

- **Domains:** teams, goals, game statistics
- **Accountabilities:** team assignment, goal assignment, player statistics
- **Repository:** https://github.com/LearnersGuild/game

### Event Log

- **Domains:** log data for player actions
- **Accountabilities:** player action data logging and reporting
- **Powered by:** [Keen.io][keen.io]

## Other Software

### Chrome Extension (maybe?)

- **Accountabilities:** interactions with LG APIs via GitHub
- **Repository:** (COMING MAYBE?)


[arch-diagram]: https://www.lucidchart.com/publicSegments/view/701b182a-c988-4eea-8231-ecae99571426/image.png
[rocket.chat]: https://rocket.chat/
[keen.io]: https://keen.io/
