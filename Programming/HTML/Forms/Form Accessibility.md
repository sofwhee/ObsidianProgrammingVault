### Accessibility:
`label` 
`fieldset`

Ideally, long forms should be spread across multiple pages, but if a form is getting long and must be on a single page, putting the different related sections inside different `fieldsets` improves usability.

Each time you have a set of radio buttons, you should nest them inside a [`<fieldset>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) element.

In addition to the [`<fieldset>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) element, it's also common practice to use HTML titles (e.g. [h1](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements), [h2](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements)) and sectioning (e.g. [`<section>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/section)) to structure complex forms.

In the case of multiple labels, you should nest a widget and its labels inside a single [`<label>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label) element.

it's common practice to wrap a label and its widget with a [`<li>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/li) element within a [`<ul>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ul) or [`<ol>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol) list. [`<p>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/p) and [`<div>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div) elements are also commonly used.

Each separate section of functionality should be contained in a separate [`<section>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/section) element, with [`<fieldset>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) elements to contain radio buttons.

The paragraph at the top states a rule for required elements.

The rule must be included _before_ it is used so that sighted users and users of assistive technologies such as screen readers can learn what it means before they encounter a required element.

```html
<p>Required fields are followed by <span aria-label="required">*</span>.</p>

<!-- So this: -->
<!--div>
  <label for="username">Name:</label>
  <input id="username" type="text" name="username" required>
  <label for="username"><span aria-label="required">*</label>
</div-->

<!-- would be better done like this: -->
<!--div>
  <label for="username">
    <span>Name:</span>
    <input id="username" type="text" name="username" required>
    <span aria-label="required">*</span>
  </label>
</div-->

<!-- But this is probably best: -->
<div>
  <label for="username">Name: <span aria-label="required">*</span></label>
  <input id="username" type="text" name="username" required />
</div>
```

![[Pasted image 20250105161155.png]]
