email: https://mail.google.com/mail/u/0/#inbox/FMfcgzQgMCWGQRhwHRfcXVbPMvqKtgKr

"New modules. Several are already uploaded and in preview state. 

When I published 301 to review as a participant, I ran into two issues almost immediately:

The course description page needs edited. It was uploaded my Maria’s partner however, she doesn’t know how to make the edits. 

When I took the first quiz, I didn’t pass and it won’t allow me to advance. Our previous modules were set up to have endless tries until you score 80% or above. 

Could you please tell us what needs to be done to correct these issues do we can move forward with the process?"

Affected platform: Lighthouse Cove LMS
Feature: Quiz
Specific content: Course Module 301 Quiz 1

Steps already taken: None
Screenshots: None so far
Exact Timestamps: None so far
Browser or device details: Haven't collected
The environment: Production

Attempt to reproduce in a comparable environment.
Was unable to reproduce issue, works fine on my end.

Check known issues


Good day Darryl,

  

I have a more complex issue with this client than it seemed.

  

This client can't retry a quiz that he is previewing. He's trying to upload a new course module. He failed and the system doesn't let him retry. However, it allows me to retry when I tried to replicate the issue.

  

I checked our Jira board and found this ticket from a week ago with the same client having the same problem: https://workerbee-dev-team.atlassian.net/browse/FSR-1103

  

The end result was that he seemed to have completed it once, then gone back and retaken it to fail on purpose. Because he had completed it previously with a passing score, it was marked as complete which prevented any future attempts.

  

There isn't a built in workaround to reset or retake the quiz after it's been marked complete through the preview feature.

  

Jillana left a comment saying she would inform the client that we could provide a one-time fix, but otherwise we will expedite the migration to the new LMS so they have this feature available.

  

They have sent this email to us seemingly unaware​

---
Daryll meeting 05 28

Log in as kmetz
- use URL to log in
- ![[Pasted image 20260528103802.png]]
- go to course topic on left
- 301
- view/edit course det
- Can't hide the course in the old platform because it doesn't let us access it
- Can still go to course and simulate taking the course
- Max attempts reached... escalate to debug

Log in as Kmetz (they have to be in the system for it to work)
https://lms.professionaltrainingmatters.org/?who=entv2team&pass=u1EBx3Y9n1FB&email=example@email.org