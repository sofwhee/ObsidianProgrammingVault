#CSS #Flexbox

Odd number of flexboxes:

Left Middle Right

Middle: {
	min-width: fit-content; (or whatever)
}

Left and Right {
	width: 100%;
}

Basically, you make the middle one have a set width, and the others have flexible width.
As long as the middle object has a set width and everything around it shrinks to accommodate it, it will be centered.

