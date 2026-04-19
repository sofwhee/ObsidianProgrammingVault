### HTML form validation

HTML form attributes can define which form controls are required and which format the user-entered data must be in to be valid.
#### Form Control Validation Attributes

Give you the ability to validate most user data without relying on JavaScript.

- [`required`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/required): Specifies whether a form field needs to be filled in before the form can be submitted.
- [`minlength`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/minlength) and [`maxlength`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/maxlength): Specifies the minimum and maximum length of textual data (strings).
- [`min`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/min), [`max`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/max), and [`step`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/step): Specifies the minimum and maximum values of numerical input types, and the increment, or step, for values, starting from the minimum.
- [`type`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#input_types): Specifies whether the data needs to be a number, an email address, or some other specific preset type.
- [`pattern`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/pattern): Specifies a [regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_expressions) that defines a pattern the entered data needs to follow.

https://developer.mozilla.org/en-US/docs/Web/HTML/Constraint_validation#validation-related_attributes

#### How Validation Works

When an element is valid, the following things are true:

- The element matches the [`:valid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:valid) CSS pseudo-class, which lets you apply a specific style to valid elements. The control will also match [`:user-valid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:user-valid) if the user has interacted with the control, and may match other UI pseudo-classes, such as [`:in-range`](https://developer.mozilla.org/en-US/docs/Web/CSS/:in-range), depending on the input type and attributes.
- If the user tries to send the data, the browser will submit the form, provided there is nothing else stopping it from doing so (e.g., JavaScript).

When an element is invalid, the following things are true:

- The element matches the [`:invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid) CSS pseudo-class. If the user has interacted with the control, it also matches the [`:user-invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:user-invalid) CSS pseudo-class. Other UI pseudo-classes may also match, such as [`:out-of-range`](https://developer.mozilla.org/en-US/docs/Web/CSS/:out-of-range), depending on the error. These let you apply a specific style to invalid elements.
- If the user tries to send the data, the browser will block the form submission and display an error message. The error message will differ depending on the type of error. The [Constraint Validation API](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation#the_constraint_validation_api) is described below.

#### Examples

##### Required (no empties)

Starting point:

![[Pasted image 20250105164259.png]]

```HTML
<form>
  <label for="choose">Would you prefer a banana or cherry?</label>
  <input id="choose" name="i-like" />
  <button>Submit</button>
</form>
```

```CSS
input:invalid {
  border: 2px dashed red;
}

input:valid {
  border: 2px solid black;
}
```

Make it required:

![[Pasted image 20250105164745.png]]
![[Pasted image 20250105164845.png]]
![[Pasted image 20250105164919.png]]

Make `input` `required`. Update `label` to tell the user it is now required. (WCAG guidelines)

```HTML
<form>
  <label for="choose">Would you prefer a banana or cherry? (required)</label>
  <input id="choose" name="i-like" required />
  <button>Submit</button>
</form>
```

```CSS
input:invalid:required {
  background-image: linear-gradient(to right, pink, lightgreen);
}
```

##### Pattern (specific inputs only)

RegEx.

![[Pasted image 20250105165152.png]]

![[Pasted image 20250105165121.png]]

```HTML
<form>
  <label for="choose">Would you prefer a banana or a cherry?</label>
  <input id="choose" name="i-like" required pattern="[Bb]anana|[Cc]herry" />
  <button>Submit</button>
</form>
```


##### Minlength Maxlength (constrain)

```HTML
    <input type="text" id="choose" name="i-like" required minlength="6" maxlength="6" />
```

### JavaScript form validation 

JavaScript is generally included to enhance or customize HTML form validation.
