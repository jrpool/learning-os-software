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
  - `/log --r1 @beth:30 @amy:20 @jose:25 @tim:@15`
  - `/log --r4 Amy's wrote very clean code. She can improve by submitting more PRs more frequently so that the rest of her team can stay up-to-date with her progress.`

## Flows

### Retrospective

At the end of a cycle, all Learners will log their reflections as a part of the retrospective process. Retrospectives occur at the end of a cycle. The Moderator will notify Learners to begin their retrospectives.

The retrospective process is essentially a set of questions and answers/reflections. The Q&A takes place in a `#log` private channel, so all responses are private. The same command (`/log`) is used for all answers.

Questions are given in sequence until all reflections for a cycle have been submitted.

1. When cycle is 80% complete, Learners will receive a notification to begin the retrospective.
  - Message from Moderator: "Time to begin the retrospective! Run `/log --retro` in your `#log` channel to start.
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
@lg-bot   > Welcome to the retrospective!

            You have 12 reflections to make. You are 0% of the way through.
            Run `/log --retro` at any time to check your progress or edit your reflections.

            Here's your first reflection...
@lg-bot   > *r1*: Rate the relative contributions of your teammates (including yourself).
            Use the command `/log --r1 <teammate>:<%contribution> [<teammate>:<%contribution>...]`
            For example,
            `/log --r1 @beth:30 @amy:20 @jose:25 @tim:@15`
@learner  > /log --r1 @bob:20 @notaplayer:80
@lg-bot   > Whoops! Looks like you have a typo.
            `@notaplayer` wasn't on your team.

            Your team was: @ali @ben @cara @dwight @learner
@learner  > /log --r1 @ali:15 @ben:15 @cara:40 @dwight:10 @learner:20
@lg-bot   > Thanks! Here's your next reflection...
@lg-bot   > *r2*: Rate your agreement with the following statement:
            "The project was relevant to my learning."
            - 1 (strongly disagree)
            - 4 (neutral)
            - 7 (strongly agree)
            - 0 (not enough information)

            Use the command `/log --r2 <number from 0-7>`
            For example,
            `/log --r2 4`
@learner  > /log --r2 5
@lg-bot   > Thanks! Here's your next reflection...

[ 10 more questions + reflections... ]

@lg-bot   > Nice work. You've completed 100% of the reflections.
            To edit any of your reflections, just submit it again before the end of the cycle.
@learner  > /log --r2 3
@lg-bot   > Reflection updated!
```
