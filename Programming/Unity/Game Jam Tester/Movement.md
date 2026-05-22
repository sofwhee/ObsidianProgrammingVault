Sprite setup

- put sprites in the same animation state in one spritesheet
- put all walk cycles into one spritesheet
- settings:
	- Pixels per unit (set based on preference like 16 bit)
	- Filter mode None (point)
	- Compression NOne
	- Set game display to window size and scale to 1x
- open sprite sheet - slice it up!

Input
- Add Player Input component
- Create actions to put in Actions slot
- You can open input settings to peruse thru em but its good as is
- Write a movement script using [[InputSystem.CallbackContext]]
- `moveInput = context.ReadValue<Vector2>();`
- Default map = player
- Behaviour Invoke Unity Events
- Events - Player - Move - Runtime - Player object .Move

