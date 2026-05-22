![[Pasted image 20260511131000.png]]

![[Pasted image 20260511131034.png]]

## Gemini explanation

![[Pasted image 20260511131148.png]]
## TaleWind API call

![[Pasted image 20260511130726.png]]

`https://stream.asha.org`
domain (i think?)

.../**wpcontent**/themes/enterprise/feed/mrssMob.php...

One of the three core directories in WP. 
`/wp-admin/` 
- Contains admin backend files. Dashboard, site management scripts, admin interface styling
`/wp-content/`
- Contains themes that control your site's design.
`/wp-includes/`
- Houses core runtime libraries and internal logic for running WordPress. Never modify files here.

`wp-config.php` Database and site settings
`.htaccess` Server rules and permalinks.

....../wpcontent/themes/**enterprise**/feed...

The enterprise theme.
Enterprise themes are designed for large oranizations.
They easily allow for API and system integrations.

.../wpcontent/themes/enterprise/**feed/**...

Access the site's built-in RSS feed.
It provides a structured XML version of your content that can be read by external apps.

... feed/**mrssMob.php**

The end of the path. The resource on the web server. In this case, a php file.

... feed/mrssMob.php **?apiKey=12CFD241146A49CC**

? is a query. We are querying the php file
? starts the query, then you use **&** to separate parameters.
API key is the password for software to talk to other software.
Like using a Google Maps Platform API key to display a map on your site.

Note: This is on the legacy platform, but passing an API key in a URL is discouraged despite being common. It exposes the API key. Instead, send it in the HTTP Header. That keeps it out of logs and history. Use an authorization header with a Bearer prefix like `Authorization: Bearer your_apy_key`

... feed/mrssMob.php?apiKey=12CFD241146A49CC **&feature&limit=2**

This is how you pass arguments in. 

## Querying php files

To query a PHP file via a URL, you use query strings.

**Query strings** are sets of key-value pairs appended to the end of the file's address.

If you need to manipulate URL  or query strings programmatically:
`http_build_query()` generates a URL-encoded query string from an array.
`parse_url()` breaks a url into its components. (scheme, host, path, query)
`parse_str()` parses a string (like a query string) into variables.

Note: **NEVER** pass sensitive info in a query string. 
Note: **ALWAYS** validate and sanitize input from `$_GET` to prevent SQL injection.

Inside your PHP script, you access these values using the `$_GET` [superglobal](https://www.w3schools.com/PhP/php_superglobals_get.asp) array.

```PHP
// If the URL is ://mysite.com $name = $_GET['user']; 
echo "Hello, " . $name; // Outputs: Hello, John
```