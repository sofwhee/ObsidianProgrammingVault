
Step 1: Download and extract from https://wordpress.org/download/

Step 2: Install WP on a database.
- If you have only one database and it's in use, make sure to have a distinctive prefix for your tables to avoid over-writing any existing database files.
- phpMyAdmin
	- If you don't already have a WP database in the left dropdown, make one.
	- For language and encoding collation, choose in the "utf8_" series
	- Click phpMyAdmin to main page, click Users.
	- If a user relating to WP doesn't already exist in list, make one.
		- Add user
		- Once done, edit privileges in the users screen
		- Database-specific privileges, under Add privileges to the following databases, select new database.
		- Go
		- Page refreshes
		- Check all to select all privileges
		- Go
		- Make note of host name listed after Server: at top (usually localhost)

Step 3: Set up `wp-config.php`
- You can make the file yourself or let WP try when you run the installation script.
- Making it yourself:
	- `wp-config.php` sits in the WP file dir root.
	- Contains base config details for website
	- Contains database connection info.
	- Not included in first download of WP.
	- Created for you based on info you provide in the installation process.
- Rename the `wp-config-sample.php` to `wp-config.php`
- Open it in your IDE
- Enter your database info under the section:
- `// ** MySQL settings - You can get this info from your web host ** //`
- It should all be the same as the stuff you used in step 2.
- You can leave DB_CHARSET as is, and DB_COLLATE blank.
- Enter **secret values** under `/* Authentication Unique Keys and Salts. */`
- Save `wp-config.php`.

Step 4: Upload files
- Choose where on your domain the WP site should appear.
- Root? `https://example.com/`
- Subdirectory? `https://example.com/blog/`
- Probably best to ask.
- If root dir, FTP client to upload all contents (but not the directory itself) into the root dir
- If subdir, rename WP directory to desired name, then FTP client upload dir to desired location within root dir of website

Step 5: Run the Install Script
- Point a web browser to start installation script
- If you placed WP files in the root dir, visit https://example.com/wp-admin/install.php
- If you placed them in a subdir (blog here) visit https://example.com/blog/wp-admin/install.php
- Set up configuration file
- If WP can't find the `wp-config.php`, it will offer to try and make it itself.
- WP will run you through the details and write them to a new `wp-config.php`
- If it works, go ahead with install
- otherwise, go back and make it yourself.