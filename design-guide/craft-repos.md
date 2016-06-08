# Craft Repositories

Craft repositories are owned by the [GuildCrafts](https://github.com/GuildCrafts/) organization and are named after the craft that they focus on.

For example, the craft of "Web Development with JavaScript" is stored in the craft repo [web-development-js](https://github.com/GuildCrafts/web-development-js).

Each craft repository should follow a consistent file structure and repo metadata (issues, labels, milestones, etc.) patterns.

This document is a guide for setting up and managing craft repositories.

_Note: language here conforms to [RFC 2119](https://www.ietf.org/rfc/rfc2119.txt) standards._

## File Structure

Craft repositories _should_ use the following structure.

```shell
<repo-name>/
├── .github                 
│   └── ISSUE_TEMPLATE.md   # Template for writing goals
├── CONTRIBUTING.md         # Instructions for contributing and goal writing
├── README.md               # Self-explanatory
├── guides                  # Guides and helpful wisdom
│   ├── TEMPLATE.md         # Template file for writing guides
│   └── ...
└── library                 # Resource library (articles, videos, etc.)
    ├── TEMPLATE.md         # Template file for adding resources
    └── ...
```

## Issues

Issues on a craft repo are used as the **goal library** for the craft.

All issues _must_ use the standard issue template, unless they are non-goal issues.

## Pull Requests

Pull requests are used to update the content of a craft repository. Any active learner can open a pull request against the master branch of a craft repo to add/edit/remove content.

Only learners with proper privileges (for now, professional players) can accept/merge pull requests.

All changes to the files in craft repositories _must_ be made via pull requests, in line with [GitHub flow](https://guides.github.com/introduction/flow/).

## Labels

Labels are used to add metadata to goals that is consumed by our software to inform processes like project creation and stats assignment.

Because labels are also user-facing, they _must_ have human readable and intelligible names.

The number of labels may grow, so labels of a similar type _should_ be given similar colors.

### Label Types

#### Project/Team Size

The following labels denote recommended team size for a goal and _should_ all be given a **blue** color:

- `team-size-2`
- `team-size-3`
- `team-size-4`
- `team-size-5`

## Milestones

Milestones are used to demarcate broad, exclusive categorizations for goals.
