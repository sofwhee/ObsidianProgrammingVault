Authentication
- User is who they say they are
- sign in form
- keep track of user during session until user logs out

Tips:
- NEVER roll your own auth system
- There are already well tested solutions (Devise)
- Don't store passwords plain text
- Store encrypted "password digest" version
- Compare new digests to existing digests
- If match, logged in user

--- HTTP Basic ---
- casual, insecure
- submit user + pass to form
- send unencrypted across network
- restrict access to certain controllers
- http_basic_authenticate_with (does the former)

--- HTTP Digest ---
- slightly more secure
- before_action runs method which calls
- authenticate_or_request_with_http_digest
- takes block that should return correct pass

--- Rails (session) ---
- has_secure_password
- User model (make it accept password + password_confirmatin attributes)
- has_secure_password intercepts values and converts to digest
- new user: sessions_controller.rb (:new :create :destroy)
- if user correct credentials (check using #authenticate)
- session = <id>
- use session var to validate

--- Rails (rememeber) ---
- Add password_digest column in Users table (name it whatever)
- User sign in -> convert submitted pass into digest
- add has_secure_password to User model
- use it to store digest in User's password_digest column

- Add validations for password + password conf length

- + sessions controller and its routes
- #authenticate method to sign in user
- (when sign in form submitted with proper credentials)


- Remember user with remember_token column in Users table
- Save that remember_token as a permanent cookie in browser
- Reset on each new sign in

- To check if User is already signed in..
- On page loads that require authentication...
- (using before_action in relevant controllers...)
- Compare browser's remember_token to User's remember_token
- if mismatch, redirect to sign in

- Make helper methods for repeated things

