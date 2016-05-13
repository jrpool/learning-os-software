# UI/UX Design Guide

This document guides the design of learner interfaces and the experiences of interacting with them.

## Design Constraints

Our interface and experience design is bounded by this set of design constraints:

- The chat environment is the primary learner interface.
- Customized secondary interfaces are avoided whenever possible.
- All learner actions are available via commands within the chat environment.
- We follow a command-line-first approach: all user actions are supported via a text command, with graphical interfaces being optional enhancements.
- All game-relevant data can be expressed in text format, including learner, team, project, and cycle state and attributes.
- In textual interfaces, we use noun-verb dialogues when many operations are needed for a single object, and verb-noun dialogues when multiple objects need a similar operation performed.

## Common Specifications for Commands

_Note: language here conforms to [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) standards._

### Use verbs for common actions

Commands for common and frequently used learner actions _should_ take the grammatical form of `verb + object`.

Objects can be omitted when not necessary or when a sensible default is available.

**Examples:**

```
> /vote 3 1          => vote on goals 3 and 1
> /request -h        => submit a help request
> /offer -f #bee-12  => offer feedback on project bee-12
> /log --retro       => log a retrospective
```

**Reason:** most command-line interfaces use verbs for commands, so learners will not have as much context switching to do when moving between other CLI environments and ours.

### Use nouns for navigation and inspection

Commands for navigation and inspection _should_ be nouns.

**Examples:**

```
> /profile            => open account profile panel
> /cycle              => show cycle stats
> /project            => show current project
> /goal 12            => show goal with id 12
> /goal search React  => search goals for text "React"
```

**Reason:** for looking at and searching for _things_ in the system, it is most natural to start with the _kind of thing_.

### Use object as context identifier for mutable actions when necessary

When a context is important for actions that mutate game state, the action _should_ be supplied as an argument to a command in noun form.

**Examples:**

```
> /goal create                     => make a new goal
> /cycle launch                    => start the cycle (form projects from votes)
> /project create 12               => create a new project from goal 12
> /project add #bee-12 @jerry -m   => add @jerry to project bee-12 as a team member
> /learner play                    => make current learner active
> /learner pause @jerry            => pause learner with handle @jerry
> /learner pause                   => pause the current learner
```

**Reason:** there will be a growing list of ways to interact with core game objects, so having an object-first approach provides important context and reduces overall amount of commands.

### Provide an immediate response

Every action _must_ respond with a "success" or "error" message or notification. As a user, I cannot verify that my command was received unless I see feedback.

**Good**:

```
> /vote 2 3
> Thanks for voting!
```

**Bad**:

```
> /vote 2 3   => (no response or change to UI)
```

### Provide a help message

When passed the option `--help` or `-h`, every command _must_ respond with a helpful message about the command.

The help message _should_ include a brief description, a list of possible arguments/options, and at least one usage example.

**Good**:

```
> /vote -h
>
> COMMAND
>   /vote [goalId] [goalId]
> DESCRIPTION
>   Vote on goals for the upcoming cycle. Each learner gets two votes per cycle.
>
>   When invoked with no arguments, opens the voting panel.
>
>   Voting multiple times will override previous votes.
> ARGUMENTS
>   goalId : The issue number of a goal (from the goal library)
> USAGE
>   /vote         // open the voting panel
>   /vote 2 5     // vote for goals 2 and 5
>   /vote 6 6     // vote for goal 6 twice
```

**Bad**:

```
> /vote -h
> Vote command. Vote on goals.
```

## References

- http://www.cs.pomona.edu/classes/cs181f/supp/cli.html
- http://www.catb.org/esr/writings/taoup/html/design.html
- http://www.gnu.org/prep/standards/standards.html#Command_002dLine-Interfaces
- http://www.usabilityfirst.com/glossary/noun-verb-paradigm/
