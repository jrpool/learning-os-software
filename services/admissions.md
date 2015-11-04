# Admissions

The Admissions service manages the process of moving an Applicant to a Member Learner within a Pod. Not all Applicants, of course, will be accepted into a pod. It's also possible that some Applicants will already be Non-Member Learners.

It is quite possible that this is mostly a "front end" service with some associated background jobs, but that not much data is owned by this service specifically. It has dependencies on a huge number of other services.

## Use Case Examples

### Invite and Overview

An individual receives an email invitation to apply for Learners Guild. She clicks through to the link in the email and is taken to a page that explains Learners Guild, how it works, etc.

### Reject: Culture Mismatch

After reading and understanding how Learners Guild work, a potential Applicant clicks / taps "Apply" and is immediately directed to a psychographic survey (TBD) that will act as an initial filter for "culture fit" within Learners Guild. It is determined that the candidate is not a strong culture-fit and a friendly message explaining that is displayed.

### Reject: Missing Aptitude

A potential Applicant who passes the culture-screen is directed to a straight-forward aptitude challenge (TBD, but should require no previous programming experience). The applicant is unsuccessful with the challenge, and a friendly message explaining that is displayed.

### On-boarding

After passing the culture and aptitude screenings, an Applicant is redirected to the [Identity Management](identity-management.md) service to sign-up and create a profile. Once completed, she is directed back to the Admissions service to complete the on-boarding process, whereby she must indicate at least 3 time slots each week where she will be available for "pair programming challenges" with other applicants. After indicating her availability, she is offered the opportunity to explore challenges in the [Challenge Taking and Review](challenge-taking-and-review.md) service.

### Pairing Invitation

An Applicant receives an invite to work on a pair-programming challenge with another Applicant. After accepting the invitation, a calendar appointment will be automatically added to her calendar.

### Pod Formation

An Applicant is reminded by her calendar of a pair-programming challenge appointment that she has with another Applicant. She uses the [Challenge Taking and Review](challenge-taking-and-review.md) service to work with the other Applicant on the challenge, and upon completion receives a request from the [Feedback](feedback.md) service to provide feedback on the other applicant.

On a periodic basis, a background process will run within the Admissions service to:
  - assign next pairing-challenge partners
  - identify potential pod assignments for applicants
  - reject applicants after a certain amount of negative feedback has accumulated

### Status Check

An Applicant visits the Admissions service to check-in on her status within the admissions process. She is shown:
  - a progress meter displaying how far along in the process she is
  - a checklist of any as-yet-unfinished to-do items from the [Task List](task-list.md) service
  - statistics on the number of pairing sessions she has completed
  - pod assignment (if determined)


## Data Owned

- documentation about what Learners Guild is, how it works, etc.
- interactive aptitude challenges
