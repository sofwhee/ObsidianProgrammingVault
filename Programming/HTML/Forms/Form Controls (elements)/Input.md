
`input` is the most versatile.  Accepts [[Input|type]] attribute which tells the browser what _type_ of data it should expect and how it should render the input element.
## Input Types

`text` self explanatory.

`email` attribute validates correct formatting. (And include the @ on mobile device keyboards)

```html
<label for="user_email">Email Address:</label>
<input type="email" id="user_email" name="email" placeholder="you@example.com">
```

`password` inputs mask inputted data with asterisks.

```html
<label for="user_password">Password:</label>
<input type="password" id="user_password" name="password">
```

`number` input only accepts number values.

```html
<label for="amount">Amount:</label>
<input type="number" id="amount" name="amount">
```

`date` renders a date picker calendar.

```html
<label for="dob">Date of Birth:</label>
<input type="date" id="dob" name="dob">
```