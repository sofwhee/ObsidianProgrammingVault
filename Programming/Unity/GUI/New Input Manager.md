Action maps: Controls for walking, controlsinside a vehicle, controls in a plane

Action Type: 
Value - continuous input, like an analog stick.
Button - button
Pass Through - like value, but system decides which input is active

Save Asset  - found at the top.
## Player Input Component

Actions: Put in an Input Action Asset

Behaviour:
- Send Messages: triggers functions with certain names. (OnControlsChanged)
- Broadcast Messages: also triggers functions on child objects
- Invoke Unity Events, Invoke C# Events, use these usually

Events: Assign scripts to the controls you applied in the Actions widget.

Event > Player > Jump (spacebar) > public void Jump() {stuff}

Phases: 
- Jump Press = prepare
- Jump Pressing = perform
- Jump Release = canceled

