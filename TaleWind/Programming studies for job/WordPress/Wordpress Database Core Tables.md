
This is what we are working with at TaleWind for data.

A standard installation of WordPress has this database structure.
WordPress provides the **wpdb** class to make accessing the database easy.

If you are manipulating this database, your code should do the housekeeping.
Don't [[SQL|orphan]] records, WordPress will not maintain the integrity between the tables.
(Such as when foreign keys are deleted)

### Tables:
`wp_users` - list of users. Used for authentication.
- handles essential login info
`wp_usermeta` - flexible storage for other user info. Flexible metadata.
- wp_capabilities (Administrator, Editor, Subscriber)
- first and last names, nicknames, bio
- Preferences

`wp_comments` - connects to users, but not posts, interestingly.
- author, date, content, karma, approved, agent, type, parent
`wp_commentmeta` - you know the drill.

`wp_posts `- Core of the data. Pages and navigation menu items are also stored here.
`wp_postmeta` - Non-core info, like from plugins. Prevents clutter in core table.

`wp_terms` - Post categories and tags. 
- Usually used to display info on the front end.
- Sometimes used in `JOIN` queries with `wp_term_taxonomy` and `wp_term_relationships` to identify which posts belong to which categories.
`wp_termmeta` - each term stores info in here.
`wp_term_taxonomy` - stores whether a term is a tag or a category.
`wp_term_relationships` 
- Post associations with categories / tags in the `wp_terms` table are stored here.


`wp_links` - holds info from links feature of WP. (Deprecated, but can be re-enabled.)
`wp_options` - Administration -> Settings panel options.



### Diagram:

![[Pasted image 20260507132805.png]]