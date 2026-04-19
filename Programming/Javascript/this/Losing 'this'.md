 Once a method is passed somewhere separately from the object – `this` is lost.
 
```javascript
let user = {
  firstName: "John",
  sayHi() {
    alert(`Hello, ${this.firstName}!`);
  }
};

setTimeout(user.sayHi, 1000); // Hello, undefined!
```

It gives you undefined because `setTimeout` changes `this`.

```javascript
setTimeout(thing, 1000);

// this = window / this = Timer Object in NodeJS
// any `this` calls passed to it are now...
// "window.<call>" instead of "this.<call>"
// which does not exist, so you get 'undefined'
```

It lost the `User` context because it received `user.sayHi` separately (??) from the object.

```javascript
// old line
setTimeout(user.sayHi, 1000); // Hello, undefined!

// this is what it actually does
let f = user.sayHi;
setTimeout(f, 1000); // lost user context
```
## How do we avoid this problem?

### Solution 1: a wrapper

The simplest solution
(If `user` changes during `setTimeout`'s one-second delay, it will call the wrong object. Solution 2 fixes that)

Solution 1:

```javascript
setTimeout(function() {
  user.sayHi(); // Hello, John!
}, 1000);
```

Now it receives `user` from the outer lexical environment, and calls it normally without changing anything inside.

Shortened:

```javascript
setTimeout(() => user.sayHi(), 1000); // Hello, John!
```

### Solution 2: bind

[[bind]]

A "bound" function will always have the right context. Delays don't matter.

```javascript
let user = {
  firstName: "John",
  sayHi() {
    alert(`Hello, ${this.firstName}!`);
  }
};

let sayHi = user.sayHi.bind(user);
```

```javascript
// can run it without an object
sayHi(); // Hello, John!

setTimeout(sayHi, 1000); // Hello, John!
```

## Class Solution (Class fields)

The class field `click = () => {...}` is created on a per-object basis.

Each `Class object` gets a separate `click` function, with the `this` inside of it maintaining its context. `this` will always be correct.

```javascript
class Button {
  constructor(value) {
    this.value = value;
  }
  click = () => {
    alert(this.value);
  }
}

let button = new Button("hello");

setTimeout(button.click, 1000); // hello
```
