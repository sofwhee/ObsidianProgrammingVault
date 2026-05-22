It is considered best practice to modify email links to provide stronger authentication context via a session.

- When the user [[Requesting an Email|requests an email]] on their laptop
	- (this just means they triggered an email to be sent to them)
- Store a `session_id` or `device_id` in your server's backend (eg Redis)
- When the user clicks the email link
- Server verifies if incoming click holds a cookie for that same `session_id`
- If unmatched, auth fails
	- this prevents user from requesting a link on phone but clicking it on a public pc