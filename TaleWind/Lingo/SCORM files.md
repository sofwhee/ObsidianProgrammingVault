Zip files that get uploaded and give LMS content all packaged together as html js etc. 

Accessible via Admin Dashboard -> Analytics -> Learning Analytics -> SCORM chapters

- Our SCORM chapters are saved as WP posts in our database ( `wp_posts_table` )
- with custom post type `wb_lms_chapter`.
- Related info to the posts are saved as `sp_postmeta` just like other post types.


Previously we would just run this query, and export the data to CSV  

```SQL
SELECT m2.post_id AS chapter_id, p2.post_title AS chapter_title, p2.post_date AS chapter_post_date, [p.ID](http://p.ID) AS course_id, p.post_title as course_title, p.post_status AS course_status, p.post_date AS course_post_date  
FROM wp_postmeta m LEFT JOIN wp_postmeta m2 ON m.post_id = m2.post_id AND m2.meta_key = 'wb_course_id'  
LEFT JOIN wp_posts p2 ON m.post_id = [p2.ID](http://p2.ID)  
LEFT JOIN wp_posts p ON m2.meta_value = [p.ID](http://p.ID)  
WHERE m.meta_key = 'wb_chapter_type' AND m.meta_value = 'scorm'  
AND m2.post_id IS NOT NULL AND [p.ID](http://p.ID) IS NOT NULL  
ORDER by p.post_date DESC, m.post_id ASC
```

- We have two tables here : `m` and `m2`
	- `m` - the source table it seems?
		- holds the courses as posts
	- `m2` - the foreign table
		- holds the chapters as posts
- We will be joining them so courses and chapters are associated with each other in a table.
	- A [[SQL#Join|`LEFT JOIN`]] will be used
- aliasing everything by replacing "post" with "chapter"
	- `m2.post_id` is now `chapter_id`
	- `p2.post_title` is now `chapter_title`
	- `p2.post_date` is now `chapter_post_date`
	- `[p.ID](http://p.ID)` is now `course_id`
		- what?
		- This is markdown formatting
		- Used to create clickable hyperlinks in query results
		- Only useable if you run this query in a tool that renders markdown (SQL Notebooks or Bl tools)
		- if you run `SELECT '[Google](https://google.com) AS WebsiteLink;`
		- The resulting grid will show a clickable Google link
		- used by analysts to turn URLS stored in the database into clickable links in the final report output
	- `p.post_title` is now `course_title`
		- we are now dealing with `p` and not `p2`
		- What is the difference? and why are there two?
		- well it appears this is the course, not the chapter
		- so we are joining...
		- `p2` the chapter
		- `p` the course
	- `p.post_status` is now `course_status`
	- `p.post_date` is now `course_post_date`
- then we join the tables `m` and `m2`:
		- `FROM wp_postmeta m` - sets the primary source table and gives it the alias `m`
		- a `LEFT JOIN` ensures that all rows from the first table `m` are kept, even if no matching row is found in the second table `m2`
		- So in full: `FROM wp_postmeta m LEFT JOIN wp_postmeta m2` joins the 
	- 
- Presumably this is to resolve naming conflicts and improve readability.