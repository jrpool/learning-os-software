# User Experiences

This document lists and describes the actions available to users.

There are two types of users: Learners and Moderators. When working on a project, Learners take on the role of either a Team Lead or Team Member.

## All Actions

| Command    | Description                                    |
|:-----------|:-----------------------------------------------|
| `/status`  | Get status of learner, project, or cycle       |
| `/search`  | Search for goals, projects, learners, and more |
| `/list`    | List goals, projects, help requests, and more  |
| `/create`  | Create a new goal                              |
| `/play`    | Activate a learner                             |
| `/pause`   | Deactivate a learner for current cycle         |
| `/vote`    | Vote on goals                                  |
| `/request` | Submit a help or feedback request              |
| `/offer`   | Offer help or feedback                         |
| `/profile` | Edit your user profile                         |

## Moderator-Only Actions

| Command   | Description                                    |
|:----------|:-----------------------------------------------|
| `/start`  | Start a cycle                                  |
| `/make`   | Run scripts to aid in game moderation          |
| `/invite` | Invite learner to project (built-in command)   |
| `/kick`   | Remove learner from project (built-in command) |

## General UX

Stories:

- Check status of learners
- Check status of projects
- Check status of cycles
- View a goal
- View a project
- Search goals
- Search projects

## Learner UX

Stories:

- Create goals
- Vote on goals
- Request help
- Request feedback
- View help requests
- View feedback requests
- Offer help
- Offer feedback

## Moderator UX

**Stories (happy path)**:

- Check status of voting
  - `/status next`
- Start cycle (form projects)
  - `/start`
- View formed projects
  - `/list projects`
- Check status of retrospective
  - `/status`

**Stories (manual override)**:

- Play/pause learners
  - `/play @learner`
  - `/pause @learner`
- Start/stop voting
  - `/start votes`
  - `/stop votes`
- Assign learners to projects
  - `/invite @learner` (from project channel)
- Remove learners from projects
  - `/kick @learner` (from project channel)
- Make a learner a team lead
  - `/make lead @learner #project-channel`
- Make a learner a team member
  - `/make member @learner #project-channel`
- Start/stop retrospective
  - `/start retro`
  - `/stop retro`

### Flow: Lifecycle of a Cycle

The core accountability of Moderators is to oversee cycles. They are responsible for ensuring that voting happens, that projects are formed appropriately, and that a retrospective occurs at the end of a cycle.

1. `/status next` : check status of votes for next (upcoming) cycle
  - If the next cycle is ready to start (all active chapter learners have voted and all retrospectives for current cycle have been submitted)...
    - "Ready" message is displayed
    - Moderator is prompted to run `/start` to start the next cycle
  - Else...
    - "Waiting" message is displayed
    - Description indicates why next cycle is not ready to be started (e.g. vote quorum not met, outstanding retrospectives)
1. `/start` : start the next cycle by forming teams
  - If the next cycle cannot be started...
    - Error message with explanation displayed (see above for "Waiting" condition)
  - Game transitions from current cycle to next
    - Current cycle is set to inactive
    - All projects in current cycle are set to inactive
    - Projects are formed from votes
    - Next cycle is set to active
    - Projects are set to active
  - "Cycle started" message is displayed
    - Public announcement to all learners
    - Includes information about projects and teams
1. `/list projects` : show the list of currently active projects
  - Displays information about the projects for the current cycle
1. `/status` : check status of current cycle
  - Running `/status` with no arguments displays information about the currently active cycle
  - Overview of project statuses and % completion of retrospectives is displayed

## Team Member UX

## Team Lead UX
