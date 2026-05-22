#Interface

Instead of inheriting from a class, just reference the class from a variable.

```C#
public class InheritingClass : InheritedClass
//...

public class InheritingClass
{
	private InheritedClass inheritedClass;
}
```

## Problem Example:

![[Pasted image 20260503001930.png]]

Our vampire can't attack **and** heal.
Because it can't inherit from two diff classes.

Interfaces and abstract class to the rescue!

![[Pasted image 20260503001908.png]]