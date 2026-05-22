
Interaction where your website sends an email:
User clicks literally anything that generates an email to be sent to them
Frontend grabs user's info (session, or from a form) and sends it to the server
Server (backend app) receives the payload,
probably uses a pre-coded HTML template to format an email,
then uses a mailing library (Nodemailer for Node.js, ActionMailer for RoR) to route the msg
- mailing libraries package the email and connect to an email server
	- Traditional SMTP
	- or RESTful web API

#### Email Service Providers (ESPs)
- AWS SES
- Sendgrid
- Mailgun

Instead of sending emails from your own server you send it through them.
They prevent you dealing with getting flagged as a spammer.

#### Asynchronous Queuing
Web apps that sends lots of mail will add to a queue instead of sending instantly.

#### Dummy Mailers
Mailtrap
Mailhog
intercept outgoing messages and display them in a safe local dashboard for debuging.
