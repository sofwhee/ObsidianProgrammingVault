# Summary

- Prototype is another object
- Works like a Python class with inheriting functions, properties...

# Example

```javascript
// Declare Prototype via Object Constructor function
function Person(name) {
  this.name = name;
}

// Give it functions
Person.prototype.sayName = function() {
  console.log(`Hello, I'm ${this.name}!`);
};

Player.prototype.getMarker = function() {
  console.log(`My marker is '${this.marker}'`);
};

// Declare Player Object Constructor function
function Player(name, marker) {
  this.name = name;
  this.marker = marker;
}

// Now make `Player` objects inherit from `Person`
Object.setPrototypeOf(Player.prototype, Person.prototype);
Object.getPrototypeOf(Player.prototype); // returns Person.prototype

// Create objects by calling 'new' on Object Constructors
// There's no need to call 'new' on Prototype Object Constructor
const player1 = new Player('steve', 'X');
const player2 = new Player('also steve', 'O');

player1.sayName(); // Hello, I'm steve!
player2.sayName(); // Hello, I'm also steve!

player1.getMarker(); // My marker is 'X'
player2.getMarker(); // My marker is 'O'
```