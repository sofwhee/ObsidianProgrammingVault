A global instance of a class that survives scene loading.

Introduces global state which makes testing difficult.

- Class with private construcor
- That exposes a public static instance of itself
- All of its properties can be accessed from anywhere in code
- Initialize on Awake
- `DontDestroyOnLoad(this)`

Singletons don't scale
Waste memory until game closed
Main menu is kept even during gameplay
Everything is fully accessible even when it shouldn't be
Tight Coupling
Messy dependencies