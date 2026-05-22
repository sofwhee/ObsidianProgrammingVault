## Media IDs

8-char alphanumeric string.
A digital fingerprint for the file.
The platform automatically assigns it to uploaded content.

It is strictly generated.
It cannot be manually assigned.
It cannot be changed.

Can be viewed in dashboard and embed codes.

Used for:
- Content Embedding
- Developers to have a reference to it in code
	- API requests to fetch video metadata
	- pull manifests
	- generate streaming URLs
- Avoids playback / tracking conflicts

## Client Tag

Also known as an "ad tag".

A specific URL that connects the player to a third party ad server or supply-side platform.

Used for:
- Players to grab an ad to play.
	- Player calls ad tag
	- Ad tag makes ad server return an ad payload (VAST XML file)
	- Player loads the ad
	- Player plays the ad when requested during the video.
- Client side JS to grab an ad to play.
	- Defined as the value of a custom key you set.
	- Allows player to dynamically pull the right ad based on the page you're on.
	- Useful if you want ads to behave differently depending on page/placement.

Usage notes:
- Fallbacks
	- pass an array of ad tag URLs instead of a single string