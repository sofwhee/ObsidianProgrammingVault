What `class User {...}` construct really does is:

1. It results in a `function` called `User`
2. The function code is taken from `constructor`
3. Stores methods in`User.prototype`

```javascript
class User {
  constructor(name) { this.name = name; }
  sayHi() { alert(this.name); }
}

// class is a function
alert(typeof User); // function

// ...or, more precisely, the constructor method
alert(User === User.prototype.constructor); // true

// The methods are in User.prototype, e.g:
alert(User.prototype.sayHi); // the code of the sayHi method

// there are exactly two methods in the prototype
alert(Object.getOwnPropertyNames(User.prototype)); // constructor, sayHi
```

```javascript
// rewriting class User in pure functions

// 1. Create constructor function
function User(name) {
  this.name = name;
}
// a function prototype has "constructor" property by default,
// so we don't need to create it

// 2. Add the method to prototype
User.prototype.sayHi = function() {
  alert(this.name);
};

// Usage:
let user = new User("John");
user.sayHi();
```

## It's different from other function objects

1. Labelled with a special internal property `[[IsClassConstructor]]: true`
	- Requires `new`
	- String rep starts with `class`
	- (Other changes)
1. Class `methods` have their `enumerable` flag set to `false` in `prototype`
	- So `for..in` doesn't return its class `methods`!
2. All code inside the class construct is automatically in `strict` mode.
3. (Other things not mentioned here...)
