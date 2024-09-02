[ChatGPT Source](https://chatgpt.com/c/eff38f15-54e9-4021-ac1d-e8c9b480978a)
- Situation is related to a client sending requests to a server or domain
- These requests mainly come from a web page 
- CORS seeks to prevent requests being made from web pages that are not authorized.
- An example:
	- Imagine a banking site with URL `https://bank.com` with sensitive user information. The user requests that site, enters information and submits it back. 
	- If a malicious site `https://evil.com` could bypass the same-origin policy, it might trick the browser into sending requests to `https://bank.com` and accessing private data without the user's knowledge. 
	- CORS headers on `https://bank.com` ensure that only requests from trusted domains (or none at all) are allowed. 
- A typical setting is `Same-Origin Policy` which means, using the example above, that only web pages who's URL is `https://bank.com` can make requests to `https://bank.com` i.e. the site that initially served the web page (request).
- NOTE: It's the browser that enforces the CORS policy using the HTTP headers sent by the server. 