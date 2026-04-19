Serializes JSON data as a string.

Helps with compatibility issues.

```javascript
// Using toJSON() method
BigInt.prototype.toJSON = function () {
  return this.toString();
};
const str1 = JSON.stringify(data);

// Using JSON.stringify() with replacer
const str2 = JSON.stringify(data, (key, value) => {
  if (key === "gross_gdp") {
    return value.toString();
  }
  return value;
});
```