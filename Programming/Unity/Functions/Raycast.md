Ray = Point -> Direction

Origin is a transform.position.
Direction is a normalized Vector 3 (0, 0, 1) (length of vector is always unit. it's a direction)

Raycast Hit = Contains information about a ray's collision with an object.
Once a ray hits an object, you can check the Raycast data to check what the object was, where it happened, or the tag of the collider that was hit. 

`if (Physics.Raycast(ray, out RaycastHit hit))`

It's a physics function. So you're using Physics, Physics2d, Collider, Collider2d etc.
## Raycast Function types 

### Physics.Raycast 

lets you cast a ray, and if it hits something, saves that data into the "out" keyword.
Returns a bool.
```C#
if (Physics.Raycast(ray, out RaycastHit hit)) {...}

// Overloads

if (Physics.Raycast(ray, out RaycastHit hit, maxDistance, layersToHit))
// layersToHit will exclude certain layers from being hit (using a layer mask)
// Layermasks let you specify which layers of objects a raycast check should include.

public LayerMask layersToHit;

void Start()
...
// ^^^ Then use the unity dropdown to select a layermask.
// then pass the variable into the raycast check's parameters..
// you MUST use a maxDistance for some reason
// you can also use 1<<9. wathc video to understand this
if (Physics.Raycast(... layersToHit))
```

### RaycastAll

![[Pasted image 20260415220738.png]]

Returns an unsorted array of collisions.

Sort them with Array.Sort.
```C#
// Array.Sort lets you compare items against each other, in this case by distance.
Array.Sort(hits, (RaycastHit x, Raycasty) => x.distance.CompareTo(y.distance))
```

```C#
void CheckForColliders() 
{
	hits = Physics.RaycastAll(ray);
	
	if(hits.Length > 0) 
	{
	}
}
```

### RaycastNonAlloc
A cheaper version of RaycastAll.
Returns an int value of how many things were hit by the ray.

![[Pasted image 20260416110200.png]]
### Linecast
Instead of a ray, it's a line with a defined start and end point.
Can be easier to use than Raycast sometimes.

`if (Physics.Linecast(startPoint, endPoint)`

### Collider.Raycast

![[Pasted image 20260415221612.png]]

Returns true when it's hit by collider it's called from.
Useful when you only want to check if one collider is hit, such as the Player.

```C#
// Syntax
// colliderToHit should be the collider you're checking is hit
// maxDistance is a float like 100
void CheckForColliders()
{
	if(colliderToHit.Raycast(ray, out RaycastHit hit, maxDistance))
	{ Debug.Log("The orange cube was hit!") }
}
```

### SphereCast CapsuleCast BoxCast

Useful for checking if a specific size object will fit into a space.
Or just projecting a wider shaped ray.

Project a primitive shape into the scene instead of a ray.

![[Pasted image 20260415222213.png]]

```C#
// (ray, thiccnesss)
Physics.SpherecCast(ray, 0.5f)
// Declare size of cube by using a Vector3 for its half extents
// (the distance from the center of the object, to its surface in each direction)
Physics.BoxCast(transform.position, boxSize / 2, transform.forward)
```

A one-unit cube.

![[Pasted image 20260415222535.png]]

Capsule is defined by the two points of the capsule and its radius.

![[Pasted image 20260415222758.png]]

Then, it's swept through the scene in whatever direction you choose using the max distance.

![[Pasted image 20260415222909.png]]

```C#
Physics.CapsuleCast(position1, position2, 0.5f, transform.forward)
```

### Plane.Raycast

Detects collisions against an invisible plane in the scene. 

Extremely useful for detecting collisions against a virtual floor or wall.

Returns true when the plane is hit, and passes out a distance value.

![[Pasted image 20260415223123.png]]

Lightweight since it doesn't require a collider or even a game object to work.

Useful for giving a mouse raycast a surface to interact with.

```C#
// make a plane by passing in a Vector3 direction for the 'in normal'
// AKA, the back side of the plane.
// Then, give it an offset.
Plane plane = new Plane(Vector3.down, 0)
...
if (plane.Raycast(ray, out float distance)) 
{
	// useful with GetPoint, which returns a real position along the ray
	transform.position = ray.GetPoint(distance);
}

// Shoot ray where mouse is
Ray cameraRay = Camera.main.ScreenPointToRay(Input.mousePosition);
```

## Raycast 2D

Instead of a boolean, they now usually return a RaycastHit 2d value instead.

This means it's probably easier to just store it in a variable and check if it returned.

```C#
RaycastHit2d raycastHit2D = Physics2D.Raycast(transform.position, Vector3.right);

if (racyastHit2D) { Debug.Log("Something was hit!")}
```
### Collider 2D

It works in reverse!

![[Pasted image 20260415224556.png]]

The collider you call the function from is considered the origin of the ray.

It checks for other colliders, but ignores its own.

```C#
// Similar to RaycastNonAlloc
// Returns an int equal to the numebr of results hit
// Meanwhile, the RaycastHit 2Dcollisions are stored in a pre-existing array.
public Collider2D myCollider;
RaycastHit2D[] hits = new RaycastHit2D[5]

private void Start()
{
	myCollider = GetComponent<Collider2D>();
	
	int numHits = myCollider.Raycast(Vector2.right, hits);
	
	if (numHits > 0)
	{
		// Something was Hit!
	}
}
```

### RaycastAll

It DOES sort its results for some reason.

### Layermasks

We use 2d Contact Filters instead!

To use them, set a public contactFilter2D variable...
Set it in the inspector...
Pass the contactFilter2D as a parameter into one of the raycast overloads (that support it)

```C#
public ContactFilter2D contactFilter;
RaycastHit2D[] hits = new RaycastHit2D[5];

private void Start()
{
	int numHits = Physics2D.Raycast(transform.position, Vector3.right)
}
```

### Physics2D.OverlapPoint

An OverlapPoint is conceptually like looking at the scene through an infinitely small hole to determine what can be seen. Any Collider2D seen can be detected and reported.

Checks a point against all Colliders in the scene, returning all intersections.

```C#
// Get world position with mouse
Vector3 screenPosition = Input.mousePosition;
screenPosition.z = 0;
Vector3 worldPosition = Camera.main.ScreenToWorldPoint(screenPosition);
// Return the first collider hit
Collider2D collider = Physics2D.OverlapPoint(worldPosition);
Debug.Log(collider);
```

### GraphicsRaycaster

As long as you have graphics raycaster on the canvas it will do most of the heavy lifting.

1. mouse -> connect -> script
	1. Object (with script)
		1. Add an event trigger component
		2. Add appropriate pointer events (pointer click/down/up/enter/exit)
		3. Wire pointer events to functions
2. UnityEngine.Events.IPointerHandler
	1. Put the events you want to handle on the class
	2. This will add methods to the class that get called on appropriate mouse event


GraphicRaycaster
This component is attached to a Canvas to allow interaction with UI elements (Images, Buttons) on that specific canvas. 

How it works: It checks if input (mouse/touch) hits any graphic element within its assigned canvas, accounting for sortOrderPriority.
Use Cases: Standard UI interaction, detecting clicks on a specific HUD canvas.
Limitation: It only knows about objects on its own Canvas. 

2. EventSystem.current.RaycastAll
This is a method called through the EventSystem to perform a comprehensive raycast against all active BaseRaycaster components in the scene. 

How it works: It polls all registered GraphicRaycaster, PhysicsRaycaster, and Physics2DRaycaster components, sorts the results by distance, and returns them in a list.
Use Cases: When you need to know everything under the mouse cursor, including UI elements and 3D objects behind them, or for custom raycasting logic (e.g., in VR).
Limitation: It can be expensive if there are many UI elements or physics colliders in the scene, as it does not have broadphase collision detection. 