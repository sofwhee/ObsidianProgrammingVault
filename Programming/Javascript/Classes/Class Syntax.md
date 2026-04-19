```javascript
class MyClass {
  prop = value; // property

  constructor(...) { // constructor
    // ...
  }

  method(...) {} // method

  get something(...) {} // getter method
  set something(...) {} // setter method

  [Symbol.iterator]() {} // method with computed name (symbol here)
  // ...
}
```

example

```javascript
class User {

  constructor(name) {
    this.name = name;
  }

  sayHi() {
    alert(this.name);
  }

}

// Usage:
let user = new User("John");
user.sayHi();
```

## No comma between class methods

A common pitfall for novice developers is to put a comma between class methods, which would result in a syntax error.

The notation here is not to be confused with object literals. Within the class, no commas are required


There are important differences.

1. First, a function created by `class` is labelled by a special internal property `[[IsClassConstructor]]: true`. So it’s not entirely the same as creating it manually.
    
    The language checks for that property in a variety of places. For example, unlike a regular function, it must be called with `new`:
    
    [](https://javascript.info/class# "run")
    
    [](https://javascript.info/class# "open in sandbox")
    
    ``` `class` `User` `{`   `constructor``(``)` `{``}` `}`  `alert``(``typeof` User`)``;` `// function` `User``(``)``;` `// Error: Class constructor User cannot be invoked without 'new'` ```
    
    Also, a string representation of a class constructor in most JavaScript engines starts with the “class…”
    
    [](https://javascript.info/class# "run")
    
    [](https://javascript.info/class# "open in sandbox")
    
    ``` `class` `User` `{`   `constructor``(``)` `{``}` `}`  `alert``(`User`)``;` `// class User { ... }` ```
    
    There are other differences, we’ll see them soon.
    
2. Class methods are non-enumerable. A class definition sets `enumerable` flag to `false` for all methods in the `"prototype"`.
    
    That’s good, because if we `for..in` over an object, we usually don’t want its class methods.
    
3. Classes always `use strict`. All code inside the class construct is automatically in strict mode.
    

Besides, `class` syntax brings many other features that we’ll explore later.