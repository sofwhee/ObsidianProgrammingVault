Really simply...
You're just labeling something as "blank"able.
"oh, this is blankable. Call the blank function on it then."

Then, whatever object is interacting with the interfaced object will just check if the interfaced object has the interface in question ("oh, this is blankable. Do this")

Behaviour that can be inherited by multiple unrelated classes.

Bullet, when hitting a crate, should call its damage function
Bullet, when hitting a person, should call its damage function
Bullet, when hittin a building, should call its damage function

Clothing , when landing on crate, should call its dropped function
Clothing, when landing on something else, should call its dropped function

Make an IDroppable interface
that will give every item that has it the correct dropped function