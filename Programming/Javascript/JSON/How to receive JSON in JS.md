1. Make a [[Request]] object. `new Request(requestURL`
2. Use [[Fetch]] with Request to get Response object. `await fetch(<request object>)`
3. Retrieve JSON from Response object using its `.json()` method. `await response.json()`

### Fetch API

Make network requests to retrieve resources from a server via JavaScript 
(e.g. images, text, JSON, even HTML snippets)

## Example

You are making a website using JSON data to populate elements.
### Top-level

1. Declare `requestURL` variable to store GitHub URL.
2. Use the URL to initialize a new `Request` object.
3. Make the network request using `fetch()`, returning a `Response` object.
4. Retrieve the response as JSON using the `json()` function of the `Response` object.

```javascript
async function populate() {
  // populate

  // store GitHub URL
  const requestURL =
    "https://mdn.github.io/learning-area/javascript/oojs/json/superheroes.json";
  const request = new Request(requestURL); // initialize Request object

  const response = await fetch(request);
  const superHeroes = await response.json();

  populateHeader(superHeroes);
  populateHeroes(superHeroes);
}
```
