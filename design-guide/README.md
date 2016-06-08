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

Read more detailed design specifications for [Command Interfaces](command-interfaces.md) and [Graphical Interfaces](graphical-interfaces.md).

For information on the structure and purpose of craft repositories, read [craft-repos.md](craft-repos.md).

## References

- http://www.cs.pomona.edu/classes/cs181f/supp/cli.html
- http://www.catb.org/esr/writings/taoup/html/design.html
- http://www.gnu.org/prep/standards/standards.html#Command_002dLine-Interfaces
- http://www.usabilityfirst.com/glossary/noun-verb-paradigm/
