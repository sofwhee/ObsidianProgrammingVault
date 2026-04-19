
Note - Prototype connections must be set *before* any objects are created!!

Also don't try to do it this way...
```javascript
Player.prototype = Person.prototype; // This doesn't work and causes problems
```

#### `Object`.setPrototypeOf(`object`)

```Javascript
Object.setPrototypeOf(Player.prototype, Person.prototype);
```
#### `object`.prototype `Object`.getProtoTypeOf(`object`)

(deprecated: `__proto__`, `[[Prototype]]`)

```javascript
Object.getPrototypeOf(player1) === Player.prototype; // returns true
Object.getPrototypeOf(player2) === Player.prototype; // returns true
```