### Input.mousePosition (old input manager)
(or mouse.current.position.readValue in the new input manager)
Gives pixel coordinates of the mouse.

However, now you have to convert it to a position in the game world...
### Camera.ScreenToWorldPoint()

![[Pasted image 20260415231641.png]]

This can be useful when you want the mouse to physically occupy a space in the world!

Note: Returns a Z value of 0.

So if you do this...

```C#
screenPosition = Input.mousePosition
worldPosition - Camera.main.ScreenToWorldPoint(screenPosition);
objectToMove.transform.position = worldPosition
```

... You'll just teleport the object to the camera's position.

So just give the screen position a z-value!

```C#
screenPosition = Input.mousePosition

// add a z (you can use anything to put it at least in front of the cam)
// .nearClipPlane is just the area where the camera clips objects.
screenPosition.z = Camera.main.nearClipPlane + 1;

worldPosition - Camera.main.ScreenToWorldPoint(screenPosition);
objectToMove.transform.position = worldPosition
```

### Camera.ScreenPointToRay()

If you want to interact with collider'd objects in the world...
(selecting objects, rubbing a wall or floor...)

Instead of returning a Vector3 pos, it returns a ray!

That you can then plug into a [[Raycast]] function.
(find position against other objects. other colliders, a wall, the floor...)

(*You may need to use a [[Raycast#Layermasks|Layermask]] to exclude any colliders you don't want to interact with.)

```C#
// this makes maxDistance overload required (sigh)
// you can also just use 1<<6 (if layerMask is the 6th layer)
public Layermask layersToHit;

screenPosition = Input.mousePosition;
// shoot the ray from the camera in the direction of the camera!!! PEWWW
Ray ray = Camera.main.ScreenPointToRay(screenPosition);

// Check for raycast hitting a collider
If (Physics.Raycast(ray, out RaycastHit hitData, maxDistance, layersToHit)) 
{
	worldPosition = hitData.point;
}

transform.position = worldPosition;
```

### Plane.Raycast()

Don't want to use colliders? Use this!

Allows you to get raycast data via an invisible Plane surface!

Useful for strategy games, simulation games, board simulating games, UI...

Declare a new plane...
new Plane(Vector3.down, 0)
(We use Vector3.down because it's the backside of the plane. The 'In Normal'.) 
(Adding a positive value will bring it closer, negative further away.)

```C#
screenPosition = Input.mousePosition;
Ray ray = Camera.main.ScreenPointToRay(screenPosition);

if (plane.Raycast(ray, out float distance))
{
	worldPosition = ray.GetPoint(distance);
}

transform.position = worldPosition;
```

### Camera.ScreenToViewportPoint()

Viewport space is normalized and relative to the camera. Bottom left is (0, 0), top right is (1, 1). Z is in world units from the camera.

Screen: from (0, 0) to (Screen.width, Screen.height)
Viewport: from (0, 0) to (1, 1)

```C#
```



```C#
```


```C#
```