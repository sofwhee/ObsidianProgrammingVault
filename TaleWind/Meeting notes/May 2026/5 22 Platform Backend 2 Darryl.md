bitbucket
- it's all in php
- need at least 2 approvals on a pull request before merge can be done
	- look up pull request etiquette etc
Dashboard review
- vtt holds video chapter info, thumbnails for chapters, positino on timeline etc
- We only show thumbnail for restricted users
- Access for post gating
	- We can paste marketing form embed code in there and it sometimes works, but we've only used it with a couple clients so it's uncertain how functional this box is.
- Make private
	- really only for MHI
	- adds a true value to certain field in API, which MHI uses
	- Shouldn't be available to everyone else
- Product ID
	- rarely used, just an additional field, a holder or something
	- It can be used to link two records in the database
	- Can be used for integration (AUTM)
		- wanted our system to forward a record to their system

Recommends I go through audio to see the fields that aren't in other post types.

LMS
- Same as posts but diff structure and fields
- Banner ads have a heirarchy based on specificity

## Google Search Console
We use this email for google analytics and google search console: workerbeetv@gmail.com

Darryl:
When you are setting up / registering a site for gogle search
I usually choose URL prefix instead of domain. You could use either.
Domain provides file for you to download and add to site directory.
Just a basic HTML or text file sometimes.
URL prefix is verified by email - i think.

Once domain registered, the next step is submit sitemap

## Sitemap
sitemap.xml

to set up that sitemap.xml we set up a plugin in site. (sic)

wp admin -> plugins - 

(when you see these updates, I was tempted to click and do the update - but i was reminded i should never do that until the update cycle. every update has to be tested first. These days it's almost always compatible but now we do updates along with release cycle because clicking an update takes a while and it can cause downtime.)

XM Sitemap Generator for Google - settings - click a thing and it generates the xml sitemap

usually takes up to 4 hours to submit the sitemap.

the crawling or indexing takes up to a week or more.

it takes a while for a client platform to become available in google search. it takes a while.

Index

You can look at the index and find out why pages aren't indexed.

server error means issue with our platform, same as 4xx issue.
403 is *not* good. that's our issue.
That's because this is the record of blocked access for the bots. 

We used to not want AI to crawl our sites.
Now we want AI to crawl our sites.

## Bing Webmaster
Same as google search thing but for Microsoft.

Going into server to troubleshoot verification for bing...
sign into server directories
clusiter 2 we use SSH key isntead of password
home/ubuntu/efs/ondemand.tapp.org/
BingSiteAuth.xml is in here...

left side of window is pc right side is server

anyway bing webmaster is similar to google search console.

## OEDSP Light house Cove

We are setting up an LMS with them.
Seperate from the old one.
Once we have the new one set  up we will terminate the old.
Using same domain for new one as old one.
currently this is empty: [new lms](https://newlearning.lms.professionaltrainingmatters.org/)

Want me to take a stab on this.

Want me to get my hands on setting up a site.
Install wordpress.
Then set up database.

empty database is there
wordpress installation documentation here: https://developer.wordpress.org/advanced-administration/before-install/howto-install/

Darryl will send me log ins, documentation, etc.

download and extract and then upload.
Once it's up, you wil have to access the URL I sent you. Once you acess that it will prompt you to set up database, that's in the instructions as well.

db name, password, wp config, etc will be sent by darryl.
Once I'm able to set up WP we can set up plugins, third party plugins, teams, then configs for each plugins.

Well here's what I determined.

1. downloaded `wp-config.php`
2. Since we have an empty database at https://newlearning.lms.professionaltrainingmatters.org/  I'm assuming that means we don't have to create a new one, right? 
3. Does that also mean, then, that we already have a user set up in phpMyAdmin and I don't need to create one in phpMyAdmin and give it privileges?
4. For uploading files, I assume I would need the username and pass and so on for my FTP.
5. Since our platforms exists in a subdomain, what directory should I be installing WordPress?