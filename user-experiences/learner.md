# Learner UX

## Stories

### Basics

- Create goals
  - `/goal create`
- Vote on goals
  - `/vote <id> <id>`
- Check own stats
  - `/stats`
- Check stats of player
  - `/stats @learner`
- Check stats of team
  - `/stats #project-id`
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
- Set artifact for project
  - `/project set-artifact #project-id <url>`
- Search projects
  - `/project search <query>`
- Show retrospective status and list of questions
  - `/log --retro`
  - `/log -r`
- Log retrospective reflection
  - `/log -r -q1 beth:30 amy:20 jose:25 tim:15`
  - `/log -r -q4 "Amy's wrote very clean code. She can improve by submitting more PRs more frequently so that the rest of her team can stay up-to-date with her progress."`
- Show projects for review
  - `/project list --in-review`
  - `/project list -r`
- Review projects
  - `/review #project-id --completeness 89 --quality 63`
  - `/review #project-id -c89 -q63`

### Additional / Undecided

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

### Checking Stats

Stats are the primary way that learners get quantitative feedback on their progress and success in the game.

Learners should be able to see:

1. Their own stats, both in summary and in detail
1. Other learners' stats
1. Team stats (aggregations thereof)

#### Example

```
@learner  > /stats
@echo     > Stats for @learner:
            XP        [132.5] +++++++++++++
            Support   [  89%] |========= |
@learner  > /stats --xp
@echo     > XP Stats for @learner:
            Total XP:                 [132.5]
            Projects Completed:       [    3]
            Avg. Proj. Completeness:  [  94%]
            Avg. Proj. Quality:       [  87%]
            Avg. Rel. Contrib.:       [  +4%]
@learner  > /stats @julia
@echo     > Stats for @julia:
            XP        [171.9] +++++++++++++++++
            Support   [  73%] |=======   |
@learner  > /stats #whimpering-wallabies
@echo     > Stats for #whimpering-wallabies:
            Total XP      [925.2]
            Avg. XP       [144.1] ++++++++++++++
            Avg. Support  [  76%] |=======   |
```

### Voting + Project Creation

Learners vote on goals (after moderator runs `/cycle init`), and then projects are formed when the moderator runs `/cycle launch`.

At this time, a new channel is created for each project, named with the syntax `#<project-id>`.

#### Example

```
# moderator starts cycle
@mod      > /cycle init
@echo     > Cycle created! Voting can now begin.

# learners vote on goals
@learner  > /vote 2
@echo     > Error: You must vote for exactly 2 goals. Try `--help` for usage.
@learner  > /vote 2 5
@echo     > Vote recorded! You voted for goals 2 and 5.
@learner  > /vote 7 5
@echo     > Vote recorded! You voted for goals 7 and 5.

# after voting is complete, moderator creates projects
@mod      > /cycle launch
@echo     > Voting is closed. Generating projects from goals...

# in project channel (#terrible-tiger) after projects have been created...
@echo     > Time to start work on your projects!

            The first step is to create an appropriate project artifact.
            Once you've created the artifact, connect it to your project with the `/project set-artifact` command.

            Run `/project set-artifact --help` for more guidance.
@learner  > /project set-artifact https://github.com/owner/repo
@echo     > Error: invalid command - wrong number of arguments (1 for 2).

            Use `/project set-artifact --help` to read the docs.

@learner  > /project set-artifact #terrible-tiger https://github.com/owner/repo
@echo     > Thanks! The artifact for project #terrible-tiger is now set to https://github.com/owner/repo.
```

### Complete Retrospective Reflections

At the end of a cycle, all Learners will log their reflections as a part of the retrospective process. Retrospectives occur at the end of a cycle. The Moderator will notify Learners to begin their retrospectives.

The retrospective is a set of questions to which Learners must respond. Learners use the `/log` command to view questions and submit answers/reflections. They can respond by logging their reflections in any channel, as the `/log` command is private to the learner.

Most Learners will likely want to use a private group or a DM channel (perhaps with the `@echo`) for issuing `/log` commands, so that they can keep this history separate from other channel histories.

Learners can log their reflections in any order, but they questions are numbered in a sequential order to influence reflection order.

