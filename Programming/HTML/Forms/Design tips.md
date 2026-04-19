# Design tips

The bigger your form, the more you risk frustrating people and losing users. Keep it simple and stay focused: ask only for the data you absolutely need.

## Organizing Forms for User Friendliness

Use `button` instead of `input` where possible.

HTML provides a couple of elements that make it easy to organize forms into sections that are visually distinct and manageable to digest.

 `fieldset` element is a container element that allows us to group related form inputs into one logical unit.

`legend` element is used to give `fieldset` a heading or caption so the user can see what a grouping of inputs is for.

```html
<fieldset>
  <legend>Contact Details</legend>

  <label for="name">Name:</label>
  <input type="text" id="name" name="name">

  <label for="phone_number">Phone Number:</label>
  <input type="tel" id="phone_number" name="phone_number">

  <label for="email">Email:</label>
  <input type="email" id="email" name="email">
</fieldset>

<fieldset>
  <legend>Delivery Details</legend>

  <label for="street_address">Street Address:</label>
  <input type="text" id="street_address" name="street_address">

  <label for="city">City:</label>
  <input type="text" id="city" name="city">

  <label for="zip_code">Zip Code:</label>
  <input type="text" id="zip_code" name="zip_code">
</fieldset>
```

`radio` `fieldset`. (Common use)

```html
<fieldset>
  <legend>What would you like to drink?</legend>

  <div>
    <input type="radio" name="drink" id="coffee" value="coffee">
    <label for="coffee">Coffee</label>
  </div>

  <div>
    <input type="radio" name="drink" id="tea" value="tea">
    <label for="tea">Tea</label>
  </div>

  <div>
    <input type="radio" name="drink" id="soda" value="soda">
    <label for="soda">Soda</label>
  </div>
</fieldset>
```

## Consistent Design Across Browsers

To have a consistent design among all browsers, we have to override default styles.

Text-based form controls like `text`, `email`, `password` and `text area` are reasonably straightforward to style. They operate like any other HTML element, and most CSS properties can be used on them.

Things get more tricky when creating custom styles for radio buttons and checkboxes. But there are many guides out there you can use to achieve your desired design, such as this [guide on custom checkbox styling](https://moderncss.dev/pure-css-custom-checkbox-style). There have also been [new CSS properties](https://developer.mozilla.org/en-US/docs/Web/CSS/accent-color) made available in recent times to make styling radio buttons and checkboxes much easier.

Certain aspects of other elements are downright impossible to style, for example, `calendar` or `date` pickers. If we want custom styles for these, we will have to build custom form controls with **JavaScript** or use one of the many **JavaScript libraries** that provide us with ready-made solutions.