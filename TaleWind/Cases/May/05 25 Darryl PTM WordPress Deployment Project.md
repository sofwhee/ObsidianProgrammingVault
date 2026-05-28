[[How to install wordpress for a website]]
[empty database here](https://newlearning.lms.professionaltrainingmatters.org/)

Downloaded `wp-config.php` and unzipped.
Empty database already present above, no need to create a new one. The tables will be set up during the WordPress installation.
A user with privilege to the db already exists. It just needs to be setup in wordpress config, which will be done during the WP installation process.
FTP - use SCP file protocol, port 22, hostname and username included in the email.
Instead of a pass you'll need an auth key. Attached a ppk file for me to use.

[Site URL for LMS staging](https://newlearning.lms.professionaltrainingmatters.org/))

**Server Info -** Cluster: SPE Cluster

Code base directory: /home/ubuntu/efs/[professionaltrainingmatters.org](http://professionaltrainingmatters.org/) - **Reminder:** all other directories inside EFS are active site directories, so please be careful not to modify or update those.

Host name: 44.198.18.121

User name: ubuntu

Password: [Use SSH Key ppk attached]

**RDS Info:**

DB Host: [spe-2024.cluster-clh05vjfrova.us-east-1.rds.amazonaws.com](http://spe-2024.cluster-clh05vjfrova.us-east-1.rds.amazonaws.com/)  
DB Name: lmsptm_db  
DB User: lmsptm_user  
DB Password: xV12Ixh27a8l

---
5 26

HEX Deployment Release - google drive folder
march 2026
the files in here are not necessarily - we have plugins that may not be in here because we don't have updates for it
now that i'm mentioning about it i realized that we probably should have each, and actual folder for all the combined last updated packages no matter what period they were released
- might be a worthy project to undertake
If you find there's missing, let me know i can p9oint you to the right folder where to find the plugin

let's download the zip files
then start installing the theme
then i'll outline helpful steps for meto config
for now just download and install

to install theme, go to themes -> 
add theme -> 
zip file i downloaded, put it in there ->
upload our custom theme by choosing the zip file -> 
and then same thing for plugins in the plugins section -> 
first one to install shoould be the theme, media manaager, media uploader, channels plugin (you can see there's no media uploader, so check previous month release folders to see where we did our last update and pull it from there) -> 
continue installing all other excpet for LMS related plugins (the quiz, lms plugin ,and organization) and the ecommerce plugin. we can set these up after the baseline plugins are set up. -> 
while your'e installing, add this as a new record here in the hex plugins update trackikng sheet -> 
new row, OADSP LMS (Professional Training Matters), fill in the rest of the columns later on, for now just add the WP version, Hex theme, everything up to column o, skip lms and ecommerce, quiz, organization, and SEO. 

there are just problems if you do it in the wrong order.

## Problem with Http and Https

Css wouldn't load. Said the website was trying to load an insecure stylesheet over http. 
Normally this happens when an https site tries to load a resource over http.
I guess the website has an SSL certificate which makes it https, despite the wp_siteurl being http???

Anyway, we fix it like this:

Add the following HTTP rewrite before the Wordpress directive (Do this after WordPress has been installed)

.htaccess
```php
// conditional wrapper in Apache's .htaccess files
// execute URL rewriting rules only if mod_rewrite module is installed and enabled on the server
// prevents 500 internal server errors if rewrite directives were processed on a server that lacked this module
// mod_rewrite.c is a reference to the source file for the module
// Necessary for pretty permalinks in WP, cause it needs to rewrite URLs dynamically
// Only to be used if behind a reverse proxy or load balancer that sets this header.
// Without a proxy, rule can be insecure. Would allow anyone to inject the header and trick server into thinking it's secure.
// For standard setups checking %{HTTPS} !=on is the safer default.
<ifModule mod_rewrite.c>  
RewriteEngine On  
// if X-Forwarded-Proto header is http
RewriteCond %{HTTP:X-Forwarded-Proto} =http
// Permanently redirect (R=permanent)
// to https version of same url
RewriteRule .* https://%{HTTP:Host}%{REQUEST_URI} [L,R=permanent]  
</ifModule>  
```

wp-config.php
```php
// Tells WP that the site is served over HTTPS
// Stops WP from generating mixed content links
$_SERVER["HTTPS"] = "on";
```