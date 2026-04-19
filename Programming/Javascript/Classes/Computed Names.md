Just like a literal object, you can give methods computed names.

Here’s an example with a computed method name using brackets `[...]`:

```javascript
class User {

  ['say' + 'Hi']() {
    alert("Hello");
  }

}

new User().sayHi();
```

