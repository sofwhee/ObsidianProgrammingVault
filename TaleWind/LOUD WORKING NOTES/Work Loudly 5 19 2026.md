Today I am working on the SQL query

- What do I need to find?
	- uhh...
	- looking in notes
	- Dist channels page
	- 5 15 16
	- Page views?
	- Term ID 4885
	- For each of these channels
	- ![[Pasted image 20260519092746.png]]
	- For each post type (video, audio, pdf, podcast, event)
		- get post type within wp posts
	- Within 6 1 2025 - 5-19-2026
- How do I go about it?
	- Get post_date from wp_posts
	- Get post_status "publish" from wp_posts
	- Get ID from wp_posts
	- Relate each post to the channel by 
		- using the wp_term_relationships table's object_id column to match the post ID (this table literally just connects other tables together)
		- use the wp_term_relationships table's term_taxonomy_id to go to the wp_term_taxonomy table and use the term_taxonomy_id there to join in a bunch of wp_terms (the channels with their info) as well
		- joining wp_posts and wp_terms on wp_term_relationships gets you posts associated with the correct channels.

Notes:
- It seems like the taxonomy wb_channels is getting me channels with the right ids?

``` SQL
SELECT wp_term_taxonomy.description, wp_term_taxonomy.term_taxonomy_id, `wp_posts`.`post_type`, COALESCE(COUNT(wp_posts.ID), 0) as published 
FROM `wp_posts`
LEFT JOIN wp_term_relationships ON (wp_posts.ID = wp_term_relationships.object_id)
LEFT JOIN wp_term_taxonomy ON (wp_term_relationships.term_taxonomy_id = wp_term_taxonomy.term_taxonomy_id)
WHERE wp_term_taxonomy.term_taxonomy_id IN (37, 63, 69, 71, 79, 167, 462, 4676, 4885, 4963)
AND wp_posts.post_date BETWEEN '2025-06-01' AND '2026-05-19'
GROUP BY wp_term_taxonomy.description, wp_posts.post_type
```

```SQL
SELECT wp_term_taxonomy.description, wp_term_taxonomy.term_taxonomy_id, `wp_posts`.`post_type`, COALESCE(COUNT(wp_posts.ID), 0) as published 
FROM `wp_term_taxonomy`
LEFT JOIN wp_term_relationships ON (wp_term_taxonomy.term_taxonomy_id = wp_term_relationships.term_taxonomy_id)
LEFT JOIN wp_posts ON (wp_term_relationships.object_id = wp_posts.ID)
WHERE wp_term_taxonomy.term_taxonomy_id IN (37, 63, 69, 71, 79, 167, 462, 4676, 4885, 4963)
AND wp_posts.post_date BETWEEN '2025-06-01' AND '2026-05-19'
GROUP BY wp_term_taxonomy.description, wp_posts.post_type
```

Problem:
- Need 0 count for published column within date range

Marcus Leite Sales and marketing.

easier to find and easier for you to manage, easier for your customers to consume
it's one place, it's one tool
you just gotta learn one thing instead of a bunch of different technologies. 
we sell knowledge
they closely relate to the bureucracy of govt. they have boards and non profits and theres governanfce in that.
lots of talking and meetings and opinions. 
not a lot of action in keeping up with tech and consumer expectations
very inward facing, very structure and consistency oriented. 
they're a little hard to budge away from what they're already doing
pretty conservative about what they have if it's not on fire
a lot of associations have a good portion of their year distracted by their annual conference
association is made up of some level of programming
an annual event...
and then their publication.
associations are very siloed
they're throwing spears at each other and saying "don't touch my stuff!"
so there's 6 websites for each different part of the association or assocatons

- this guy is very anti govt...
- what, exactly, are the problems with the structures
- He's very growth is good oriented. greedy?
- he pointed out that i care about looking as a smarty pants. hmm. intimidated?
- my gut feeling about this guy is mixed.