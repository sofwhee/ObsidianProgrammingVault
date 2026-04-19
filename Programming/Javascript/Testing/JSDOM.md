# Setup

### Important note for jest >28

If you are using jest 28, you will need to install `jest-environment-jsdom` separately by either:

npm: `npm i jest-environment-jsdom --save-dev`

### `package.json`

```json
"jest":{
    "testEnvironment": "jsdom"
}
```

### `jest.config.[js|ts]`

```json
module.exports = {
    "testEnvironment": "jsdom"
}
```

# Usage

Put `@jest-environment jsdom` to set the environment to `jsdom`.

Now everything should work normally.

```javascript
/**
 * @jest-environment jsdom
 */

test('use jsdom in this test file', () => {
  const element = document.createElement('div');
  expect(element).not.toBeNull();
});
```

You will primarily use the `JSDOM` constructor.

Pass the constructor a string. You will get back a `JSDOM` object, which has a number of useful properties, notably `window`:

```javascript
const dom = new JSDOM(`<!DOCTYPE html><p>Hello world</p>`);
console.log(dom.window.document.querySelector("p").textContent); // "Hello world"
```

It can be used to act on the jsdom from the "outside," doing things that are not possible with the normal DOM APIs. 

For simple cases, where you don't need any of this functionality, we recommend a coding pattern like

```javascript
const { window } = new JSDOM(`...`);
// or even
const { document } = (new JSDOM(`...`)).window;
```

## Customizing JSDOM

(an example, look it up further if needed. https://github.com/jsdom/jsdom)

```javascript
const dom = new JSDOM(``, {
  url: "https://example.org/",
  referrer: "https://example.com/",
  contentType: "text/html",
  includeNodeLocations: true,
  storageQuota: 10000000
});
```

## Loading subresources

By default, jsdom will not load any subresources such as scripts, stylesheets, images, or iframes. 

If you'd like jsdom to load such resources, you can pass the `resources: "usable"` option, which will load all usable resources.

- Frames and iframes, via `<frame>` and `<iframe>`
- Stylesheets, via `<link rel="stylesheet">`
- Scripts, via `<script>`, but only if `runScripts: "dangerously"` is also set
- Images, via `<img>`, but only if the `canvas` npm package is also installed

### Virtual consoles

console.log and stuff...

### Cookie jars

Like web browsers, jsdom has the concept of a cookie jar, storing HTTP cookies.