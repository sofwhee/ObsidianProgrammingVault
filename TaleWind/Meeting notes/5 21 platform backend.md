ASQ sandbox
- THey want a staging site
- looking to migrate from their diff portals
	- magazine
	- podacast
	- spread out in diff platforms
	- want to consolidate
- Old site no LMS setup
	- want to migrate lms course content to their platform
	- we have already set up lms on top
	- when lms is enabled bny default the feature for the events calnedar and leaderboard is also enabled
	- our dev site has lms enabled,
	-  so we have events calendar and leaderboard on the trneding section now
	- They requested we disabled events calnendar and leaderboard
		- want me to handle this one cause it's easy
		- go to wp admin - LMS setings (our custom plugin, found in wp plugins tab, named WBTV LMS. naming is not consistent because lots of diff dev worked on it over the years)
		- We have enable checkbox in the calendar tab
		- So we just check front end to make sure it's actually disabled
		- if you log in you get redirected to front end or dashboard
		- the wp top bar is only aavilable with wordpress admins
	- Sometimes clients wants content to be called something that's not in our post types
		- we can just rename an existing post type's label in the wp admin side

Documentation of WP plugins

Set up Out Of Office responder

Audience roles - gating access
User Groups - mainly for backend. Creator groups.

make graphic

admin, superadmin
manage everything on dashboard
difference is  super admin can add other admins
"superadmin gets admin management privileges"

editor
universal post management

author can't access posts from other authors

contributor?

subscriber front end user

lms learner, end user with lms access

lms instructor, 
doesn't have dashboard abilities atm,
used to indicate who arranged the learning material even if they didn't upload it themselves

can also be a learner

reg subscriber

clients ask to add superadmin and admin
clients can't add a superadmin, so we do it in the backend of wordpress
wp admin -> user -> add user

adding user sends an email notification automatically

to access the client's dashboard, it would be `"videos.___.com/org"`
Our subdomain is "videos.whatever" or "screening.spe.org"
refer to the [plugin tracking spreadsheet](https://docs.google.com/spreadsheets/d/1FJGvBx1mbB8KtJs-_crv1We4xrPLaHtskK8_-gckGXY/edit?gid=0#gid=0)

clients they could be using any SSO
So we go to WB SSO settings in wp admin side to manage their SSO
we make an SSO Type for each client hat has its own SSO
SSO Type - only applicable to the site it's related to
make sure SSO is enabled when required

We try to make reusable SSO types, but... it's tough
They always always have different configurations

Usually we have SSO client IDs and client Secrets here, but not here for some reason

we start the develeopment on the client side
we mostly always do SSO before the site is launched, so we do it without the staging site
If the client wants a new SSO it's tricky because we can only test on the live site.
(Is there a way to test without it being live?)

our system auto makes records for their logins
we receive tokens when they successfully sign in they get redirected with the token or important info, we use an api to collect that, they have endpoints for us to determine where we get those information, once they log in for the first time we save those informations, we save first name last name and email address
sometimes client requires for our integration to determine membnership type it would have that information in the api
we can get that info from the api
we would also save that in our database for our records

but as for editing... (i should not be able to see the edit part of it)

![[Pasted image 20260521104824.png]]
![[Pasted image 20260521104820.png]]

there are certain things we can edit, but not the core information.

