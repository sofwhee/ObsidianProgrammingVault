AKA "Wrapper" pattern or "Façade" pattern.

Create a wrapper around external dependencies, so your code depends on the **wrapper** and makes all those different APIs look exactly the same to your application.

Calling Stripe API directly causes problems:
- Tightly **couples code** to Stripe API.
- **Testability:** Don't wanna call Stripe API while we're testing
- **Harder to switch** to paypal / add paypal functionality

![[Pasted image 20250130135833.png]]![[Pasted image 20250130135837.png]]
![[Pasted image 20250130140537.png]]

# Example

```javascript

```