Private properties get created by using a hash `#` prefix and cannot be legally referenced outside of the class. 

It is a syntax error to refer to `#` names from outside of the class.

Most class properties have their private counterparts:
- Not constructors. You have to use a **private flag** for these.
- Private fields
- Private methods
- Private static fields
- Private static methods
- Private getters
- Private setters
- Private static getters
- Private static setters
## Syntax:

- All private identifiers declared within a class must be unique. 
	- The namespace is shared between static and instance properties. 
	- The only exception is when the two declarations define a getter-setter pair.
- The private identifier cannot be `#constructor`.


```javascript
class ClassWithPrivate {
  #privateField;
  #privateFieldWithInitializer = 42;

  #privateMethod() {
    // …
  }

  static #privateStaticField;
  static #privateStaticFieldWithInitializer = 42;

  static #privateStaticMethod() {
    // …
  }
}
```