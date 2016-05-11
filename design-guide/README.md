# UI/UX Design Guide

This document guides the design of learner interfaces and the experiences of interacting with them.

## Design Constraints

Our interface and experience design is bounded by this set of design constraints:

- The chat environment is the primary learner interface.
- Customized secondary interfaces are avoided whenever possible.
- All learner actions are available via commands within the chat environment.
- We follow a command-line-first approach: all user actions are supported via a text command, with graphical interfaces being optional enhancements.
- All game-relevant data can be expressed in text format, including learner, team, project, and cycle state and attributes.

## Common Specifications for Commands

_Note: language here conforms to [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) standards._

### Use verbs for actions

Commands for user actions _should_ take the grammatical form of `verb + object`.

Objects can be omitted when not necessary or when a sensible default is available.

**Examples:**

```
> /vote 3 1             => vote on goals 3 and 1
> /request help         => submit a help request
> /play                 => make current learner active
> /pause @jerry         => pause learner with handle @jerry
> /pause                => pause the current learner
> /search --goal React  => search goals for text "React"
```

### Use nouns for navigation and inspection

Commands for navigation and inspection _should_ be nouns.

Commands in noun form _must not_ affect game state.

**Examples:**

```
/profile   => open account profile panel
/goals     => open goal library
/status    => show user stats
```

### Use nouns for options and argument modifiers

When options are provided for commands, they _should_ be nouns.

Argument modifiers _should_ be prefixed with `--` and be nouns.

**Examples:**

```
/status project       => show project status
/request feedback     => submit a feedback request
/search --goal React  => search goals for text "React"
```

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
