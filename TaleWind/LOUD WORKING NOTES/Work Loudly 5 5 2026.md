1. 8:30 AM Participated in my first sprint meeting, talked about how I've been studying the platform and shared my favorite music (nostalgic 2000s documentary music. so refreshing and relaxing)
2. Met with Daryll to update her on my onboarding
3. After the meeting from around 9:15 to 10:30, I Studied Knowledgebase, made notes and explored features
	1. Made extensive notes and explored functionality of the Dashboard, My Account, Users, and Posts
4. Meeting 10:30, Product / AM team catch up. I took more notes during the meetings and learned more about our processes.
	1. Presented an opportunity to learn about our processes
	2. Rig and Alison asked about different items in the meeting document, Mariah and Daryll answered most questions about bugs, Daryll answered questions about upcoming updates.
5. After the meeting, I continued studying the knowledgebase
	1. Ads, Annotations
	2. Ecommerce
	3. Learning Management
	4. Distribution
6. At 11 I scheduled a meeting with Mariah to exchange knowledge about the Jira Spreadsheet and some other things
7. I continued studying the knowledgebase
8. at 11:30 I took a break
	1. cooked some button mushrooms with lemon juice
9. at 11:45 I continued studying the site
	1. Distribution, channel, tags, podcast feeds, and embed management
	2. Analytics modules and reports.
	3. Alerts module, Settings module
	4. Completed site overview
10. 12:30 PM I took my lunch break.
11. 1PM I studied the Jira Update sheet before my meeting with Mariah
	1. I reviewed the jira tickets associated with the update sheet to better understand its purpose
12. 1:30 PM - 2:40 PM [[5 5 mariah meeting]]
	1. Reviewed jira update sheet and how it works
	2. Reviewed how website and jira work
	3. Was given a series of video tutorials to view!
13. 2:40 PM Reviewed video series
14. 3:40 PM completed video series
15. 3:45 PM Took my last break
16. 4 PM Started going through all the tickets in the AM / PD Jira Status Updates document (going through them earlier gave me a lot of helpful context for how my work is conducted)
	1. 1432 - read through Mariah's ticket and code to understand her process.
		1. It looks like we are making customers manually include `wb_import_id` despite it being only for us to use, and not the end user.
		2. We also aren't checking for `wb_import_id` when checking for duplicates
		3. "Validate against" is the term
		4. Makes clients use it is unnecessary and causes problems
		5. Suggesting removing it
		6. generating a unique import ID automatically instead of asking them to give one
		7. store the generated id in `wb_import_id`, referred to here as "post meta". I guess that means it's part of the post metadata, which we use for internal tracking.
		8. Ensure no regression in duplicate prevention logic. Regression means when you break things as a result of adding something, or the addition of bugs.
		9. Don't break compatibility for existing orgs that already have this meta key
		10. Imrpove duplicate detection logic to validate against
			1. organization title
			2. internal import id `wb_org_import_id` which is different apparently
		11. Despite my lack of PHP experience, I was able to understand the code!
		12. First, we trimmed to prevent attacks via the form
		13. Then, Mariah proposed a WP_Query to find a duplicate of the post being made
		14. If a duplicate is found then, presumably, the process would cancel
	2. 1430 - read through bug report and understood how tickets become associated to one another
	3. 1433 - read through ticket briefly and ended my day.
17. 5 PM day ended