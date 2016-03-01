# Architecture

Everything we build conforms the principles of [service-oriented-architectures](../global-requirements/soa.md).

![architecture diagram][arch-diagram]

## Services

### SSO

- **Powered by:** [Auth0][auth0]

### Chat

- **Endpoint:** https://chat.learnersguild.org
- **Repository:** https://github.com/LearnersGuild/Rocket.Chat
- **Powered by:** [Rocket.Chat][rocket.chat]

#### Chat Customizations

- **Repository:** (COMING SOON)

### Event Log

- **Powered by:** [Keen.io][keen.io]

### Player Stats

- **Repository:** (COMING SOON)

### Identity Management

- **Endpoint:** https://idm.learnersguild.org
- **Repository:** https://github.com/LearnersGuild/idm


[arch-diagram]: https://www.lucidchart.com/publicSegments/view/701b182a-c988-4eea-8231-ecae99571426/image.png
[auth0]: https://auth0.com/
[rocket.chat]: https://rocket.chat/
[keen.io]: https://keen.io/
