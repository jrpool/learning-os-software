# Learner UX

## Stories

**Basics for v0**

- Create goals
  - `/goal create`
- Vote on goals
  - `/vote <id> <id>`
- Check status of projects
  - `/project status #project-id`
- Check status of cycles
  - `/cycle status`
  - `/cycle status <cycle-id>`
  - `/cycle status --project #project-id`
- View a goal
  - `/goal show <id>`
- Search goals
  - `/goal search <query>`
- Search projects
  - `/project search <query>`
- Show retrospective status and list of questions
  - `/log --retro`
  - `/log -r`
- Log retrospective reflection
  - `/log -r -q1 beth:30 amy:20 jose:25 tim:@15`
  - `/log -r -q4 Amy's wrote very clean code. She can improve by submitting more PRs more frequently so that the rest of her team can stay up-to-date with her progress.`

**Possible future stories**

- Request help
  - `/request -h`
- Request feedback
  - `/request -f`
- View help requests
  - Go to `#help` channel, review posts
- View feedback requests
  - Go to `#feedback` channel, review posts
- Offer help
  - `/offer -h`
  - `/offer -h @handle`
  - `/offer -h #project-id`
- Offer feedback
  - `/offer -f`
  - `/offer -f @handle`
  - `/offer -f #project-id`
- Check status of learners
  - `/learner status`
  - `/learner status @handle`

## Flows

### Complete Retrospective Reflections

At the end of a cycle, all Learners will log their reflections as a part of the retrospective process. Retrospectives occur at the end of a cycle. The Moderator will notify Learners to begin their retrospectives.

The retrospective is a set of questions to which Learners must respond. Learners use the `/log` command to view questions and submit answers/reflections. They can respond by logging their reflections in any channel, as the `/log` command is private to the learner.

Most Learners will likely want to use a private group or a DM channel (perhaps with the `@echo`) for issuing `/log` commands, so that they can keep this history separate from other channel histories.

Learners can log their reflections in any order, but they questions are numbered in a sequential order to influence reflection order.

Learners must submit reflections for every question in the retrospective in order for their retrospective to be considered "complete".

1. When Moderator runs `/cycle reflect`, Learners will receive a notification to begin the retrospective in their current project channel.
  - Message from `@echo`: "Time to begin the retrospective! Run `/log -r` to start."
1. `/log -r` : show retrospective status and questions
  - `@echo` responds with welcome message and instructions.
1. Repeat...
  - `/log -r -q<n>` : Show question number `<n>`
    - `@echo` responds with question and instructions for logging reflection.
  - `/log -r -q<n> [arguments]` : Log reflection for question number `<n>`
    - Syntax for `[arguments]` varies based on question
  - If reflection is valid and complete...
    - `@echo` responds with a confirmation and "thank you" message.
  - Else...
    - `@echo` responds with a helpful error message.
1. `/log -r` : check retrospective status
  - If all questions are complete...
    - `@echo` notifies Learner of completion.
    - Includes instructions for how to edit any submissions.
  - Else...
    - `@echo` informs Learner of progress on Retrospective.
1. When Learner has completed their retrospectives...
  - Notification is sent to project channel (see Project Retrospective Status & Notifications below)

#### Example

```
@learner  > /log -r
@echo     > You have logged 0/12 of your reflections for this retrospective.
            Run `/log -r` at any time to check your progress.

            To log a reflection, pick a question using the command:
            `/log -r -q<integer from 1-12>`

            For example:
            `/log -r -q3` => show question 3 (of 12)

            Then follow the instructions specified in the question to answer.
@learner  > /log -r -q1
@echo     > *r1*: Rate the relative contributions of your teammates (including yourself).

            Use the command:
            `/log -r -q1 <teammate>:<%contribution> [<teammate>:<%contribution>...]`

            For example:
            `/log -r -q1 beth:30 amy:20 jose:25 tim:15`
@learner  > /log -r -q1 bob:20 notaplayer:80
@echo     > Whoops! Looks like you have a typo.
            `@notaplayer` wasn't on your team.

            Your team was: ali ben cara dwight learner
@learner  > /log -r -q1 ali:15 ben:15 cara:40 dwight:10 learner:20
@echo     > Thanks! Reflection logged. You're 8.3% of the way through the retrospective.
@learner  > /log -r -q2
@echo     > *r2*: Rate your agreement with the following statement:

            > The project was relevant to my learning.

            Options:
            - 1 (strongly disagree)
            - 4 (neutral)
            - 7 (strongly agree)
            - 0 (not enough information)

            Use the command:
            `/log -r -q2 <integer from 0-7>`

            For example:
            `/log -r -q2 4`
@learner  > /log -r -q2 5
@echo     > Thanks! Reflection logged. You're 16.7% of the way through the retrospective.
@learner  > /log -r
@echo     > You have logged 2/12 of your reflections for this retrospective.
            Run `/log -r` at any time to check your progress.

            To log a reflection, pick a question using the command:
            `/log -r<integer from 1-12>`

            For example:
            `/log -r -q3` => show question 3 (of 12)

            Then follow the instructions specified in the question to answer.

[ 10 more questions + reflections... ]

@learner  > /log -r
@echo     > Nice work! You've completed 100% of the reflections.

            To edit any of your reflections, just log it again before the end of the cycle.
@learner  > /log -r -q2 3
@echo     > Reflection for retrospective question 2 updated!
```

### Project Reviews



### Project Retrospective Status & Notifications

There are two ways that teams can find out the status of their retrospective: pull and push.

1. Pull: any Learner can run the `/cycle status --project` command to get information about the state of the current cycle for their project.
1. Push: after a Learner completes their reflections for a retrospective, `@echo` notifies the project channel.

#### Status Example

```
@learner  > /cycle status --project
@echo     > The cycle for project #bee-23 is currently in *reflection* state.
            2 / 5 retrospectives have been completed for this project.
```

#### Notification Example

After a Learner completes their reflections, this message is posted to the **project channel**:

```
@echo     > One of your teammates has just submitted their reflections for this retrospective!
            2 / 5 retrospectives have been completed for this project.
```
