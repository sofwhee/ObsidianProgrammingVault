Singleton
- Class with private construcor
- That exposes a public static instance of itself
- All of its properties can be accessed from anywhere in code
- Initialize on Awake
- `DontDestroyOnLoad(this)`

ScriptableObjectArchitecturePattern (SOAP)
- Make it a scriptableobject instead
- Available in all scenes

Singletons don't scale
Waste memory until game closed
Main menu is kept even during gameplay
Everything is fully accessible even when it shouldn't be
Tight Coupling
Messy dependencies

ObjectResolver
- Holds a single dict that maps each type to its instance
- Methods to register and unregister instances
- You need to register each class to it on Awake
- Can get instance by type
- Need to manually pass the object resolver to each class

Pros:
- Can remove things from memory as needed during runtime to save on memory
Cons:
- Have to manually remember every class instead of autocompleteing

Dependency Injection

Instead of creating a dependency

```C#
private ClassB _classB;

public void SetDependencies()
{
	_classB = Singleton.Instance.ClassB;
}
```

The class passes it to you instead

```C#
private ClassB _classB;

public void Inject(ClassB classB)
{
	_classB = classB;
}
```

You can write it yourself, or use VContainer, or Modest Tree Zenject.
https://vcontainer.hadashikick.jp/