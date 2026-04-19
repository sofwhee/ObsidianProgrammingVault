The word "asynchronous" just means "takes some time" or "happens in the future, not right now".

Code normally executes from top to bottom in order.
Async functions can execute at any time regardless of where they are in the code.

## Why?

Normal functions return things right away.
Functions that are async and use callbacks don't return anything right away.

```javascript
var photo = downloadPhoto('http://coolcats.com/cat.gif')
```

In this case the gif might take a very long time to download, and you don't want your program to pause (aka 'block') while waiting for the download to finish.

## Is this an async function or not?

The difference can be confusing. It depends a lot on context.
Usually things that have to **talk to hard drives or networks** will be asynchronous.