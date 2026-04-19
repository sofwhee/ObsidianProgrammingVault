Sometimes it doesn't make sense to be checking Update() every frame to see if something happened yet!

With event based logic, it's possible to wait for something to happen, and then respond when it does.

## The Observer Pattern

Subject ----- Observer

Allows you to connect functionality of a script to an event in your game.

It allows Subjects to respond to things in your game without needing to tightly connect everything together. Observers manage their own connections to a subject's events.

That means the subject doesn't need to prepare for an observer to do anything, it will just broadcast and let observers pick up its radio waves.

[[The Observer Pattern in Unity]]
## Delegates

Event --- trigger --- Observer

Essentially function containers.

Delegate = variable that holds 1 or more functions, calls them when triggered.

Why?
"The player's health script might call an OnDeath delegate when its health drops to 0.
A UI object could subscribe to that delegate to show a Game Over when it happens.
Neither object relies on the other to exist.
The UI object manages its own reference to the delegate."

Risks
- Delegate needs to be publicly available
- So it's possible to accidentally **set** the delegate instead of adding to it
- Which would fuck up other functions that rely on the delegate
- Any script can call the delegate, which confuses which object is the subject and observer
- Using event delegates helps with this

How to use:
```C#
public class Character : MonoBehaviour
{

delegate void OnPlayerDeath();
OnPlayerDeath onPlayerDeath;

private void Start()
{
// When delegate function is called, it will execute all functions in itself
// Add, remove functions from delegate function.
onPlayerDeath = PlayerDeathFunction // or
onPlayerDeath += PlayerDeathFunction // or
onPlayerDeath -= null
}
// always check if null before using
if (onPlayerDeath != null) 
// or
onPlayerDeath?.Invoke();
```

## EventDelegates

Useful to prevent public access to delegate from all over the program. Makes it easier to avoid errors.

Good for game-wide events rather than just local objects.

Can only be called from inside its own class.

```C#
public delegate void OnPlayerDeath();
// need to declare "event" delegate here
public static event OnPlayerDeath onPlayerDeath
```

## Actions in Unity

Basically ready-made delegates. Great way to make event delegates in code.

Don't return a value, but can take parameters.

```C#
public static event Action onPlayerDeath;
public static event Action<float> onPlayerHurt;
```

## Unity Events

Set a trigger in inspector.
Unity event ---- Response

Lets you create modular connections in the Unity inspector!

Best used for connecting local objects. Such as scripts on the same object or group of objects.

Example:
![[Pasted image 20260416090339.png]]
![[Pasted image 20260416090403.png]]

Both objects can...
- take damage through OnDamageTaken() 
- be destroyed by OnDamageTaken()

You can make them respond in different ways to the same methods in the inspector!

1. Add UnityEngine.Events namespace
2. Declare a public UnityEvent
3. Trigger using Invoke

```C#
public UnityEvent onDamageTaken;
...
if (velocity > minVelocity)
{
	onDamageTaken.Invoke();
}
```

For dynamic data: (for example, you can also set the amount of damage taken as a float)

![[Pasted image 20260416090616.png]]

```C#
public UnityFloatEvent onDamageTaken;
...
if (velocity > minVelocity)
	onDamageTaken.Invoke(velocity * damageMultiplier);

[System.Serializable]
public class UnityFloatEvent : UnityEvent<float> { }
```

## Scriptable Object Events

**(GameEvent)** The fuse for a bunch of GameEventListeners -->
**(GameEvent)** Is **CALLED!!!** Light the beacons! Send the calvary!!! -->
**(GameEvent)** All subscribed GameEventListeners are triggered -->
**(GameEventListener)** Attached to Wants-To-Respond-To-Events-Object --> 
**(GameEventListener)** GameEvent **screams** in its listening ear --> 
**(GameEventListener)** Responds with Unity Events -->

### GameEvent Script:

GameEvent is a ScriptableObject asset
![[Pasted image 20260416092522.png]]
Contains a list of subscribed listeners
![[Pasted image 20260416092538.png]]
Provides functions so that it can subscribe to listen to an event, or remove listeners.
![[Pasted image 20260416092558.png]]
When a listened event is called, each
![[Pasted image 20260416092627.png]]

### GameEvent Listener Script:

The Observer.
A script that attaches to any object that wants to respond to an event.

Will subscribe itself to an event...
![[Pasted image 20260416092215.png]]
Will trigger its own unity event in response to that subscribed event being called.
![[Pasted image 20260416092240.png]]
Which can be manually connected to other scripts / objects.
![[Pasted image 20260416092342.png]]

To connect a listener to a specific event
- connect the Game Event to the GameEventListener
- connect the same Game Event to the event-broadcasting-object

(Here we connect OnPlayerDeath event to the Health object, which will scream that the player died
and a GameEventListener that will listen for that scream and respond.)![[Pasted image 20260416094952.png]]
![[Pasted image 20260416095026.png]]

### Subject (Object) Script

```C#
// Simply declare a GameEvent...
public GameEvent onPlayerDeath;

public void RemoveHealth(float amount)
{
	...
	// And call the TriggerEvent() function on it.
	if (hp < 0)
		onPlayerDeath.TriggerEvent()
}
```
### In Summary...

Strength of gamewide events.
Strength of local object connections with unity inspector.
Allows a layer of abstraction between the subject and observer. Keeps them nicely decoupled.
Observers can subscribe to an object's events without needing an object reference.

![[Pasted image 20260416091655.png]]



```C#

```