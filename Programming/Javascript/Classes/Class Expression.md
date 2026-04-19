Just like functions, you can put classes in variables (called a Class Expression)

Here’s an example of a class expression:

```javascript 
let User = class {
  sayHi() {
    alert("Hello");
  }
};
```

If a class expression has a name, it’s visible inside the class only:

```javascript
// "Named Class Expression"
// (no such term in the spec, but that's similar to Named Function Expression)
let User = class MyClass {
  sayHi() {
    alert(MyClass); // MyClass name is visible only inside the class
  }
};

new User().sayHi(); // works, shows MyClass definition

alert(MyClass); // error, MyClass name isn't visible outside of the class
```

Dynamically make classes "on-demand":

```javascript
function makeClass(phrase) {
  // declare a class and return it
  return class {
    sayHi() {
      alert(phrase);
    }
  };
}

// Create a new class
let User = makeClass("Hello");

new User().sayHi(); // Hello
```