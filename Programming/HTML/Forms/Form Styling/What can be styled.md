# Easy

1. [`<form>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form)
2. [`<fieldset>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/fieldset) and [`<legend>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/legend)
3. Single-line text [`<input>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)s (e.g. type text, url, email), except for [`<input type="search">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/search).
4. Multi-line [`<textarea>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea)
5. Buttons (both [`<input>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input) and [`<button>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button))
6. [`<label>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label)
7. [`<output>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/output)

May be styled using techniques from the articles [Your first form](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Your_first_form) and [CSS building blocks](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics).

There are also special selectors — [UI pseudo-classes](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/UI_pseudo-classes) — that enable styling based on the current state of the UI.
# Harder

The article [Advanced form styling](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Advanced_form_styling) shows how to style these.

- Checkboxes and radio buttons
- [`<input type="search">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/search)

# Can't be styled in CSS alone

- [`<input type="color">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/color)
- Date-related controls such as [`<input type="datetime-local">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/datetime-local)
- [`<input type="range">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/range)
- [`<input type="file">`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file)
- Elements involved in creating dropdown widgets, including [`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select), [`<option>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/option), [`<optgroup>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/optgroup) and [`<datalist>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/datalist).
- [`<progress>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress) and [`<meter>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meter)

For example, the date picker calendar, and the button on `select` that displays an options list when clicked, can't be styled using CSS alone.

The articles Advanced form styling and How to build custom form controls describe how to style these.

# [Fonts and text](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Styling_web_forms#fonts_and_text)

By default, some widgets do not inherit [`font-family`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-family) and [`font-size`](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size) from their parents.

Fix the inconsistency by doing it manually:
 
```CSS
button,
input,
select,
textarea {
  font-family: inherit;
  font-size: 100%;
}
```

Results on the following:

- `<input type="text">` 
- `<input type="date">`
- `<select>`  
- `<textarea>`
- `<input type="submit">` (Did not inherit. Use `<button>` instead)
- `<button>`


![[Pasted image 20250105162729.png]]

