![[Pasted image 20260418104933.png]]

Model: Holds your data
Presenter: Intermediary
View: Displays your data

But sometimes, the simple separation of Data and Display are enough.

![[Pasted image 20260418105726.png]]

## When to use

Use when 
- you feel like your code dependencies are jumping around unpredictably instead of logically in a step-by-step manner.
- It feels impossible to change one piece without affecting the whole system
- Adding new features takes a long time
- Fixing bugs feels excessively time-consuming.
## Why?

It's an extension of the single-responsibility principle from [[Programming/General web dev stuff/Design principles/SOLID|SOLID]].

If
- You have a larger UI-heavy game
- You have a large team
- You wanna divide work between Front end, back end, other specializations...
- You will be changing and maintaining code for a long time
- You want simplified unit testing
- Because gameplay logic is separate from UI, you can simulate objects to work with code without entering play mode
- Smaller classes are easier to read and keep functionality in your head.
Then because View and Presenter are separated, developing UI can happen nearly independently from the rest of the codebase.

## Why not?

- Benefits won't be apparent until project gets big enough.
- Takes more organization to pull off, because it must be consistently applied.
- Simple scripts don't yield many benefits from it
- Not every Unity component can be split like this.
Let unit tests guide you. If you need it for testing, do it.


## Model View Controller

Model: Holds data.
View: Presents data.
Controller: Changes data.

![[Pasted image 20260418110332.png]]

## MVP in Unity

The controller doesn't handle input in Unity. The view does.

Model <- Presenter <- View <- User
Model -> Presenter -> View <- User

![[Pasted image 20260418111520.png|214]]

UI events (Observer pattern)
Presenter object manipulates the Model (data)

## Examples

A game with targets that have health.

You can shoot the target, reducing its health to 0.
You can reset the targets.

User -> Target -> HealthPresenter -> Health
User clicks -> OnDamaged(50) -> Damage.Invoke(50) -> Decrement(50)
(User -> View -> Presenter -> Model)

User <- Target <- HealthPresenter <- Health
User sees it <- DisplayHealth() <- OnHealthChanged() <- UpdateHealth()