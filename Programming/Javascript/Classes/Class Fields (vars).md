Class fields are a recent addition to the language.

Previously, classes only had `methods`. “Class fields” is a syntax that allows to add any `properties`.

[[Losing 'this'#Class Solution (Class fields)|Class Fields solve the 'Losing This' problem!]]

The important difference of class fields is that they are set on individual objects, not `User.prototype`. Example:

```javascript
class User {
  name = "John";
}

let user = new User();
alert(user.name); // John
alert(User.prototype.name); // undefined
```