# Member Actions

## Stories

### Basics

- Check status of cycles
  - `/cycle status`
  - `/cycle status <cycle-id>`
  - `/cycle status --project #project-id`
- Set artifact for project
  - `/project set-artifact #project-id <url>`
- Log retrospective reflection
  - `/retro #my-project`
- Show projects for review
  - `/project list -r`

## Flows

### Voting + Project Creation

Members vote on goals (after moderator runs `/cycle init`), and then projects are formed when the moderator runs `/cycle launch`.

At this time, a new channel is created for each project, named with the syntax `#<project-id>`.

#### Example

```
# moderator starts cycle
@mod      > /cycle init
@echo     > Cycle created! Voting can now begin.

# Members vote on goals
@member  > /vote 2
@echo     > Error: You must vote for exactly 2 goals. Try `--help` for usage.
@member  > /vote 2 5
@echo     > Vote recorded! You voted for goals 2 and 5.
@member  > /vote 7 5
@echo     > Vote recorded! You voted for goals 7 and 5.

# after voting is complete, moderator creates projects
@mod      > /cycle launch
@echo     > Voting is closed. Generating projects from goals...

# in project channel (#terrible-tiger) after projects have been created...
@echo     > Time to start work on your projects!

            The first step is to create an appropriate project artifact.
            Once you've created the artifact, connect it to your project with the `/project set-artifact` command.

            Run `/project set-artifact --help` for more guidance.
@member  > /project set-artifact https://github.com/owner/repo
@echo     > Error: invalid command - wrong number of arguments (1 for 2).

            Use `/project set-artifact --help` to read the docs.

@member  > /project set-artifact #terrible-tiger https://github.com/owner/repo
@echo     > Thanks! The artifact for project #terrible-tiger is now set to https://github.com/owner/repo.
```

#### Notification Example

After a Member completes their reflections, this message is sent as a DM to the member:

```
@echo     > One of your teammates has just submitted their reflections for this retrospective!
            2 / 5 retrospectives have been completed for this project.
```
