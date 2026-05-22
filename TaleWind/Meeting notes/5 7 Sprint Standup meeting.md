
Estimation:

![[Pasted image 20260507084243.png]]

quesitons:
- ~~what does the number mean in story point estimate?~~[[What is a Sprint]]
- how are priority levels decided?
- How do we determine the "risk level" of a feature, and reward level?
- What is CB 3176 about?
- Should I look into updating Jira so we can make it an urgent ticket?
- ~~What is SPE~~(Society of Petroleum Engineers) and [[Marketo]], and why is them previously using Marketto making the ticket their concern?
They decided to exclude the Playlive video upload (exclude - multiple media ID)
- Zoom can also accomodate this

"email capture gating" - valuable content is hidden behind a email address submission form for users to gain access
adding "marketing and mail gating" to "post gating" field
"SPE concern because prev they're using marketo"
"looks like for tasks we cannot spcify if this jira ticket is an urgetn ticket"

###### CB3176 - An improvement to discussion board - 

we are using a link to a script. high risk low reward? No client is using it. Not a big request right now. Maybe we can combine it into a single task to review. This was devd by on of our prev devs before. If we agree we can let Alison and Daryll know about this before we proceed with this request. (team agrees) last update i did was to remove a few dependency files linked to our server. This shows that it's not 100% tested and this feature is a very big risk.  

###### Video Post Layout - use enhanced post layout
- What does enhanced video post layout do?
	- if it's unchecked, something something old design
	- (testing...)
	- It looks like unchecking it switches it back to the old design!
- So in addition to the site wide setting, we'll be adding another setting the post level
	- add a checkbox or toggle on video host page
	- same logic with this one
	- when enabled, title and desc should appear above video (so like this toggle)
	- but by default it should be video above
###### Update UI of trending pages (most pop, most revent, rfeatures)
- This needs to be a script, right? (yeah, each page)
- I need to split this ticket
- So the look right now is the old one
	- (hexdev didn't work for testing, so they pulled up demo.talewinddigital.com! interesting)
	- yeah like this, surrounded
- Okay I'm splitting this into 3
- team voted 2
##### Most Popular Channel - Add search and enhance sorting and filtering
- note : they're using the images to go through and understand the request...
- note : they're playin around with the website etc to figure out what's being requested and the problem at hand to estimate the work
- Learned: I need to be structuring codebuster tickets to make it easy to estimate what work needs to be done and how complicated it will be
- Do we think this should be blocked by the previous ticket?
	- "yeah..."
- This is not possible for the special pages, right? (yeah..)
- What happens when we search? (tried test video)
	- So it only searches under that channel
	- So the search will only search from the list given
- "I feel that we are missing something here in the requirements...."
- any questions?
	- are we searching for the... for all codes... i think searching for most popular is a normal search... it's just sorted by default to most popular
- right, so that's another qustion but...
	- In here, in our demo, the result...
- it only searches within the result of most popular here (instead of everything? idk)
- We can use the entire search and just arrange it by popularity
	- (adds " Use the default seach and rank the results based on popularity (New)" )
- The question is do we really need to apply this or not?
	- Mark: So no sorting, just search. (why? I didn't understand)
- how about the filters?
	- if what we are after here is to have a standard page, that defeats the purpose of those specific pages, right?
- (the ticket wasn't clear and led to a lot of confusion because the customer's goal isn't clear, or has already been achieved by the existing design of the website. Implementing the change would be redundant or conflicting with design)
- Why are you going to sort this if you are looking for the most recent, right?
	- Maybe there needs to be a search here...
	- Same goes with featured content. Yeah we can just go on search on this one. I think sorting is applicable
	- "yeah, featured post is a category"
	- Yeah we can apply the search, like this one *goes to demo site to explore ways to monetize your content*
- What do we think team. Is this possible for this "featured"?
	- "yeah"
- But this one has its own template, correct
- Yeah, I think the filters are applicable here (goes to ticket CB-3854)
	- yeah, it can be sorted and filtered,  we can put it here in sub-categories, and then these are the custom filters
- Okay, I think we can estimate this one right?
	- 2, 3

### 4096 estimate - 1, 2
- introduce a filter in the posts table to allow users to filter posts by status, included new Expired status

### CB 4101 - append "-spotlight" to wb_carousel_slide post_name slug to prevent conflicts
- I think this is to prevent duplicate slugs
- we append spotlight to slug, so its unique to that post type
- I think i get it now, these aren't posts
- it's in the admin dasboard
- yeah, alright. ok i noticed now, thanks.
- so for add coursel slide "create new coursel slide"
	- this one you can leave it as this...
	- so if we make a new carousel...
	- "yeah there's no permalink validation there"
	- yeah so we just add "-spotlight"
	- but this will not 100% cure the issue. it will not address it. what do you think?
	- "yeah maybe we should also add a validation just like when we're creating media posts. the permalink validation"
	- yeah, cause what if i create a new one...
	- How do we decide the title on this one, gigi
	- what if we did make another carousel
	- "the second one would have -1 and then -spotlight"
	- the only problem here is that it conflicts with other post types
	- tat would mean ... -1, -2, and then -spotlight... but im okay with that

CB 4106
- I think it's missing URL parameter
- don't know complexity on this one, so its a bug

## Takeaways:
- write tickets to support this estimation process
	- 
- Review tickets mentioned here to learn what they were talking about, and intuit how they made their estimates, and develop an intuition for how to write tickets so they don't have to do as much investigation to figure out the estimates (they went over time on some tickets that were confusing, note what went wrong there)
- learn about slugs and stuff 

## answers:
- number mean
- ![[Pasted image 20260507084418.png]]
- what is slug generation for? and how are permalinks related?