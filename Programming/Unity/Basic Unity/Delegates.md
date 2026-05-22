String is a type for text
Delegate is a type for methods

Action
Function
Events
Anonymous methods
Lambda Expressions

When Invoked, they all perform the same

Lambda Expressions - uses no memory when reused
## When they're useful

Delegates
- Insert logic into another method
```C#
var levels = new List<int> {1, 3, 4, 5, 7, 8};
var levelsUnderFive = levels.FindAll(level => level < 5); // 1 3 4
```
- Pass callback method as a parameter
```C#
playButton.onClick.AddListener(OnClick)
```
- Listen to, like events
```C#
missionsService.OnMissionCompleted += OnMissionCompleted;
```

## Why not an Event

Events are the element's protector.
External classes cannot change it or invoke it.
Not so for delegates!

"Events are Stationary"
"Delegates are Passed Around"