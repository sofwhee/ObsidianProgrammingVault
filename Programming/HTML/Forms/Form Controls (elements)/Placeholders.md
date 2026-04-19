`placeholder` places a pre-filled value.
`input` is a void element (no closing tag), so you can also use `value` to pre-fill a value.
`textarea` just type it in.

```html
<form action="/my-handling-form-page" method="post">
  <p>
    <label for="name">Name:</label>
    <input type="text" id="name" name="user_name" placeholder="Bob"/>
  </p>
  <p>
    <label for="mail">Email:</label>
    <input type="email" id="mail" name="user_email" value="example@email.com"/>
  </p>
  <p>
    <label for="msg">Message:</label>
    <textarea id="msg" name="user_message">
    by default this element is filled with this text
    </textarea>
  </p>
</form>
```