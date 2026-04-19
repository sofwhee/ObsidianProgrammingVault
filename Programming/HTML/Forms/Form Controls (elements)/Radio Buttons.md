`radio` buttons. (best user experience for 5 or less options.)

When we select one of the radio buttons and then select another, it will deselect the first one. Radio buttons know to do this because they have the same `name` attribute. This is how the browser knows these elements are part of the same group of options.

```html
<h1>Ticket Type</h1>
<div>
  <input type="radio" id="child" name="ticket_type" value="child">
  <label for="child">Child</label>
</div>

<div>
  // 'checked' makes it the default selected radio button
  <input type="radio" id="adult" name="ticket_type" value="adult" checked> 
  <label for="adult">Adult</label>
</div>

<div>
  <input type="radio" id="senior" name="ticket_type" value="senior">
  <label for="senior">Senior</label>
</div>
```