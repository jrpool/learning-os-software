# Learner UX

## Stories

- Create goals
  - `/goal create`
- Vote on goals
  - `/vote <id> <id>`
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
- Check status of projects
  - `/project status #project-id`
- Check status of cycles
  - `/cycle status`
  - `/cycle status <cycle-id>`
- View a goal
  - `/goal show <id>`
- Search goals
  - `/goal search <query>`
- Search projects
  - `/project search <query>`
- Begin retrospective
  - `/log --retro`
- Log retrospective reflection
  - `/log --r1 beth:30 amy:20 jose:25 tim:@15`
  - `/log --r4 Amy's wrote very clean code. She can improve by submitting more PRs more frequently so that the rest of her team can stay up-to-date with her progress.`
- Check retrospective progress
  - `/cycle status` (for chapter)
  - `/cycle status --project` (for current project)

## Flows

### Complete Retrospective Reflections

At the end of a cycle, all Learners will log their reflections as a part of the retrospective process. Retrospectives occur at the end of a cycle. The Moderator will notify Learners to begin their retrospectives.

The retrospective process is essentially a set of questions and answers/reflections. The Q&A takes place in a `#log` private channel, so all responses are private. The same command (`/log`) is used for all answers.

Questions are given in sequence until all reflections for a cycle have been submitted.

1. When Moderator runs `/cycle retro`, Learners will receive a notification to begin the retrospective in their current project channel.
  - Message from `@lg-bot`: "Time to begin the retrospective! Run `/log --retro` in your `#log` channel to start.
1. `/log --retro` (in `#log` channel) : begin retrospective process
  - `@lg-bot` responds with welcome message and instructions.
  - `@lg-bot` shows first reflection question (`r1`) along with instructions for how to answer.
1. Repeat until all reflections are complete...
  - `/log --r<question number> [arguments]` : Learner logs reflection for current question
    - Syntax varies based on question
  - If reflection is valid and complete...
    - `@lg-bot` responds with a confirmation and "thank you" message.
    - `@lg-bot` shows next reflection question along with instructions for how to answer.
  - Else...
    - `@lg-bot` responds with a helpful error message.
1. `@lg-bot` notifies Learner of completion.
  - Includes instructions for how to edit any submissions.

#### Example

```
@learner  > /log --retro
@lg-bot   > You have logged 0/12 of your reflections for this retrospective.
            Run `/log --retro` at any time to check your progress.

            To log a reflection, pick a question using the command:
            `/log --r<integer from 1-12>`

            For example:
            `/log --r3` => show question 3 (of 12)

            Then follow the instructions specified in the question to answer.
@learner  > /log --r1
@lg-bot   > *r1*: Rate the relative contributions of your teammates (including yourself).

            Use the command:
            `/log --r1 <teammate>:<%contribution> [<teammate>:<%contribution>...]`

            For example:
            `/log --r1 beth:30 amy:20 jose:25 tim:@15`
@learner  > /log --r1 bob:20 notaplayer:80
@lg-bot   > Whoops! Looks like you have a typo.
            `@notaplayer` wasn't on your team.

            Your team was: ali ben cara dwight learner
@learner  > /log --r1 ali:15 ben:15 cara:40 dwight:10 learner:20
@lg-bot   > Thanks! Reflection logged. You're 8.3% of the way through the retrospective.
@learner  > /log --r2
@lg-bot   > *r2*: Rate your agreement with the following statement:

            > The project was relevant to my learning.

            Options:
            - 1 (strongly disagree)
            - 4 (neutral)
            - 7 (strongly agree)
            - 0 (not enough information)

            Use the command:
            `/log --r2 <integer from 0-7>`

            For example:
            `/log --r2 4`
@learner  > /log --r2 5
@lg-bot   > Thanks! Reflection logged. You're 16.7% of the way through the retrospective.
@learner  > /log --retro
@lg-bot   > You have logged 2/12 of your reflections for this retrospective.
            Run `/log --retro` at any time to check your progress.

            To log a reflection, pick a question using the command:
            `/log --r<integer from 1-12>`

            For example:
            `/log --r3` => show question 3 (of 12)

            Then follow the instructions specified in the question to answer.

[ 10 more questions + reflections... ]

@lg-bot   > Nice work. You've completed 100% of the reflections.
            To edit any of your reflections, just log it again before the end of the cycle.
@learner  > /log --r2 3
@lg-bot   > Reflection for retrospective question 2 updated!
```

### Project Retrospective Status & Notifications

There are two ways that teams can find out the status of their retrospective: pull and push.

1. Pull: any Learner can run the `/cycle status --project` command to get information about the state of the current cycle for their project.
1. Push: after a Learner completes their reflections for a retrospective, `@lg-bot` notifies the project channel.

#### Status Example

```
@learner  > /cycle status --project
@lg-bot   > The cycle for project #bee-23 is currently in *reflection* state.
            2 / 5 retrospectives have been completed for this project.
```

#### Notification Example

After a Learner completes their reflections, this message is posted to the **project channel**:

```
@lg-bot   > One of your teammates has just submitted their reflections for this retrospective!
            2 / 5 retrospectives have been completed for this project.
```
