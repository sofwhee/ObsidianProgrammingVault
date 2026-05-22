[Standard Workflow Guide](https://hexdevelopment.workerbee.tv/?post_type=docs&p=7753)
# Client Technical Support Handling

My duties, from initial contact to resolution.
### Temporary Onboarding process:

- Mariah will communicate that we are transitioning to a new member, me!
- Daryll and I will be taking over
- I will be responding when it's straightforward, but Daryll handles more complex cases.
	- 35% of customers communicate directly to us instead of using tickets
	- Most are replying to release notes email thread
		- We don't normally do an email blast with release notes... so idk why that's happenin

### Support Request Process

- Acknowledge
	- Within time window
	- Confirm receipt of request
	- Outline planned next steps
	- If ownership between me and AM is unclear, I take it by default
- Investigate (properly)
	- Identify key details
		- Affected platform
		- Feature
		- Specific Content / Assets referenced
	- Ask clarifying questions
		- Steps already taken
		- Screenshots or recordings
		- Exact timestamps
		- Browser or device details
		- The environment (Production, Staging, etc)
	- Attempt to reproduce in comparable environment
		- Log in to access content:
			- Admin log in
		- Chrome Dev Tools
		- [Demo TaleWind Site](demo.talewinddigital.com)
		- [Hex Dev Site](https://hexdevelopment.workerbee.tv/)
		- [W3schools Tryit Editor](https://www.w3schools.com/tryit/)
	- Check known issues
		- [Jira Codebusters Board](https://workerbee-dev-team.atlassian.net/jira/software/projects/CB/boards/1)
	- Check app logs
		- Dev tools (Inspect)
			- Console - errors and warnings
			- Network - failed API requests (404, 500)
			- Network - filter - collect - refresh or action
		- Google analytics?
			- Reports -> Realtime
			- Event count by Event name card to see which actions (click, page views etc) are logged
			- Click on a specific event to see parameters being sent with that log entry
		- Google Analytics Debugger chrome extension
			- prints detailed tracking info into browser console)
		- DebugView in Google Analytics (admin -> data display -> debugview)
	- Check current system status
	- Rule out user error or misconfiguration
		- Need more details here?
- Resolve / Escalate (Correctly decide)
	- Know the boundaries between what I can fix, and what must be sent to the dev team.
		- Summary: 
			- We prioritize Support Clients before development.
			- Mariah doesn't know if I'm expected to help with development.
			- You can work on a bug proportionally to the amount of free time you have
			- Don't worry about contributing to the codebusters board too much, it's just something to do when you have free time (according to Mariah)
			- If you have downtime: First help with documentation, then testing, and then codebusters board development, creating mockups of feature requests.
		- More details:
			- How long can I take on fixing one task?
				- Varied based on her bandwidth for support that day
				- See how much we need to resolve before diving into development
				- If my workload is small, i can take as much time as i need
			- personally, if you look at prev codebuster sprints, i dont just do bugs i do stories too
	- Confirmed bug
		- Reproducible and not the result of user error or misconfiguration.
	- Feature limitation or gap
		- Client request falls outside current platform capabilities
	- Performance or System level issue
		- Symptoms relate to latency, downtime, or infrastructure
	- No viable workaround
		- Unresolvable through config or other support level intervention
- Communicate (to client, account manager and the dev team)
	- Create / log ticket if directly contacted by client
	- Avoid open-ended language
		- every substantive client response must include
		- realistic timelines
		- the next concrete step
		- an explicit indication of whether further investigation is required
		- Commitment to a specific follow-up date or milestone
	- Keep the AM cc'd on client responses
	- If it becomes deeply technical and not useful for AM, move to a separate thread and summarize outcomes back to the AM
	- The Technical / AM Sync Up group on Gmail should be used for those recap communications

### Inbound client communications that are my responsibility.

- "How to" questions
	- Platform feature guidance
	- Supported workflows
	- Best practices for media ingest, publishing, and distribution
- Configuration support
	- Assistance with system settings
	- integrations
	- connection of third party tools
	- account level configuration
	- onboarding adjustments
- Suspected bugs
	- reproducing reported issues
	- gathering relevant logs
	- determine if behaviour deviates from expected platform functionality
- Data verification
	- outputs (?)
		- error messages
		- structured data
		- secure HTML that prevents cross-site scripting attacks
		- input santiziation and validation
		- output encoding to prevent XSS
		- validation messages ("invalid email format")
		- Data integrity checks (data remains consistent from submission to storage)
	- reports (?)
		- validate data integrity during migrations or integrations
		- data type checks (number vs text)
		- format verification (YYYY-MM-DD)
		- consistency checks (eg end date is after start date)
		- Range validation (within min/max values)
		- Uniqueness checks (prevent duplicate records, user ids or email adresses for example)
	- CSV imports (?)
		- validate user data before it hits the database
		- `Papa Parse` (frontend)
		- `CSV-parse` (backend)
		- Zod (schema validation)
		- Schema validation (define required columns and data types, like date formats)
		- prevent bad data ingestion
		- send validated JSON data to a secure endpoint, like CSV box (backend Webhook)
		- ensure CSV encoded in UTF-8 to prevent data corruption during parsing
		- Test with `csv:check-import` to evaluate data complexity, run unit tests on parsers
	- expected system payloads (payload mismatch?)
		- Validate JSON schemas
		- correct the data types
		- ensure raw data is used for signature verification
		- etc
	- reconciliation of metadata and content delivery records
- Minor fixes
	- client-specific quick development involvement
	- targeted data adjustments
	- CSS manipulation

### Communication methods I will be utilizing.

- Email
- Jira (Feature Support request AKA FSR) board
- CB sprint board

## Escalation Process

- Log and categorize in Jira
	- Bug - confirmed unintended behaviour
	- Support Request - further internal investigation required
	- Feature Request - product limitation, not defect
	- (I can look through the history of Jira tasks to see how to format my Tickets)
- Document thoroughly
	- clear summary
	- step by step reproduction instructions
	- screenshots or screen recordings to show issue
	- relevant logs / error messages
	- timestamps and environment details (platform, browser, device, region)
	- client imapct description - how many users or workflows affected
- Define severity and priority
	- use ref table in section 8
	- reflect operational impact on client, not perceived complexity
- Route to appropriate team
	- Assign bugs to dev colleagues within Product Development Team via the CB sprint board
	- Route Feature Requests to product colleagues within the Product Development Team for backlog prioritizations
	- Keep Support Requests on the FSR board, owned by the technical support specialist, unless further escalation becomes necessary
- Communicate clearly with the client
	- inform that the issue has been raised interanlly
	- what is being investigated
	- current status of ticket
	- expected timeline, aligned with application SLA where one exists
- Maintain Ownership
	- Remain point of contact
	- Monitor Jira ticket progress at regular cadence
	- Follow up internally with assigned dev or team as needed
	- Provide consistent updates to the client and keep AM informed of material changes

### Priority and Response Times

![[Pasted image 20260501184343.png]]

### Documentation

- So that any team member can pick up an issue without loss of context
- On Jira Ticket
	- All client interactions
	- All investigation steps
	- Email threads linked or summarized
	- Resolution notes on closure for future reference and trend analysis

### Review and Maintenance

- Standard Of Procedure is owned by me
- Reviewed annually
- Or sooner if material changes occur to
	- supported platforms
	- jira workflow
	- or escalation model
- suggested amendments raised with document owner