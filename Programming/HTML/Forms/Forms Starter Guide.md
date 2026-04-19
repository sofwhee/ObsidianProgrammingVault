Forms allow users to
- send data to a web server
- immediately update the interface of a website

**Form** **Controls** (widgets) - text fields, dropdowns, buttons, etc.
**Form Validation** - enforces formats/values.

[[Design tips]]
[[Form Accessibility]]
## How to build a form

### Design it:

![[Pasted image 20250105145801.png]]

### `form` element:

`form` - wraps all of the inputs a user will interact with.
`action` -  takes a URL value that tells the form where it should send its data to be processed.
`method` - tells the browser [which HTTP request method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) it should use to submit the form. The GET and POST request methods are the two you will find yourself using the most.

```html
<form action="/my-handling-form-page" method="post">…</form>
```

### Form Controls

`label`, `input`, `textarea`, etc...

The `<p>` elements are there to conveniently structure our code and make styling easier.

```html
<form action="/my-handling-form-page" method="post">
  <p>
  
  </p>
  <p>

  </p>
  <p>

  </p>
</form>
```

`label` informs users what type of data to enter.

`label` `for` connects to `form control` + `id`. 
(For screen-readers and accessibility. Mouse, trackpad, touch, click on label -> activates field.)

`input` is the most versatile.  Accepts [[Input|type]] attribute which tells the browser what _type_ of data it should expect and how it should render the input element.

`textarea` accepts text input and can be resized. `rows` and `cols` control initial height.

```html
<form action="/my-handling-form-page" method="post">
  <p>
    <label for="name">Name:</label>
    <input type="text" id="name"/>
  </p>
  <p>
    <label for="mail">Email:</label>
    <input type="email" id="mail"/>
  </p>
  <p>
    <label for="msg">Message:</label>
    <textarea id="msg"></textarea>
  </p>
</form>
```

`name` attribute, because we need to let the backend know what each piece of data represents. (You can think of it as a variable name for the input.)

```html
<form action="/my-handling-form-page" method="post">
  <p>
    <label for="name">Name:</label>
    <input type="text" id="name" name="user_name" />
  </p>
  <p>
    <label for="mail">Email:</label>
    <input type="email" id="mail" name="user_email" />
  </p>
  <p>
    <label for="msg">Message:</label>
    <textarea id="msg" name="user_message"></textarea>
  </p>
</form>
```

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

`button` so the form can be submitted!

Accepted [[Buttons|types]]: `submit` (sends via `action`), `reset`(clears), `button`(nothing).

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
  
  <p class="button">
    <button type="submit">Send your message</button>
  </p>
</form>
```

### Form Styling

Suggested CSS starting point:

```CSS
body {
  /* Center the form on the page */
  text-align: center;
}

form {
  display: inline-block;
  /* Form outline */
  padding: 1em;
  border: 1px solid #ccc;
  border-radius: 1em;
}

p + p {
  margin-top: 1em;
}

label {
  /* Uniform size & alignment */
  display: inline-block;
  min-width: 90px;
  text-align: right;
}

input,
textarea {
  /* To make sure that all text fields have the same font settings
     By default, text areas have a monospace font */
  font: 1em sans-serif;
  /* Uniform text field size */
  width: 300px;
  box-sizing: border-box;
  /* Match form field borders */
  border: 1px solid #999;
}

input:focus,
textarea:focus {
  /* Set the outline width and style */
  outline-style: solid;
  /* To give a little highlight on active elements */
  outline-color: #000;
}

textarea {
  /* Align multiline text fields with their labels */
  vertical-align: top;
  /* Provide space to type some text */
  height: 5em;
}

.button {
  /* Align buttons with the text fields */
  padding-left: 90px; /* same size as the label elements */
}

button {
  /* This extra margin represent roughly the same space as the space
     between the labels and their text fields */
  margin-left: 0.5em;
}
```

#### HTML Forms tutorial
https://internetingishard.netlify.app/html-and-css/forms/index.html

### Form Validation

### Sending Form Data

#### `action`

Normally, `action` value should be a file on the server that can handle the incoming data, including ensuring server-side validation. The server then responds, generally handling the data and loading the URL defined by the `action` attribute, causing a new page load (or a refresh of the existing page, if the `action` points to the same page).

Nothing - Form is sent to the same page the form is present on.

```html
<form>…</form>
```

Absolute URL `https://example.com`

```html
<form action="https://example.com">…</form>
```

Relative URL - different URL on the same origin.

```html
<form action="/somewhere_else">…</form>
```

#### What's being sent?

`name=value` pairs from form controls. Joined with "&".

```html
<form action="https://example.com/animals">
...
</form>
```

The preceding example makes a request to `https://example.com/animals`. A script on the `example.com` backend can handle requests to `/animals` and process data from the form.

By default, form data is sent as a `GET` request, with the submitted data appended to the URL. If a user submits 'frog' in the example above, the browser makes a request to the following URL:

`https://example.com/animals?animal=frog`

In this case, you can access the data on the frontend or the backend by getting the data from the URL.

