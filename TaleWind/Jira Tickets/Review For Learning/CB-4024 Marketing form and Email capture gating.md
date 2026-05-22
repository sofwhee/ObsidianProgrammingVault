"Currently, on **Event posts**, Marketing Form gating and Email Capture gating options are unavailable in the new Event UI."

Break it down:
- Event posts - posts on our platform for events
- [[Marketing form gating]] and [[email capture gating]].
- New Event UI - a new UI TaleWind now has, specifically for managing Events as an Admin.
- This feature request proposes an enhancement to the new Event UI:
	- Apparently when we moved to the new Event UI, we removed the ability to choose Marketing Form gating and Email Capture gating in the access dropdown.
	- Potential conflict: Having the built-in registration form enabled will make a registration form show up
	- So if the customer has that enabled AND one of these gating types enabled, they could show up simultaneously. Which would be bad, UI wise.
	- Solution: Display an inline-warning if built-in registration form is enabled AND customer selects one of these types, to prevent this from happening.
		- Text: (warning icon) You cannot enable Marketing Form or Email Capture gating while the built-in registration form is active. Please disable the built-in registration form first.
- Built-in registration form
	- A pre-built form for registering a user, that TaleWind provides.
	- can be enabled or disabled
- Admin - a user who has the Admin role

### Daryll's thought process...

#### Description
- She started off by giving current behaviour as context, and explains why current behaviour is insufficient.
#### Proposed Enhancements
- She says which area of the codebase the change should take place (frontend, new event UI)
- If necessary, she then described which elements need their behaviour changed.
- She then describes the desired behaviour via logic, in english.
	- "assumes the built in registration form is not enabled" is an interesting way to portray a conditional
#### Expected Behavior
- She summarizes each proposed enhancement, as a review of the proposals.
- She also adds anything not covered in the proposals, such as whether it should work consistently in the old and new event UI.

#### Acceptance Criteria:
- 

- Why did Mark say this is an SPE concern because prev they were using Marketo? Maybe Marketo provided this before hand?