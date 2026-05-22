The D in [[Programming/General web dev stuff/Design principles/SOLID|SOLID]] principles.

It's when you take a dependency a class has, and you use an in-between class (AKA an Interface) to reverse it.

The idea is to never have high-level modules import from low-level modules. Both should depend on an abstraction.

Aim for as few dependencies between classes as possible.
## Why?

Dependencies create problems.

- Code becomes fragile. Extending it, changing it, causes bugs.
- Now you have to recode the original code every time you want to add functionality.
- Easier to work with other programmers when you aren't worried about breaking each other's code.

![[Pasted image 20260418154228.png]]

When one class knows too much about another, modifying it can damage the second, or vice versa. Aim for loose coupling and high cohesion.

If modifying / expanding your game is hard because it's fragile and resistant to modification, investigate the structure.

## Example Problem

Character triggers a switch, and a door opens.

Your instinct might be to do this:

![[Pasted image 20260418154902.png]]

The Door is responsible for the opening of the door geometry.
The Switch looks in the Door class, and uses the Open method in it.

**The problem:** What if the logic of the Switch needs to work on more than just a Door. Like a light? Or a giant robot?

You'd have to modify the original code of the Switch every time you want to extend functionality. 

#### Solution!

![[Pasted image 20260418155922.png]]

Sandwich an interface in between your classes!

Now the dependency is inverted. Door depends on the interface that Switch controls.

![[Pasted image 20260418160217.png]]

## How to implement

```C#
public interface ISwitchable
{
	public bool IsActive { get; }
	public void Activate();
	public void Deactivate();
}
```

Switch

```C#
public class Switch : MonoBehaviour
{
	public ISwitchable client;
	public void Toggle()
	{
		if (client.IsActive)
		{
			client.Deactivate();
		}
		else
		{
			client.Activate();
		}
	}
}
```

Door

```C#
public class Door : MonoBehaviour, ISwitchable
{
	private bool isActive;
	public bool IsActive => isActive;
	public void Activate()
	{
		isActive = true;
		Debug.Log("The door is open.");
	}
	
	public void Deactivate()
	{
		isActive = false;
		Debug.Log("The door is closed.");
	}
}
```

## My example

