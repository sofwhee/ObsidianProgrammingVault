1. Set up an "identity" in AWS SES Console
2. (The point of this is to prove ownership of address/domain to prevent spam)
	1. AWS Management Console -> Amazon SES Console
	2. Config -> Identities -> Create Identity
	3. Verify email address/domain (domain recommended)
		1. if you chose domain, you gotta add the provided dns records to your domain registrat's settings
3. Account is placed in the SES sandbox by default. (prevent fraud?)
	1. Can only send emails to/from verified email addresses
	2. Strict sending limit
4. To move out of the dashboard...
	1. SES dashboard -> Account Dashboard
	2. Request production access
	3. Fill out the form. Typically approved within 24 hrs.
5. Choose sending method.
6. (Depends on tech stack)
	1. SES API / AWS SDK
	2. SMTP - ideal for migrating from traditional email servers or using Wordpress
		1. SMTP settings in SES console and Create SMTP Credentials.
		2. Use generated username pass and smtp endpoint in your app's email settings
7. Monitor bounces, complaints, deliveries (you can use CloudWatch or SNS)
8. You can also set up a custom MAIL FROM domain using your own DNS MX TXT

## Wordpress set up

1. Sign up with AWS, verify identity via domain or email address
2. Request production access
3. You need credentials to allow Wordpress to securely talk to AWS.
	1. API Keys
		1. Create IAM user with programmatic access
		2. attach `AmazonSESFullAccess` and `AmazonSNSFullAccess` policies to obtain an **Access Key ID** and **Secret Access Key**
	2. SMTP Credentials
		1. SMTP settings in SES console and click **Create my SMTP Credentials** to generate specialized username and password
4. Install a plugin to bridge WP and SES
	1. WP Mail SMTP
	2. FluentSMTP
	3. WP Offload SES Lite
	4. YaySMTP
5. Test it with Send Test Email within plugin's settings.