I made these step-by-step instructions in July last year, but I know things have changed a bit in the LMS.

- Learner Management [HERE](https://drive.google.com/file/d/1EXaUb97CGTK9vCCvrFAp1P9Vvw-lAYEk/view?usp=drive_link)
- Learning Content [HERE](https://drive.google.com/file/d/1ZUCuO3jxK9ijn4qTGO6t5oQE0Kgg_cNu/view?usp=drive_link)
- Org Admin [HERE](https://docs.google.com/document/d/1FhsQLTzOmXE7iNeB55Nvktccw4VJgkPAOCF9Kcxinzs/edit?usp=sharing)

Summary
- Read through existing documentation.
- Learn the current process.
- Create new documentation by editing the current one.
- Use it as a script.
- Go through the process myself as a test run, taking notes of what to edit.
- Record myself going through the process and explaining what I'm doing.

Notes:
[Learner Management](https://drive.google.com/file/d/1EXaUb97CGTK9vCCvrFAp1P9Vvw-lAYEk/view)
- Specific mentions to AICC. I suppose this is just for them? **Should I make it more general?**
- Broken link on "using your credential (sic) from [here](https://www.aiccbox.org/login.aspx)" https://www.aiccbox.org/login.aspx so this is their login. ~~Why can't I access it? Did it move somewhere else?~~ Found it, this is their new domain: https://now.aiccbox.org/login/
- I made it as far as step 2, "from the org admin dashboard, select learning management." It is not present in their dashboard. Is this because they haven't set it up yet? Should it be visible for me? Do I need to go to the dev site? I'll try going to our hexdev site.
- Hexdev site seems to be set up for some kind of ASQTV testing and when I click on my user to access the dashboard, I get "access denied."
- Moved to LMS demo site.
- Was able to make it past step 2 this time.
- Step 3 - Organization Learners doesn't appear on the top level. We need to add a step here that says to click "Organization" first, then "All Organization Learners."
- Step 6 - Search for your learner's Organization and click on it
- If you want to add more learners, click the "Add Another Learner" button.
- Step 7 - To add your learner(s), click the "Add Learner" button.
- To Bulk Import Learners, go to Learning Management -> Organizations -> All Organization Learners -> Import Learners
- Here, you can download our template CSV to make sure your CSV file is formatted correctly for uploading.
- Upload your CSV file that follows the format provided in the template CSV.
- A green box here will tell you how many successful imports were completed.
- ![[Pasted image 20260526095706.png]]

Note: Checkbox to mass delete learners would be very helpful
Ask darryl: "If a client uploads a CSV with unaligned data, let's say the organization ID is off by one on all emails they are importing, and they have a ton of new Learners created with the wrong organization IDs... do they have a way to mass delete learners? Like with a checkbox? Is this something we're working on?"

In All Organization Learners, clicking "manage" takes you to the learner's courses instead of managing the learner itself. It might be a good idea to change "manage" here to "manage courses." and then add an additional button to "manage learner"

If you click "add a new learner" from the All Organization Learners page, it prompts you to add a learner email and a learner organization. However, all the other fields you would normally find when you add a learner in the "Learners" section of the dashboard are not available. This results in creating a user that only has an email and organization attached, but without a name. It also results in "There's been an eror while updating the user profile. Please report to the administrator."

Assign Content to a Learner
- "Colleges"? Do they mean Pathways?
- "Search and select the learner" You can't really "select" a learner. I think what they mean is to click the "manage" button.
- "Click view next to the learner's name" This isn't present anymore. I think they mean "manage" now.
	- The tutorial mentions how you can view the learner's details this way. I think that would be much more intuitive than a vague "manage". Manage what? The learner? No, the courses of the learner. It doesn't really make intuitive sense.
	- In addition, once you are in the manage step, there's no indicator anywhere detailing *which* user you are managing. That can be disorienting.
- Select what kind of material you want to assign to the user.
- Search for its title using the search bar.
	- Only being able to use a search without having a table to scroll through might be a bit user-unfriendly.
	- Interestingly, when I used the search term "test", nothing appeared. However, when I went to the Courses and Pathways tables from our dashboard, there were MANY courses with "test" in their titles. I think the search function might not work.
	- However, when I input nothing it does give me the JSM pathway 2 courses. Is this because the learner I created doesn't have access to the other courses?
	- Perhaps a better way to make this clear would be to show the courses but gray them out with something that says "Premium content".
	- Or maybe having the learner's manage page tell you what level of access it has. Or even the Assign Contents page.

[AICC - LMS - User Guides (Org Admin)](https://docs.google.com/document/d/1FhsQLTzOmXE7iNeB55Nvktccw4VJgkPAOCF9Kcxinzs/edit?tab=t.0#heading=h.juv4gls3ynf0)
- More updated than the previous one.
- Step 1 and 2 - Ask AICC to create an Org Admin and a Company in Packaging University
	- Do I need to demonstrate this in the tutorial?
- Log in as the org admin after being assigned to an organization
	- https://learning.aiccbox.org/login/
- "Rebecca can help us create the necessary Org Admin accounts" - not sure how to tutorialize this. I don't know what the process is for assigning someone to an organization. Should I just say "Contact your account manager if you need an Org Admin Account."?
- "Navigate to the course catalogue on the frontend"
	- It's not immediately clear how to do this looking at the front page. There is no course catalogue, it all seems to be broken up in "browse channels"
	- Clicked the drop down for Webinars. It is also a redirect link which pulls me to the top. Kind of annoying...
	- AICC University > Overview of Learning for Each College  table is messed up...
	- I was on the wrong page. I had to click "AICC University".
	- It says to go to the frontend, but I don't think that's quite right. It should probably say "navigate to Learning Management -> Organizations"
	- I tried going to the development version of the site, but it looks outdated. 
		- I don't think I can use it to create a guide, or to test things.
	- Ask Darryl how they want me to go about creating a test organization for demonstration purposes on AICC's website,0 since the tutorial we have is using their client-facing side.

The older doc and the more recently modified document seemingly teach the same thing and are titled similarly, but give different instructions.

Some of the problems in my way
- Step 1 and 2 - Ask AICC to create an Org Admin and a Company in Packaging University
	- Do I need to demonstrate this in the tutorial?
- Dev site seems different than production site
	- Instead of 
	- Is this because it is outdated, or because I have less privileges
- Log in as the org admin after being assigned to an organization
	- Should I create an org admin account in order to test this?

---

Add a new learner.
1. Ask AICC to create an Organization Administrator account and a Company in Packaging University.
2. Log in to your Organization Administrator account.
3. Click on "My Account" from the top hyperlinks.
4. From the Organization Administrator dashboard, select Learning Management.
5. Under the Learning Management dropdown, select Organization Learners.
6. Click "Add a New Learner."
7. Fill out the Learner's email and Organization.
	1. (Note that the Organization Learner must have SSO AICC Credentials.)

Import a list of learners.
0. Click on your user icon, and then click on "dashboard."
1. From the Organization admin dashboard, select Learning Management.
2. Under the Learning Management dropdown, select Organization Learners
3. Select the "Import Learners" button on the Organization Learners page.
4. Upload the csv file.

Assign Content to a Learner
1. From the Organization admin dashboard, select Learning Management.


---
Daryll Meeting

Org Adm have their own companies

Several member companies

Those orgs have a primary manager

They assing courses to members like new staff getting onboarded

The org as a superadmin or an admin you can see all orgs

Orgs need an admin attached

(so it looks like org admins really do use the normal platform we use in hex dev for example)

Use Workerbee TV org in order to do demonstrations.

Courses that org has already purchased to be assigned to learners

Manage Administratos, that's managing org admins.

As org admin... Click on Myaccount for backend. Only thing available is learning management. Use this for demo.

So for the demo, make sure I'm logged in as an org admin.

 what is the log in for the org admin WorkerBee TV.

Assign content to learners:

Manage content on a course under learning content in dashboard. for org admin.

Invite a new learner doesn't have a name input, so it has some issues. (should i tell them not to use this?) log in as AICC (SSO) non member log in (no SSO?) If the learner already has an AICC account and they log in, their name will be filled in automatically.

Don't use single add a new learner, recommend import instead.

Import learner doesn't take name

Summary:
Do the demo by signing in as an org admin in AICC backend. (WorkerBee TV)
- Can I get this login info?
- Daryll will add me 
- if you have not yet been added, contact the site administrator?

There are some problems with adding learners (no name input box)

Learner status will only show up once they start consuming content.

If you don't see "add course to account" check that you have not already added itto your account.

in AICC they don't assign any prices to theri courses.