Using `POST`, the data is included in the [body of the request](https://developer.mozilla.org/docs/Web/HTTP/Methods/POST#example).

```html
<form method="post">
...
</form>
```

The data will not be visible in the URL and can only be accessed from a frontend or backend script.

#### `method`

[HTTP protocol method.](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods) Usually POST or GET.

GET = "Hey server, I want to get this resource."
POST = "Hey server, take a look at this data and send me back an appropriate result."

### Sending form data to your web server

what: `name` (sent to server as name/value pairs)
where: `action` (URL)
why: `method` (`get` (default) `post`, `dialog` closes dialog and submits )

#### Viewing HTTP requests (Form data that was sent)

HTTP requests are never displayed to the user (if you want to see them, you need to use tools such as the [Firefox Network Monitor](https://firefox-source-docs.mozilla.org/devtools-user/network_monitor/index.html) or the [Chrome Developer Tools](https://developer.chrome.com/docs/devtools/)). As an example, your form data will be shown as follows in the Chrome Network tab. After submitting the form:

1. Open the developer tools.
2. Select "Network"
3. Select "All"
4. Select "foo.com" in the "Name" tab
5. Select "Request" (Firefox) or "Payload" (Chrome/Edge)

![[Pasted image 20250106125752.png]]

The only thing displayed to the user is the URL called. As we mentioned above, with a `GET` request the user will see the data in their URL bar, but with a `POST` request they won't. This can be very important for two reasons:

1. If you need to send a password (or any other sensitive piece of data), never use the `GET` method or you risk displaying it in the URL bar, which would be very insecure.
2. If you need to send a large amount of data, the `POST` method is preferred because some browsers limit the sizes of URLs. In addition, many servers limit the length of URLs they accept.

#### Event: `preventDefault()`

Tells the [user agent](https://developer.mozilla.org/en-US/docs/Glossary/User_agent) that if the event does not get explicitly handled, its default action should not be taken as it normally would be.

### Receiving the data locally through JS

1. Grab form element from DOM.
2. .elements = HTMLFormControlCollection object
3. HTMLFormControlCollection.namedItem("thing") = Form Control Element with the name
4. Form Control Element.value = its value property!

```javascript
dialogSubmit.addEventListener("click", function(event){
	event.preventDefault() // prevent default submit sending to web server
	// grab the form from DOM
	const bookForm = document.querySelector("form")
	// form.elements = HTMLFormControlCollection object
	// .namedItem("title") = Element object
	// Element.value = accesses the element's "value" property
	const title = bookForm.elements.namedItem("title").value
	const author = bookForm.elements.namedItem("author").value
	const pages = bookForm.elements.namedItem("pages").value
	const read = bookForm.elements.namedItem("read").value
	
	const fields = [title, author, pages, read]
	console.log(fields) // ["a title", "an author", "123", "on/off"]
})
```

### Receiving the data server-side

The way you access this list depends on the development platform you use and on any specific frameworks you may be using with it.

It's worth noting that it's very uncommon to use these technologies directly because this can be tricky. It's more common to use one of the many high quality frameworks that make handling forms easier, such as:

- Python
    - [Django](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Server-side/Django)
    - [Flask](https://flask.palletsprojects.com/)
    - [web2py](https://github.com/web2py/web2py) (easiest to get started with)
    - [py4web](https://py4web.com/) (written by the same develops as web2py, has a more Django-like setup)
- Node.js
    - [Express](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Server-side/Express_Nodejs)
    - [Next.js](https://nextjs.org/) (for React apps)
    - [Nuxt](https://nuxt.com/) (for Vue apps)
    - [Remix](https://remix.run/)
- PHP
    - [Laravel](https://laravel.com/)
    - [Laminas](https://getlaminas.org/) (formerly Zend Framework)
    - [Symfony](https://symfony.com/)
- Ruby
    - [Ruby On Rails](https://rubyonrails.org/)
- Java
    - [Spring Boot](https://spring.io/guides/gs/handling-form-submission/)

It's worth noting that even using these frameworks, working with forms isn't necessarily _easy_. But it's much easier than trying to write all the functionality yourself from scratch, and will save you a lot of time.

### Security Issues

HTML forms are by far the most common server attack vectors.

The problems never come from the HTML forms themselves — they come from how the server handles data.

https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Server-side/First_steps/Website_security

All data that comes to your server must be checked and sanitized. Always. No exception.

- **Escape potentially dangerous characters**. The specific characters you should be cautious with vary depending on the context in which the data is used and the server platform you employ, but all server-side languages have functions for this. Things to watch out for are character sequences that look like executable code (such as [JavaScript](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting) or [SQL](https://en.wikipedia.org/wiki/SQL) commands).
- **Limit the incoming amount of data to allow only what's necessary**.
- **Sandbox uploaded files**. Store them on a different server and allow access to the file only through a different subdomain or even better through a completely different domain.

You should be able to avoid many/most problems if you follow these three rules, but it's always a good idea to get a security review performed by a competent third party. Don't assume that you've seen all the possible problems.

## More on Form Controls

HTML5 input types (`search` `output` etc)
https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/HTML5_input_types

https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Other_form_controls
### [Using form controls outside of forms](https://www.theodinproject.com/lessons/node-path-intermediate-html-and-css-form-basics#using-form-controls-outside-of-forms)

It’s worth mentioning that you can use any of the form controls HTML provides outside of the `<form>` element, even when you don’t have a backend server where you can send data.

For example you might want to have an input that gets some data from a user and display that somewhere else on the page with JavaScript:


```html
<div>
  <label for="username">What's your name?</label>
  <input type="text"id="username">
  <button class="greet-btn">Greet Me</button>
</div>

<h1 class="greeting"></h1>
```

```javascript
const name = document.querySelector("#username")
const greetMeButton = document.querySelector(".greet-btn")
const greetingOutput = document.querySelector(".greeting")

greetMeButton.addEventListener('click', (event) => {
   greetingOutput.innerText = `Hello ${name.value}`;
})
```

![[Pasted image 20250105132124.png]]
![[Pasted image 20250105132137.png]]

