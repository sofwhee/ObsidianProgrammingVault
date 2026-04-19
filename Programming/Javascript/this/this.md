`this` references the object that is currently calling the function.

```javascript
let counter = {
  count: 0,
  next: function () {
    return ++this.count;
  },
};

counter.next();
```

## Global context

In the global context, the `this` references the [global object](https://www.javascripttutorial.net/es-next/javascript-globalthis/), which is the `window` object on the web browser or `global` object on Node.js.

This behavior is consistent in both strict and non-strict modes. Here’s the output on the web browser:

`console.log(this === window); // true`

If you assign a property to `this` object in the global context, JavaScript will add the property to the global object as shown in the following example:

`this.color= 'Red'; console.log(window.color); // 'Red'`

## Function context

In JavaScript, you can call a function in the following ways:

- Function invocation
- Method invocation
- Constructor invocation
- Indirect invocation

Each function invocation defines its own context. Therefore, the `this` behaves differently.
### 1) Simple function invocation

In the non-strict mode, the `this` references the global object when the function is called as follows:

`function show() {    console.log(this === window); // true }  show();`Code language: JavaScript (javascript)

When you call the `show()` function, the `this` references the [global object](https://www.javascripttutorial.net/es-next/javascript-globalthis/), which is the `window` on the web browser and `global` on Node.js.

Calling the `show()` function is the same as:

`window.show();`Code language: JavaScript (javascript)

In the strict mode, JavaScript sets the `this` inside a function to `undefined`. For example:

`"use strict";  function show() {     console.log(this === undefined); }  show();`Code language: JavaScript (javascript)

To enable the strict mode, you use the directive `"use strict"` at the beginning of the JavaScript file. If you want to apply the strict mode to a specific function only, you place it at the top of the function body.

Note that the strict mode has been available since ECMAScript 5.1. The `strict` mode applies to both function and nested functions. For example:

`function show() {     "use strict";     console.log(this === undefined); // true      function display() {         console.log(this === undefined); // true     }     display(); }  show();`Code language: JavaScript (javascript)

Output:

`true true`Code language: JavaScript (javascript)

In the `display()` inner function, the `this` also set to `undefined` as shown in the console.

### 2) Method invocation

When you call a method of an object, JavaScript sets `this` to the object that owns the method. See the following `car` object:

`let car = {     brand: 'Honda',     getBrand: function () {         return this.brand;     } }  console.log(car.getBrand()); // Honda`Code language: JavaScript (javascript)

In this example, the `this` object in the `getBrand()` method references the `car` object.

Since a method is a property of an object which is a value, you can store it in a variable.

`let brand = car.getBrand;`Code language: JavaScript (javascript)

And then call the method via the variable

`console.log(brand()); // undefined`Code language: JavaScript (javascript)

You get `undefined` instead of `"Honda"` because when you call a method without specifying its object, JavaScript sets `this` to the global object in non-strict mode and `undefined` in the strict mode.

To fix this issue, you use the `[bind()](https://www.javascripttutorial.net/javascript-bind/)` method of the `Function.prototype` object. The `bind()` method creates a new function whose the `this` keyword is set to a specified value.

`let brand = car.getBrand.bind(car); console.log(brand()); // Honda`
Code language: JavaScript (javascript)

In this example, when you call the `brand()` method, the `this` keyword is bound to the `car` object. For example:

`let car = {     brand: 'Honda',     getBrand: function () {         return this.brand;     } }  let bike = {     brand: 'Harley Davidson' }  let brand = car.getBrand.bind(bike); console.log(brand());`Code language: JavaScript (javascript)

Output:

`Harley Davidson`

In this example, the `bind()` method sets the `this` to the `bike` object, therefore, you see the value of the `brand` property of the `bike` object on the console.

### 3) Constructor invocation

When you use the `new` keyword to create an instance of a function object, you use the function as a constructor.

The following example declares a `Car` function, and then invokes it as a constructor:

`function Car(brand) {     this.brand = brand; }  Car.prototype.getBrand = function () {     return this.brand; }  let car = new Car('Honda'); console.log(car.getBrand());`Code language: JavaScript (javascript)

The expression `new Car('Honda')` is a constructor invocation of the `Car` function.

JavaScript creates a new object and sets `this` to the newly created object. This pattern works great with only one potential problem.

Now, you can invoke the `Car()` as a function or as a constructor. If you omit the `new` keyword as follows:

`var bmw = Car('BMW'); console.log(bmw.brand); // => TypeError: Cannot read property 'brand' of undefined`Code language: JavaScript (javascript)

Since the `this` value in the `Car()` sets to the global object, the `bmw.brand` returns `undefined`.

To make sure that the `Car()` function is always invoked using constructor invocation, you add a check at the beginning of the `Car()` function as follows:

`function Car(brand) {     if (!(this instanceof Car)) {         throw Error('Must use the new operator to call the function');     }     this.brand = brand; }`Code language: JavaScript (javascript)

ES6 introduced a meta-property named [`new.target`](https://www.javascripttutorial.net/es6/javascript-new-target/) that allows you to detect whether a function is invoked as a simple invocation or as a constructor.

You can modify the `Car()` function that uses the `new.target` metaproperty as follows:

`function Car(brand) {     if (!new.target) {         throw Error('Must use the new operator to call the function');     }     this.brand = brand; }`Code language: JavaScript (javascript)

### 4) Indirect Invocation

In JavaScript, [functions are first-class citizens](https://www.javascripttutorial.net/javascript-functions-are-first-class-citizens/). In other words, functions are objects, which are instances of the [Function type](https://www.javascripttutorial.net/javascript-function-type/).

The `Function` type has two methods: `[call()](https://www.javascripttutorial.net/javascript-call-function/)` and `[apply()](https://www.javascripttutorial.net/javascript-apply-method/)` . These methods allow you to set the `this` value when calling a function. For example:

`function getBrand(prefix) {     console.log(prefix + this.brand); }  let honda = {     brand: 'Honda' }; let audi = {     brand: 'Audi' };  getBrand.call(honda, "It's a "); getBrand.call(audi, "It's an ");`Code language: JavaScript (javascript)

Output:

`It's a Honda It's an Audi`Code language: PHP (php)

In this example, we called the `getBrand()` function indirectly using the `call()` method of the `getBrand` function. We passed `honda` and  `audi` object as the first argument of the `call()` method, therefore, we got the corresponding brand in each call.

The `apply()` method is similar to the `call()` method except that its second argument is an array of arguments.

`getBrand.apply(honda, ["It's a "]); // "It's a Honda" getBrand.apply(audi, ["It's an "]); // "It's a Audi"`