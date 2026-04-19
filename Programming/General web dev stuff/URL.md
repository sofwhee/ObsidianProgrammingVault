Uniform Resource Locator.
A text string that specifies where a resource (web page, image, video) can be found on the internet.

AKA "Web address" "link"

## Anatomy

![[Pasted image 20251104114508.png]]

**Scheme:**
	Indicates the protocol the browser must use. (HTTP, HTTPS, mailto:)
**Authority:**
	:// **domain** : **port**
		**[[Domain]]** = web server. (domain name, IP address)
		**[[Port]]** = technical "gate" used to access the resources on the web server. Omitted when using default ports. (80 HTTP, 443 HTTPS)
**Path**: (to resource)
	Path to the resource. Nowadays an abstraction from the days when this represented a physical file location on a web server.
**Parameters:**
	Used by web server to do extra stuff before returning the resource. Each web server has its own rules regarding parameters. Only reliable way to know them is through the server owner. In this case, they are key/value pairs separated by &.
**Anchor:**
	A bookmarked spot on the resource. (Certain spot on a webpage, or in a video on the page) Uses a **[[fragment identifier]]**. (#)
	Never sent to the server.
	
	