# Task List

The task list is responsible for helping Learners Guild users to "get things done" and keep on top of things that need to be completed at various points in the program.

## Use Cases

### Task Creation and Assignment

A Partner needs to add a Task that needs to be completed for a given phase. She visits the Task List service and is presented an interface to add the task and target it to one or more groups of users.

### Task Viewing

A user wants to know what outstanding tasks she has yet to complete. From the [Group Collaboration](group-collaboration.md) service, she asks the Task List bot to show her unfinished tasks and the bot replies with the list of tasks she has yet to complete.

### Task Completion

After completing a task, a user can mark the task as complete and add the task submission (text, URL, etc.) if it is required.

### Nagging

At the beginning of each day, the Task List bot should message each user the list of her outstanding tasks. In addition, if a task has been languishing, the user will be sent a message to complete the task. Whether or not the user will be nagged about a task (and how often) is determined by whether or not the task is required and its priority.

## Future Use Cases

- Incentives: Scoreboards for different Learners, Pods, Cohorts, etc.
- Auto-completion: a plugin architecture that sense when a task has been completed. Would likely require some kind of webhook.

## Data Owned

- tasks
  - description
  - target (e.g., Users, Pod, Cohort, Chapter, All Learners, etc.)
  - submission type (none, text, URL)
  - repeating?
  - when?
    - repeat interval
    - relative to point-in time (now, start date, beginning of phase, etc.)
  - required / optional
  - priority (low, normal, high)
- task completions
  - user id
  - task id
  - task submission text
  - task response URL
  - timestamp
