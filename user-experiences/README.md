# User Experiences

This document lists and describes the actions available to users.

There are two types of users: Learners and Moderators. When working on a project, Learners take on the role of either a Team Lead or Team Member.

## Common Actions

Common actions are used frequently and take the form of `> /action [options]`.

Common actions are mostly used by Learners.

| Command    | Description                                    |
|:-----------|:-----------------------------------------------|
| `/vote`    | Vote on goals                                  |
| `/request` | Submit a help or feedback request              |
| `/offer`   | Offer help or feedback                         |
| `/log`     | Log feedback, retrospectives, and other events |

## Compound Actions

Compound actions take the form of `> /object action [options]`. The object provides the context for the action.

Compound actions are mostly used by Moderators.

### Command: `/cycle`

| Action   | Description                                     |
|:---------|:------------------------------------------------|
| `status` | Get status of cycle                             |
| `launch` | Form projects from votes (to begin cycle)       |
| `play`   | Allow cycle actions (voting, retrospectives)    |
| `pause`  | Disallow cycle actions (voting, retrospectives) |

### Command: `/learner`

| Action  | Description                            |
|:--------|:---------------------------------------|
| `play`  | Activate a learner                     |
| `pause` | Deactivate a learner for current cycle |

### Command: `/goal`

| Action   | Description       |
|:---------|:------------------|
| `create` | Create a new goal |

### Command: `/project`

| Action           | Description                          |
|:-----------------|:-------------------------------------|
| `status <id>`    | Get status of project with id `<id>` |
| `search [query]` | Search for projects                  |
| `list`           | List projects                        |

## Misc. Actions

| Command    | Description            |
|:-----------|:-----------------------|
| `/profile` | Edit your user profile |

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
  - `/cycle status`
- Launch cycle (form projects)
  - `/cycle launch`
- View formed projects
  - `/project list`
- Check status of current cycle (show retrospective data)
  - `/cycle status`

**Stories (manual override)**:

- Play/pause learners
  - `/learner play @handle`
  - `/learner pause @handle`
- Start/stop voting
  - `/cycle play`
  - `/cycle pause`
- Assign learners to projects
  - `/project add #proj-id @handle --member`
  - `/project add #proj-id @handle --lead`
  - `/project add @handle --member` (from project channel)
- Remove learners from projects
  - `/project remove #proj-id @handle`
  - `/project remove @handle` (from project channel)
- Start/stop retrospective
  - `/cycle play`
  - `/cycle pause`

### Flow: Lifecycle of a Cycle

The core accountability of Moderators is to oversee cycles. They are responsible for ensuring that voting happens, that projects are formed appropriately, and that a retrospective occurs at the end of a cycle.

1. `/cycle status` : check status of votes for the current cycle
  - If the cycle is ready to be launched (all active chapter learners have voted)...
    - "Ready" message is displayed
    - Moderator is prompted to run `/cycle launch` to form projects
  - Else...
    - "Waiting" message is displayed
    - Description indicates why cycle is not ready to be launched (e.g. vote quorum not met)
1. `/cycle launch` : move the cycle into `PRACTICE` state by forming teams
  - If the cycle cannot be moved into `PRACTICE` state...
    - Error message with explanation displayed (see above for "Waiting" condition)
  - Practice stage begins
    - Projects are formed from votes
    - Cycle is set to `PRACTICE` state
  - "Practice started" message is displayed
    - Public announcement to all learners
    - Includes information about projects and teams
1. `/project list` : show the list of currently active projects
  - Displays information about the projects for the current cycle
1. `/cycle status` : check status of current cycle
  - Running `/cycle status` displays information about the currently active cycle
  - Overview of project statuses and % completion of retrospectives is displayed

## Team Member UX

## Team Lead UX
