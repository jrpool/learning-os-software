# User Experiences

This document lists and describes the actions available to users.

There are two types of users, and thus two different user experiences: [Learner UX](learner.md) and [Moderator UX](moderator.md). When working on a project, Learners take on the role of either a Team Lead or Team Member.

There are some shared stories between the two (e.g. checking the status of a learner or project), so for the sake of simplicity assume that the Moderator UX is a superset of the Learner UX.

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

| Action            | Description                                                  |
|:------------------|:-------------------------------------------------------------|
| `play <@handle>`  | Activate learner with handle `<@handle>`                     |
| `pause <@handle>` | Deactivate learner with handle `<@handle>` for current cycle |

### Command: `/goal`

| Action           | Description              |
|:-----------------|:-------------------------|
| `create`         | Create a new goal        |
| `show <id>`      | View goal with id `<id>` |
| `search <query>` | Search for goals         |

### Command: `/project`

| Action           | Description                          |
|:-----------------|:-------------------------------------|
| `status <id>`    | Get status of project with id `<id>` |
| `show <id>`      | Alias for `status`                   |
| `search <query>` | Search for projects                  |
| `list`           | List projects                        |

## Misc. Actions

Miscellaneous actions are infrequently used, and generally not part of core gameplay.

| Command    | Description            |
|:-----------|:-----------------------|
| `/profile` | Edit your user profile |
