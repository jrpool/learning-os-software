# Surveys

The Surveys service is responsible for asking questions to users in the Learners Guild system, capturing the responses to these questions, and providing insights into the results of these questions.

## Use Cases

### Question Creation

Based on some analysis of currently-running Learners Guild experiment, a Partner wants to ask the Learners a specific question in order to gain insight into said experiment. She visits the Survey service and is presented an interface to add a question, specifying:
  - the question
  - the scale of possible responses
  - the target (e.g., Users, Pod, Cohort, Chapter, All Learners, etc.)
  - the frequency of administration (e.g., every 3 weeks, once per month on the first Tuesday)

### Response Collection

A background job determines that the frequency interval for a particular question has been reached, and (via a bot / direct-message into the [Group Collaboration](group-collaboration.md) service) issues the question to the set of users from which responses should be solicited. Once the user provides a valid response to the bot, the response is captured, and the current results (including graphs) for that question should be returned to the user.

Users should not be overwhelmed with survey questions; only one question should be asked every day or two. The frequency, combined with last response timestamp for a user should be used to compute (TBD - how?) the appropriate time to issue the next question to a given user.

### Nagging

In order to ensure responses are collected from each user, the bot should "nag" any users who have not yet responded at a logarithmic time interval (down to once per hour), until a response is captured.

### Reports and Visualization

A user wishes to see how her answers or a particular groups answers to a particular question have changed over time. She visits the Surveys system and is presented with a menu of options to visualize and see reports about.

## Data Owned

- survey questions
- responses
