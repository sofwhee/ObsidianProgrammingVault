https://rickharrison.github.io/validate.js/

JavaScript is generally included to enhance or customize HTML form validation.

If you want to change the text of the native error messages, JavaScript is needed. In this section we will look at the different ways to do this.

Automated messages have two drawbacks:

- There is no standard way to change their look and feel with CSS.
- They depend on the browser locale, which means that you can have a page in one language but an error message displayed in another language, as seen in the following Firefox screenshot.

# Constraint Validation API

The Constraint Validation API consists of a set of methods and properties available on the following form element DOM interfaces:

- [`HTMLButtonElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLButtonElement) (represents a [`<button>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button) element)
- [`HTMLFieldSetElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLFieldSetElement) (represents a [`<fieldset>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) element)
- [`HTMLInputElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement) (represents an [`<input>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input) element)
- [`HTMLOutputElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLOutputElement) (represents an [`<output>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/output) element)
- [`HTMLSelectElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLSelectElement) (represents a [`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select) element)
- [`HTMLTextAreaElement`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLTextAreaElement) (represents a [`<textarea>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea) element)

The Constraint Validation API makes the following properties available on the above elements.

- `validationMessage`: Returns a localized message describing the validation constraints that the control doesn't satisfy (if any). If the control is not a candidate for constraint validation (`willValidate` is `false`) or the element's value satisfies its constraints (is valid), this will return an empty string.
    
- `validity`: Returns a `ValidityState` object that contains several properties describing the validity state of the element. You can find full details of all the available properties in the [`ValidityState`](https://developer.mozilla.org/en-US/docs/Web/API/ValidityState) reference page; below is listed a few of the more common ones:
    
    - [`patternMismatch`](https://developer.mozilla.org/en-US/docs/Web/API/ValidityState/patternMismatch "patternMismatch"): Returns `true` if the value does not match the specified [`pattern`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#pattern), and `false` if it does match. If true, the element matches the [`:invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid) CSS pseudo-class.
    - [`tooLong`](https://developer.mozilla.org/en-US/docs/Web/API/ValidityState/tooLong "tooLong"): Returns `true` if the value is longer than the maximum length specified by the [`maxlength`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#maxlength) attribute, or `false` if it is shorter than or equal to the maximum. If true, the element matches the [`:invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid) CSS pseudo-class.
    - [`tooShort`](https://developer.mozilla.org/en-US/docs/Web/API/ValidityState/tooShort "tooShort"): Returns `true` if the value is shorter than the minimum length specified by the [`minlength`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#minlength) attribute, or `false` if it is greater than or equal to the minimum. If true, the element matches the [`:invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid) CSS pseudo-class.
    - [`rangeOverflow`](https://developer.mozilla.org/en-US/docs/Web/API/ValidityState/rangeOverflow "rangeOverflow"): Returns `true` if the value is greater than the maximum specified by the [`max`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#max) attribute, or `false` if it is less than or equal to the maximum. If true, the element matches the [`:invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid) and [`:out-of-range`](https://developer.mozilla.org/en-US/docs/Web/CSS/:out-of-range) CSS pseudo-classes.
    - [`rangeUnderflow`](https://developer.mozilla.org/en-US/docs/Web/API/ValidityState/rangeUnderflow "rangeUnderflow"): Returns `true` if the value is less than the minimum specified by the [`min`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#min) attribute, or `false` if it is greater than or equal to the minimum. If true, the element matches the [`:invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid) and [`:out-of-range`](https://developer.mozilla.org/en-US/docs/Web/CSS/:out-of-range) CSS pseudo-classes.
    - [`typeMismatch`](https://developer.mozilla.org/en-US/docs/Web/API/ValidityState/typeMismatch "typeMismatch"): Returns `true` if the value is not in the required syntax (when [`type`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#type) is `email` or `url`), or `false` if the syntax is correct. If `true`, the element matches the [`:invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid) CSS pseudo-class.
    - `valid`: Returns `true` if the element meets all its validation constraints, and is therefore considered to be valid, or `false` if it fails any constraint. If true, the element matches the [`:valid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:valid) CSS pseudo-class; the [`:invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid) CSS pseudo-class otherwise.
    - `valueMissing`: Returns `true` if the element has a [`required`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#required) attribute, but no value, or `false` otherwise. If true, the element matches the [`:invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid) CSS pseudo-class.
- `willValidate`: Returns `true` if the element will be validated when the form is submitted; `false` otherwise.

The Constraint Validation API also makes the following methods available on the above elements and the [`form`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form) element.

- `checkValidity()`: Returns `true` if the element's value has no validity problems; `false` otherwise. If the element is invalid, this method also fires an [`invalid` event](https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement/invalid_event) on the element.
- `reportValidity()`: Reports invalid field(s) using events. This method is useful in combination with `preventDefault()` in an `onSubmit` event handler.
- `setCustomValidity(message)`: Adds a custom error message to the element; if you set a custom error message, the element is considered to be invalid, and the specified error is displayed. This lets you use JavaScript code to establish a validation failure other than those offered by the standard HTML validation constraints. The message is shown to the user when reporting the problem.

# Custom Error Message (input element)

![[Pasted image 20250105170819.png]]
https://mdn.github.io/learning-area/html/forms/form-validation/custom-error-message.html

Make an HTML input with a compatible `type` for `typeMismatch`. ([[#Constraint Validation API]])
`<input type="email" id="mail" name="mail" />`

Put input element into a variable using its `id` value.
`const email = document.getElementById("mail");`

Add an event listener to it...
`email.addEventListener("input"...`

With an if statement using [[#Constraint Validation API]] properties `validity` and`typeMismatch`.
(If email `input`'s `validity` returns `typeMismatch`...)
`if (email.validity.typeMismatch) {...`

Resolving with `setCustomValidity`
`email.setCustomValidity("I am expecting an email address!");`

```HTML
<form>
  <label for="mail">
    I would like you to provide me with an email address:
  </label>
  <input type="email" id="mail" name="mail" />
  <button>Submit</button>
</form>
```

```javascript
const email = document.getElementById("mail");

email.addEventListener("input", (event) => {
  if (email.validity.typeMismatch) { // if [email input].validity returns typeMismatch
    email.setCustomValidity("I am expecting an email address!");
  } else {
    email.setCustomValidity("");
  }
});
```

![[Pasted image 20250105170819.png]]
https://mdn.github.io/learning-area/html/forms/form-validation/custom-error-message.html

# Constant Error Message


![[Pasted image 20250105172424.png]]
https://mdn.github.io/learning-area/html/forms/form-validation/detailed-custom-validation.html


```HTML
<form novalidate>
  <p>
    <label for="mail">
      <span>Please enter an email address:</span>
      <input type="email" id="mail" name="mail" required minlength="8" />
      <span class="error" aria-live="polite"></span>
    </label>
  </p>
  <button>Submit</button>
</form>
```

`novalidate` stops browser's auto validation and therefore error messages.
We need this since we're using the DOM to display the error message. 
(CSS `:valid` and the CVAPI are still good.)

```HTML
<form novalidate>
	(...)
</form>
```

`<span>` to hold our error message. `aria-live` for screen readers.

```HTML
	  <input...>
      <span class="error" aria-live="polite"></span>
```

How to format CSS when dealing with the CV API. 

```CSS
input[type="email"] {
}

/* invalid fields */
input:invalid {
}

input:focus:invalid {
}

/* error message styles */
.error {
}

.error.active {
}
```

Using DOM and event handlers, we check if the form fields are valid each time the user types something.

Collect elements with queries.

```javascript
const form = document.querySelector("form");
const email = document.getElementById("mail");
const emailError = document.querySelector("#mail + span.error");
```

Make + add eventListeners. 

- On email input
- if its `.validity` returns `valid`
- change error `<span>.textContent` to nothing
- change error `<s
- pan>.class` from "`.error.active`" to "`.error`"
- else show an error with `showError()`

```javascript
email.addEventListener("input", (event) => {
  if (email.validity.valid) { // if [email input].validity returns valid 
    emailError.textContent = ""; // Remove the message content
    emailError.className = "error"; // Class goes from "active" to "error"
  } else {
    // If there is still an error, show the correct error
    showError();
  }
});
```


```javascript
form.addEventListener("submit", (event) => {
  // if the email field is invalid
  if (!email.validity.valid) {
    // display an appropriate error message
    showError();
    // prevent form submission
    event.preventDefault();
  }
});

function showError() {
  if (email.validity.valueMissing) {
    // If empty
    emailError.textContent = "You need to enter an email address.";
  } else if (email.validity.typeMismatch) {
    // If it's not an email address,
    emailError.textContent = "Entered value needs to be an email address.";
  } else if (email.validity.tooShort) {
    // If the value is too short,
    emailError.textContent = `Email should be at least ${email.minLength} characters; you entered ${email.value.length}.`;
  }
  // Add the `active` class
  emailError.className = "error active";
}
```



```
<form novalidate>
  <p>
    <label for="mail">
      <span>Please enter an email address:</span>
      <input type="email" id="mail" name="mail" required minlength="8" />
      <span class="error" aria-live="polite"></span>
    </label>
  </p>
  <button>Submit</button>
</form>
```