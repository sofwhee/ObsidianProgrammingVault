Takeaways:
- If I receive an email directly from a client about an issue, I should make sure to inform the team as it won't be automated in that instance.
- I can look through the history of Jira tasks to see how to format my Tickets
- I can look through the history of other documents Mariah has been involved with in order to understand how to create Communications documents.
- Someone named Mark will be in touch with me to give me backend access to something?
- I am expected to contribute to any documentation - like the TaleWind Digital Knowledge Base
- I was given an example of how to do my job:
	- A client informed us that the image carousel on the front page was clipping elements oddly
	- She went into dev tools and recreated the Iphone screen (there is a drop down to recreate device screens at the top)
	- She saw the issue (reproduced it at this point)
	- She looked into the CSS and discovered the problem
	- She made a document to show what she did to fix the problem
	- She put code references in it so it could be easily found in the code
	- The point of the document she made - one that I would also be expected to make - is to address the issue, or offer a workaround to it, and so it can be double checked by teammates
- Another example:
	- She noticed clients were calling in about something that could have been easily addressed if the customer was aware of the features they had available to them.
	- As a result, she informed the customer about this feature (in this case, being able to click on items in the legend to hide/show different trends) ![[Pasted image 20260504111950.png]]
- Another example where I would prepare a release form or other client communication doc:
	- We prepare release forms that inform clients of everything added in new updates
	- We don't expect clients to read it all.
	- If a client's issue is addressed in the form, the tone shouldn't be "you should have read it!"
	- Instead "Sure thing, I can help you." and then "We're here to answer your questions, and we also made a convenient guide you can refer to where you can also find this information if you'd like."
- I can and should explain where the issue was, but not get technical about it unless I know I'm dealing with a tech savvy client.
- I should make sure Daryll is forwarded when I send emails explaining the issue.
- I should research timing out, RSS feeds, hosts rejecting due to timeout, etc.
- Another example:
	- Client made a support request by sending us a document.
	- We replied by editing answers into the doc
- Examples of expectation setting:
	- "Some changes are already scheduled"
	- "We already created tickets in Jira"
- Another Troubleshootin Example:
	- When accessing a link, it said Riverside timed out
	- Timeout is 10 seconds of loading
	- To check for timeout issue, we gave them a static link - wont take 12 seconds to load
	- Client said didnt work
	- So it isn't about the time it takes
	- Probably issue on their end
	- they're timing out when connecting to us
	- ruled out timing issue with static payload
	- since it's not th timing, we guessed specific links that were included in riverside's end
	- if it's not in these links, we throw that error
- Use w3schools tryit editor for reproducing logic
- sometimes we have to use dev tools console to see if errors are being thrown
- data related inquiries
	- We have documentation on Database stuff to guide us.
	- input field that's providing bias but t not working on another platform
	- sometimes they need help with csv improts, reports
	- sometimes you can import content that's a csv file
		- are the columns the right names?
		- is the data format ok?
- We can dev the fix ourselves if we have the fix for it
- Or put it in resources tab of ticket
	- Put in specific fix, provide screenshots of proof it works
- Client specific fixes:
	- To fix CSS: We can go to customize in WordPress (at the top) -> additional CSS
	- Apply change, then publish
	- To check it, delete cache at top, reload, then it will show the change
	- Make sure to check it when signed in and signed out (just reload in incognito)
		- Signed in is instant, but signed out takes a while
- Client Feature Support Requests
	- Discern value for client feature requests before we make an FSR.
	- In those cases we have to softly turn them down.
	- Figuring out the line - it comes from experience and knowledge
	- Spending time with dev team and figuring out the gist
	- Use your own judgment based on understanding our product, and talking to darryl if its close
	- We might propose solutions for it, but not too much work into it if you're 50/50 on value vs work required to implement
- Bug escalation:
	- If there's no workaround and it requires fixing, we escalate
- Jira stuff:
	- There is a jira automation for AM support Filter
	- Am Support Filter - track jira updates for the AM / PD jira status updates spreadsheets
	- That's allison, darryl, and mark. They're all AMs.
	- We update them on all support request tickets they created.
	- The AM support filter helps quickly bring up all the jira tickets.
	- Scheduled - in sprint
	- in progress - ...?
	- backlog - Not scheduled
	- gathering info - ...?
	- blocked - On hold in Jira
- Jira spreadsheet tracker thing
	- I highlight ones I want to talk about during meeting, and remove highlight after meeting
	- Every friday I put new tickets from the FSR board there
	- If you're the one who put the ticket down in the FSR board, there's no need to put it in.
	- It'll just make the meeting take longer.
- IDK if dev is an expectation for me
- Testing IS an expectation for me.
- You can see pull request tickets
	- make sure they're in bitbucket
	- then you can test them yourself by assigning them to yourself
- Record keeping
	- Update tracking google sheets
	- Create deployment checklist
		- Darryl is more fit to give this tutorial
	- Skim through product development drive
		- It has CSV templates, tracking
	- Release notes are written and compiled by Darryl
	- We help out by adding details and ocnfirming things
	- Client comms on release notes are done by either AM or us
	- Client notification doc - I can just update the month to May instead of making a new one
	- Maintenance Mode communication - Darryl spcifies a date and time, or we keep track of it (whatever that means)
- Homework
	- Study knowledge base
	- Study wordpress database 
	- Study bitbucket (later, when i'm comfortable)

every friday i put new tickets from the fsr board here

if you're the one who put the ticket down in the FSR board there's no need to put it in
it'll just make meeting take longer

idk if dev is an expectation for me ,but testing is

you can see pull request tickets, make sure they're in bitbucket, and then you can test them yourself by assigning them toyourself

record keeping is the update tracking google shets
another is creating a deployment checklist
darryl is more fit to give me a tutorial on deployment checklistS

skim through product development drive
CSV templates, tracking

rebecca - dedicated LMS management whatever

JWPlayer is our video and audio player handlers.

Release notes are written and compiled by darryl
we help out by adding details and confirming things
client communication on release notes are done by either AM or us

Client Notification doc - you can just update the month to May so you don't have to recreate another one

either we keep track of it, or daryll specifies a date and time for Maintenance Mode to our clients

suggestion: start by going through knowledge base so you understand everything platform does
Daryll will want me to familiarize with wordpress database too

Bitbucket will be useful to me once i'm more comfortable. It will help me learn the ins and outs of how the code was written.

![[Pasted image 20260504124809.png]]
![[Pasted image 20260504124817.png]]
![[Pasted image 20260504124822.png]]
![[Pasted image 20260504124837.png]]![[Pasted image 20260504124843.png]]
![[Pasted image 20260504124850.png]]![[Pasted image 20260504124911.png]]
![[Pasted image 20260504124916.png]]
![[Pasted image 20260504124927.png]]![[Pasted image 20260504124935.png]]
![[Pasted image 20260504124940.png]]![[Pasted image 20260504125026.png]]
![[Pasted image 20260504125031.png]]