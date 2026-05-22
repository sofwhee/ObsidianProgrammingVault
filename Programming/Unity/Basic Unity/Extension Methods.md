Normal static methods that can be called from anywhere in our code.

```C#
public static class GameObjectExtensions
{
	// Use "this" keyword so you can...
	public static void ResetToParent(this Transform transform, Transform parent)
	{
		transform.SetParent(parent);
		transform.localPosition = Vector3.zero;
		transform.rotation = Quaternion.identity;
		transform.localScale = Vector3.one;
	}
}

public void ObtainGun(Transform newGun)
{
	// turn the order around from this...
	GameObjectExtensions.ResetToParent(newGun, _handTransform);
	// to this!
	newGun.ResetToParent(_handTransform);
}
```