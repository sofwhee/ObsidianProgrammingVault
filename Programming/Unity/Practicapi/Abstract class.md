A class that is only there to give inherited behaviour, but has no meaning on its own.

`public abstract class Reward`
## Abstract method / properties
Force implementation on inheriting class, like an interface.

`public abstract string DisplayName { get; }`

## Different from Interface
Interfaces are not designed to have fields and methods with implementations

However, that wastes the single inheritance that the inheriting class can have.