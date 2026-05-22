A ScriptableObject is a Unity object that's not part of a gameobject instance.

Create a class with less overhead than monobehaviour.
- No tranform
- Not in scene
- lives as an asset

Useful for anything that doesn't need to change at runtime.

- Store them in variables
- Dynamically create them or destroy them at runtime
- Pass them as args
- Return them from methods
- Include them in data structures
- Serialize/Deserialize

Useful for balancing
- In the editor, values changed during runtime do not return back
- (not so in production)

## Differences between mono and SO

![[Pasted image 20260502115426.png]]

## Event Functions

![[Pasted image 20260502115521.png]]
![[Pasted image 20260502115539.png]]
![[Pasted image 20260502115852.png]]
## Reference it

```C#
public Class MyMonoBehaviour : MonoBehaviour
{
	public ScriptableObject soInstance;
}
```

##