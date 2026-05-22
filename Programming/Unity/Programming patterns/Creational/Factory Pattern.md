You make code "factories" that create object "products".

Factories can spawn any gameplay element on an as-needed basis.
Even setting up UI elements in a dialog box.
Or parts of a game level.

Only worth doing if you have a large variety of things to spawn.

Pros
- Defining new product types doesn't change existing ones or require you to modify previous code
- Puts spawning code in its own, relatively short, script
- Makes code easier to maintain in the long run by decoupling
Cons
- Harder to read, lots of overhead. Multiple classes, subclasses...
- Only worth doing if you have a large variety of things to spawn.

![[Pasted image 20260418101130.png]]
![[Pasted image 20260418101150.png]]
## Adjustments you can make

- Use a dictionary to search for products.
	- Unique ID as the key
	- Type as a value
	- Makes retrieving products and/or corresponding factories easier
- Make factory / factory manager static.
	- Easier to use
	- But more setup
- Apply to any C# object, not just gameobjects and scripts
- Combine with object pool pattern
	- Factories can instead / also retrieve existing objects
	- Object pool pattern helps with memory management
	- example: instantiating a lot of weapon projectiles