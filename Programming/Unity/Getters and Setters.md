You can only read or write the value in a very specific manner.


## Why?

- You want to limit how values are set.
If health can only be 0 to 100, you can enforce that with getters and setters.
- You want an audit trail that logs the user in the database every time the value is changed
It's a good way to track down issues and keep track of what is setting and getting what.
