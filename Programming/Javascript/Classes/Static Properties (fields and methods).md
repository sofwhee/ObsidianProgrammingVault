**Defined on the class itself** instead of each instance.

`ClassInstance.staticMethod` will not work.
`TheClass.staticMethod` works.
## Uses

**Static properties** are useful for:
- caches
- fixed-configuration
- any other data you don't need to be replicated across instances.

**Static methods** are often utility functions, such as 
- creating objects
- cloning objects
## Syntax

(MDN Web Docs content uses the terms properties and fields interchangeably.)

```javascript
class ClassWithStatic {
  static staticField;
  static staticFieldWithInitializer = value;
  static staticMethod() {
    // …
  }
}
```
## Demo

```javascript
class ClassWithStaticMethod {
  static staticProperty = 'someValue';
  static staticMethod() {
    return 'static method has been called.';
  }
  static {
    console.log('Class static initialization block called');
  }
}

console.log(ClassWithStaticMethod.staticProperty);
// Expected output: "someValue"
console.log(ClassWithStaticMethod.staticMethod());
// Expected output: "static method has been called."
```