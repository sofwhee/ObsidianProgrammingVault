
page views from google analystics
They want stats from a certain time range, not all time
we are n longer providing subchannel data?

dist channels page
5 15 16
term id 4885

phpMyAdmin

object_ID is post (called that cause you can tag or categorize other object ids as well)

not all of these are our posts
it can contain other post types

we want to also relate or join to the wp posts table to filter the post type

12:30 tuesday

june 1st 2025 up to today

numb of published posts 
for each post type 
for each channel listed in general ch analytics report

video post 
audio post
pdf
podcast
event webinar post

for each one we have to query those published within range

wp_terms contains actual channels

wp terms contain actual 
term relationship contains which posts are tagged under a channel

post id
term id in term relationship is` term_taxonomny_id`
to get post type its in wp _ posts

to determine parent

use ids of channels one by one and use them in the where clause

They want...
Information within the range of June 1st 2025, to today 5/15/2026

The information they want is...
For each channel listed in the general channels analytics report
- (Use ids of channels one by one and use them in the where clause "to determine parent"?)
For each post type (video, audio, pdf, podcast, event webinar)
	Get post type within wp_posts
Within June 1st 2025 - 5/15/2026
retrieve number of published posts.

requested if possible Tuesday mid-day

![[Pasted image 20260518104257.png]]

![[Screenshot 2026-05-15 153727.png]]

![[Screenshot 2026-05-15 153926.png]]![[Screenshot 2026-05-15 153935.png]]