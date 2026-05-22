
Internal

Google Workspace - Gmail, G Drive, etc
Microsoft Office 365
Hubspot (sales and marketing)
Adobe Creative Cloud and Acrobat
Zoom
HIVE Portal (revisions in progress)
HIVE Knowledge Base (Revisions in progress)

Servers and Load balancing

AWS
- EC2
	- Shared
	- Autoscaled servers (4 clusters) (min 3 instances, or "3 mini servers")
	- Load balancer available to multiple zones
- CDN
	- S3 - durable, secure cloud data storage
	- CloudFront - backend of Cloudfront is S3
		- Availability is way higher
		- Cloudfront server from new zealand will serve your media
- SES
	- Our mailer. (A cloud based email service provider.)
- EFS
	- Elastic File System. Serverless, fully managed network file system.
- Route53
	- DNS Server (Domain Name System)
	- Specialized computer that acts as the phone book for the internet.
	- Why we have one: Intranet? Security. Reduces Dependence on ISP reliability. Split-horizon DNS shows different IP address to users in the company compared to internet users. Prevents information leaks as ISPs can't track company browsing activity.

Data Storage and Querying
- I thought we were using S3?...
- MySQL
- (these two are basically just MySQL but premium)
- "Someone decided to repackage the free MySQL and sell it to people" - Mark
- MariaDB
- Auroria

Framework tools
- Bootstrap
	- Free
	- Open source
	- Front end (collection of pre-written CSS and JS code)
	- Build websites quickly using ready-made components
	- To use it, link Boostrap's files to your html...
	- Assign specific classes to elements... (`class="btn btn-primary"`)
	- Instantly applies a pro design, hover effects, consistent spacing
	- Built in javascript plugins. Dropdowns, tooltips, carousels.
- jQuery
	- JS Library (functions and classes)
	- Open source
	- Simplifies web
	- dev
	- Wraps complex JS functions into easy to use methods.
	- Vast plugin ecosystem.
	- DOM manipulation, event handling, AJAX, animations, effects
	- automatically handles inconsistencies and bugs between diff web browsers. 
- Angular
	- Google
	- Open source
	- TypeScript based front-end web app
	- Used for Single Page Applications
	- Used for Enterprise web interfaces using components
	- Gives a consistent experience and a standard structure because it's opinionated.
	- Instead of multiple third party libraries, you get one consistent framework
	- Compared to React, includes tools for routing, state management, form validation, http requests.
- Introducing a new product similar to Angular soon

Monitoring / Performance

AWS
- CPU utilization
- Network
- Status Check failed
- Disk operations
Pingdom
- Speed and uptime monitoring
- Constantly tests your websites, servers, web apps
- If something comes up, it will tell you instantly.
Uptime Monitor
- Backup uptime monitoring
- We have a backup i guess.
MySQL monitoring tool
- Read and write monitoring (queries)
- Has status variables like `Com_select` to track number of `SELECT` queries executed
- An agent (like an exporter mysqld_exporter) logs into MySQL as a read-only user, and queries status variables regularly.

Business intelligence solutions
- Microsoft Power Bl
	- Connects many often unrelated data sources together into readable metrics.
- Association Analytics
	- Cloud based business intelligence platform
	- designed for pro associations and non-profits

Behavioural and product analytics
- Google analytics
- We do have internal logs but we don't tell our clients
- We might be monitoring things they don't want us to
- It's just for us

Working with other Teams
