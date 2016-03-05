# Architecture

Everything we build conforms the principles of [service-oriented-architectures](../global-requirements/soa.md).

![architecture diagram][arch-diagram]

## Services

### Chat

- **Domains:** real-time chat logs
- **Accountabilities:** real-time chat, "launchpad" for other Learners Guild services
- **Endpoint:** https://chat.learnersguild.org
- **Repository:** https://github.com/LearnersGuild/Rocket.Chat
- **Powered by:** [Rocket.Chat][rocket.chat]

#### Chat Customizations

- **Domains:** Rocket.Chat customizations
- **Accountabilities:** "launchpad" for other Learners Guild services
- **Repository:** (COMING SOON)

### Challenges (maybe?)

- **Domains:** challenges, challenge ratings, challenge discussion
- **Accountabilities:** ratings and comments about challenges
- **Repository:** (COMING MAYBE?)

### Player Stats

- **Domains:** teams, goals, player feedback, player statistics
- **Accountabilities:** "retrospective" and feedback interactions, stats APIs
- **Repository:** (COMING SOON)

### Event Log

- **Domains:** log data for player actions
- **Accountabilities:** player action data logging and reporting
- **Powered by:** [Keen.io][keen.io]

### Identity Management

- **Domains:** user data
- **Accountabilities:** SSO, authentication, authorization, user data APIs
- **Endpoint:** https://idm.learnersguild.org
- **Repository:** https://github.com/LearnersGuild/idm

## Other Software

### Chrome Extension (maybe?)

- **Accountabilities:** interactions with LG APIs via GitHub
- **Repository:** (COMING MAYBE?)


[arch-diagram]: https://www.lucidchart.com/publicSegments/view/701b182a-c988-4eea-8231-ecae99571426/image.png
[auth0]: https://auth0.com/
[rocket.chat]: https://rocket.chat/
[keen.io]: https://keen.io/