Learners must submit reflections for every question in the retrospective in order for their retrospective to be considered "complete".

1. When Moderator runs `/cycle reflect`, Learners will receive a notification to begin the retrospective in their current project channel (and the chapter channel).
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

During the `REFLECTION` stage of a cycle, learners review projects using the `/review` command.

Learners review their own projects as well as any other projects worked on during the cycle.

Project reviews happen at the end of a cycle, after retrospectives. Retrospectives == process analysis; reviews == product analysis. This distinction is important b/c retrospectives are always intra-team, whereas project reviews can be both intra- and inter-team.

At the start of a project, the team decides on which specifications it wants to include (i.e. define the scope of features) and a rubric for assessing output quality (e.g. code readability, OOP paradigm consistency, etc.).

During project review, reviewers use the set of specs to evaluate completeness and the quality rubric to evaluate quality. Both scores are `1..100` inclusive.

1. When Moderator runs `/cycle reflect`, Learners will receive a notification to begin reviewing projects.
1. `/project list --in-review` : Show projects for review
  - `@echo` responds with list of projects
1. Repeat...
  - `/review #project-id` : Show review status for project `#project-id`
    - `@echo` responds with number of reviews, and link to project artifact
  - `/review #project-id --completeness 89 --quality 72` : Review project with completeness and quality score
  - If review is valid and complete...
    - `@echo` responds with a confirmation and "thank you" message.
  - Else...
    - `@echo` responds with a helpful error message.

### Example

First, moderator kicks off reflection stage (for retrospectives and reviews):

```
@moderator  > /cycle reflect
@echo       > Cycle is now in `REFLECTION` stage.
```

Then learners are notified that they can review projects:

```
@echo     > The cycle has moved from Practice to Reflection.
            Time to start your retrospectives and project reviews.

            Run `/log --retro` to see your retrospective questions.
            Run `/project list --in-review` for a list of projects.
@learner  > /project list
@echo     > There are 5 projects active this cycle.
            You have completed 3 projects thus far. Your current project is in review.

            Run `/project list -r` to list projects in review.

@learner  > /project list --in-review
@echo     > You have reviewed 2/5 projects this cycle. Nice work!

               Project                  C    Q    Artifact
            X  #terrible-tiger          63   42   https://github.com/owner/repo
            X  #anxious-aardvark        19   77   https://github.com/owner/repo
            -  #silly-slug                        https://github.com/owner/repo
            -  #fantastic-falcon                  https://github.com/owner/repo
            -  #creepy-caterpillar                https://github.com/owner/repo
@learner  > /review #silly-slug
@echo     > Project #silly-slug has 4 reviews. You have not reviewed project #silly-slug.

            To review this project, analyze their artifact:
            > http://link.to.artifact/

            Use the rubric provided to calculate and submit a `--completeness` and `--quality` score.
@learner  > /review #silly-slug --completeness 89
@echo     > Completeness score captured for #silly-slug! Review is not yet complete.
@learner  > /project list --in-review
@echo     > You have reviewed 2/5 projects this cycle. Nice work!

               Project                  C    Q    Artifact
            X  #terrible-tiger          63   42   https://github.com/owner/repo
            X  #anxious-aardvark        19   77   https://github.com/owner/repo
            -  #silly-slug              89        https://github.com/owner/repo
            -  #fantastic-falcon                  https://github.com/owner/repo
            -  #creepy-caterpillar                https://github.com/owner/repo
@learner  > /review --quality 103
@echo     > Error: missing project id.

            When reviewing a project, be sure to include its id (for example, #bitter-bunny-2).

            Use `/review --help` to read the docs.

@learner  > /review #silly-slug --quality 103
@echo     > Error: invalid quality score.

            Quality scores must be between 1 and 100 inclusive. Decimals up to the hundreds place are allowed.

            Use `/review --help` to read the docs.

@learner  > /review #silly-slug --quality 72
@echo     > Quality score captured for #silly-slug. Review is complete. Thank you for your input.
@learner  > /review #fantastic-falcon -c75.3 -q80.8
@echo     > Completeness and quality scores captured for #fantastic-falcon! Review is complete. Thank you for your input.
```

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
