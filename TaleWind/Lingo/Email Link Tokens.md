Email link tokens
- Unique, secure strings
	- Impossible to guess
	- Uses [[UUIDs (or Globally UID)]] or high-entropy strings
	- Prevents unauthorized access to sensitive links like unsubs or account access
- Appended to URLs in emails
- Identify users (token embeds user-specific parameters (ie User ID))
	- track engagement
	- auto filling forms
	- Allows for unique URLs in mass emails
	- personalized unsub links
- Magic Links (Provide instant auth without passwords)
	- temporary, secure credentials
	- Removes need for password-based logins
	- user click -> Server verifies the token to authenticate them

- Used for logins, password resets, personalized unsub links
