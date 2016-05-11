# Design Guide

This document guides the design of learner-facing interfaces.

## Constraints

Our interface design is guided by the following set of constraints:

- The chat environment is the primary learner interface.
- Custom secondary interfaces are avoided whenever possible.
- All learner actions are available via commands within the chat environment.
- We follow a command-line-first approach: all user actions are supported via a text command, with graphical interfaces being optional enhancements.
- All game-relevant data can be expressed in text format, including learner, team, project, and cycle state and attributes.

## Common Specifications

Every action **must** adhere to the following specifications.

### Provides an immediate response


_Note: language here conforms to [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) standards._

## References

- http://www.cs.pomona.edu/classes/cs181f/supp/cli.html
- http://www.catb.org/esr/writings/taoup/html/design.html
- http://www.gnu.org/prep/standards/standards.html#Command_002dLine-Interfaces
