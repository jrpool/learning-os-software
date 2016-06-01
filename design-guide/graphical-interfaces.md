# Design Specifications for Graphical Interfaces

_Note: language here conforms to [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) standards._

## Collapsible anchored components have symmetrical toggle buttons

**Collapsible anchored components** are graphically anchored in a permanent UI element but can be made visible or invisible by the user.

For example, collapsible side panels are anchored components because they expand and collapse into a permanently visible sidebar element.

When designing collapsible anchored components, follow these guidelines:

- Collapsible components _must_ have a graphical toggle switch for both "open" and "close" actions.
- The action required to open/close any collapsible anchored element _should_ be as symmetrical as possible.

**Reason:** graphical interfaces should provide affordances similar to physical environments so that users do not become confused or disoriented. Having an element that can be opened but not closed, or whose open "button" is asymmetrical to its close "button", requires greater cognitive energy than one that enforces greater symmetry. Think of the difference between having a drawer that opens/closes by pulling/pushing on its handle and one that opens by pushing a button in a different location, and closes by pushing the drawer in (i.e. a cash register). Cash registers are intentionally difficult to use for security purposes; we need not introduce such difficulties under normal circumstances.
