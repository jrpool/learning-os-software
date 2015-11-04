# Feedback

The Feedback system is responsible for soliciting interpersonal feedback from one user to another within Learners Guild. It also allows feedback recipients to rate the feedback they receive based on certain, specific criteria.

## Use Cases

### Admissions Pod Formation Feedback

Upon the completion of a pair-programming challenge during the Admissions process, an Applicant receives a request from the Feedback service to provide feedback on the other Applicant:
  - Do you want to be in a Pod with <your pairing partner>?
    - (scale 1 to 5): 1 == NO WAY, 5 == DEFINITELY
  - How confident are you about your answer?
    - (scale 1 to 5): 1 == NOT AT ALL, 5 == VERY
  - Please rate <your pairing partner> on the following attributes (scale 1 to 5): 1 == NOT AT ALL, 5 == VERY:
    - kind
    - curious
    - passionate
    - communicative
    - collaborative

### Feedback on Feedback

After a user views her feedback, she receives a request from the Feedback service to rate the feedback she just received.
  - Please rate the feedback you just received on the following attributes (scale 1 to 5): 1 == NOT AT ALL, 5 == VERY
    - kind
    - actionable
    - specific


## Data Owned

- feedback structures (e.g., feedback during admissions process may be different than feedback during program enrollment, feedback between Partners may be different than feedback between Learners, etc.)
- feedback from one user to another
- feedback ratings
