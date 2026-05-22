InputSystem.CallbackContext
- A data structure
- Used by input system package
- to provide info about what triggered an **input event**
- Passed as a parameter (like PointerEvents) to callback methods (like OnJump, OnMove, etc.)
- when an action is performed
Use it to:
- Read Input Values using stuff like `ReadValue<T>()` 
	- `float` for trigger
	- `Vector2` for joystick
- Identify Action Phases
	- Tells you if the action started
	- performed (completed)
	- or was canceled (released button)
- Identify what button / device was used via `control` property
- Track timing
	- `time` - timestamp for when event ocurred
	- `startTime` - timestamp for when event began
	- useful for measuring hold durations
Properties:
- `ReadValue<T>()` Extracts the input value (`ReadValue<Vector2>()` for movement)
- `performed` true if the action's trigger requirements are fully met
- `started` boolean, indicates if input began (button first touched)
- `canceled` boolean, if input was stopped or interrupted
- `duration` how long action has been in progress
Usage Constraint
CallbackContext should not be stored for later use. If you need data later, store the specific value (like the Vector2) instead.