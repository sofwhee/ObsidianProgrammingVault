Clothing PSB
- What should the layers be named?

**Resources Folder**: To load sprites by name without inspector references, use `Resources.Load<Sprite>("YourSpriteName")`. Note that this requires placing the files in a folder specifically named "Resources".

Hide and show layers based on what clothing is placed.
if we run into performance issues, we'll deal with them as they appear
- Spawning EVERY POSSIBLE CLOTHING ALL AT ONCE but *hidden*
	- not really realistic, awfully resource intensive
- Spawning clothing, then hiding original body part sprite
	- very realistic maybe?

Spawn clothing on character (current option)
- In photoshop, put clothing on character on its own layers so it overlaps correctly.
- hide character underneath, import PSB to Unity
- Make clothing puppet match character when in the rig
	- I found a way to do this when I put the clothing in the base character PSD...
	- might be worth exploring this as an option
- When it's time to put clothing on, spawn clothing on character in correct position in heirarchy, in correct position locally

steps once I have time
1. Make sure shirt character rig is all set up to be on character
2. instantiate character rig when it's time
	1. give it a SPrite Skin
	2. Set its root bone as Character Transform
	3. Bone should match character bones for body part
	4. change its localPosition based on how it best fits characterw

SMART IDEA ALERT
MAKE A PSB FOR TOPS, BOTTOMS< HATS, ETC
MAKE THE TOPS MATCH THE FIT PERFECTLY
GIVE IT BONES THAT MATCH THE CHARACTER
AND THEN YOU ONLY NEED ONE SET OF LOCAL POSITION TRANSFORMS TO MAKE IT ALL FIT!! :DDDDDD
CAUSE THEY ALL WILL SPAWN IN EXACTLY THE SAME SPOT
FUCK IM SO SMART
THEN JUST COPY AND PASTE THAT PSB AND EDIT THEM ALL INDIVIDUALLY TO ONLY HAVE THEIR OWN SELF IN THE LAYER

Step 1 make clothing rig in PSB
Step 2 Import
Step 3 Set up bones and mesh to match character exactly
Step 4 Turn on Auto Rebind in Sprite Skin
Step 5 Write method to assign the clothing sprite skin root bone to the character, and the other bones to the matching character bones
Step 6 Connect an event to this method (calling this method with an event)
Step 7 edit details if needed
Step 8 FIGURE OUT HOW TO DO SORTING LAYERS RIGHT