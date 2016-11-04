# Your First Day

Congratulations for making it through the Learners Guild [hiring process][hiring-process]! Most people don't.

If you're reading this, you're most likely on the [#los][los-slack] team energizing the [Software Engineering][software-engineering-glassfrog] role, or are otherwise contributing to our software in some way. This part of the guide is meant to get you oriented, and with any luck, up-and-running on all of our software services on your local development machine.

## Getting Started

As a Learners Guild partner, you should have already received a checklist of on-boarding items to complete in Asana. The steps outlined below is not meant to supersede that list -- all of that stuff still needs to be done. However, it might take a day or two, and in the interim, or once you've made it through that list, you're (no doubt) going to want to get our systems running on your local development machine. Here's a high-level guide with some pointers to help you get started.

Please keep in mind that, from time to time, this guide may become outdated. If you notice that it _has_ become outdated, please check out this repository, fix it, and submit a pull request. You'll be saving every person after you time if you do this. **Be a hero.**

### 1. Read This Guide in Its Entirety

Okay, that may not be very satisfying, as it doesn't get you any closer to having things running, but it's pretty crucial. We're a distributed team, which means that we rely heavily on written documentation to stay synchronized. Having this software guide helps everyone understand where we're coming from philosophically, while at the same time orienting people to decisions we've made around [best practices][best-practices-software-guide], [architecture][architecture-software-guide], and [design][design-guide-software-guide].

So read through it once. You don't have to memorize it, but you should definitely have familiarized yourself with everything herein. Trust us -- it will save you time in the long run.

### 2. Slack

Make sure you've joined (at a minimum) the [#los][los-slack] and [#tech-errors][tech-errors-slack] channels in Slack. Every engineer is expected to pay attention to the activity in these channels.

### 3. Set Up Your Environment

Rather than trying to keep this guide up-to-date with all of the changes across all of our various repositories and services, what we recommend is to follow the `README.md` instructions for each of the key services **in this order**. Before you do that though, you've already read this guide in its entirety, right? Especially the [architecture][architecture-software-guide] section, right? **RIGHT?!?!** Good.

So here's the order of operations. If you follow these steps, you _should_ be up and running relatively quickly.

1. [idm][idm-repo]: Identity Management Service
2. [game][game-repo]: Game Service
3. [echo-chat][echo-chat-repo]: Chat Service

#### Seed Your Database(s)

Over time, the process by which you do this will change and evolve. But (obviously) before you can do anything with any of our services, you're going to need a user account, since all of our services use a single-sign-on system. How do you do this next step, then?

Find a buddy. Seriously. Head on over to [#los][los-slack], let folks know you've got the services up and running and you need help getting some seed / test data going. That may be an unsatisfying answer, but it's the best we've got right now.

### 4. Get a Demo of the system

Now that things are up-and-running, you should head over to [#los][los-slack] again and ask someone to give you a demo of the software as it works today. Our learning philosophy is really radical; it's based on both [cognitive apprenticeship][cognitive-apprenticeship-wikipedia] and [game-enhanced learning][game-enhanced-learning-wikipedia]. The fastest way to get yourself oriented to the game we've designed is to have someone demonstrate the game play.


<!-- references -->

[hiring-process]: http://guide.learnersguild.org/Operating-Model/Hiring-Process/
[los-slack]: https://learnersguild.slack.com/archives/los
[tech-errors-slack]: https://learnersguild.slack.com/archives/tech-errors
[software-engineering-glassfrog]: https://app.glassfrog.com/roles/4477030
[cognitive-apprenticeship-wikipedia]: https://en.wikipedia.org/wiki/Cognitive_apprenticeship
[game-enhanced-learning-wikipedia]: https://en.wikipedia.org/wiki/Educational_game

[best-practices-software-guide]: ../best-practices/README.md
[architecture-software-guide]: ../architecture/README.md
[design-guide-software-guide]: ../design-guide/README.md

[idm-repo]: https://github.com/LearnersGuild/idm
[game-repo]: https://github.com/LearnersGuild/game
[echo-chat-repo]: https://github.com/LearnersGuild/echo-chat
