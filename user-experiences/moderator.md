# Moderator UX

## Stories

**Happy path:**

- Check status of current cycle
  - `/cycle status`
- Form projects from voting
  - `/cycle launch`
- View formed projects
  - `/project list`
- Start reflection stage
  - `/cycle reflect`

**Manual override:**

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

## Flows

### Lifecycle of a Cycle

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
  - Overview of project statuses is displayed
1. `/cycle reflect` : move the cycle into `REFLECTION` state
  - Notification sent to all project channels active in this cycle
  - All Learners are instructed to begin their retrospectives
    - See the "Complete Retrospective Reflections" flow in [learner.md](learner.md).
1. `/cycle status` : check status of current cycle
  - Overview of % completion of retrospectives is displayed
