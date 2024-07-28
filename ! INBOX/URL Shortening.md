[Source URL](https://www.reddit.com/r/explainlikeimfive/comments/4nxos4/eli5_what_is_the_purpose_of_short_urls_and_how/)

#### Use Cases
- Short URLs are used to save space, especially in places with character limits like Twitter.
- They can also be used to disguise the actual destination of a link, which can be useful for tracking purposes or to avoid spam filters.
- Aside from the above issues, long links are often unsightly.

#### How it Works
- URL shortening services work by creating a database that maps short strings to full URLs.
- When a user clicks on a short URL:
	1. The browser sends a request to the URL shortening service.
	2. The URL shortening service searches its database for the matching long URL
	3. The service returns the long URL to the browser using a HTTP 302 response
	4. The browser re-directs the user to the correct page

#### HTTP 3xx Series:
- HTTP response codes 300 to 308 are special in that they also pass a URL. 
- A 300-series response code means "redirect"
- They all tell your web browser: "this is the url you really want to go to, here"

#### Shortening Algorithm
- Some discussion on this Quora [thread](https://www.quora.com/What-are-the-http-bit-ly-and-t-co-shortening-algorithms)

#### URL Shortening Services
- There are a number of third party vendors that provide URL Shortening as a service
	- Bitly.
	- TinyURL.

#### Security Risk
- Security is always a risk with URL shorteners
	- The user doesn't really know where a masked URL leads to.
- But companies try to mitigate this by running links through spam checkers, virus scanners, and services like Google's Safe Browsing.