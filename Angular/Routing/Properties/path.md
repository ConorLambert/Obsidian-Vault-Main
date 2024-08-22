#### Overview
- The `path` property only deals with the **path** (or **subdirectory**) section of a URL:
	![[Pasted image 20240716160601.png|300]]
	
#### Segments
- The strings between slashes are seen as **segments**:
	- `shop` is a segment
	- `pies` is a segment

#### Valid Path Declarations
- The `path` parameter expects a string that can be either of the following
	- Single path segment
		- `path: 'shop'`
	- Empty string 
		- `path: ''`
	- Multiple path segments
		- `path: 'shop/pie'`
	- [[Wildcard Route]]
		- `path: '**'`
- No leading or trailing slashes (`/`).

#### Empty path (path: '')
- The empty path is a bit of a special case because it can match any segment *without "consuming" it* (so its children would have to match that segment again).```
- Discussed [here](https://stackoverflow.com/questions/42992212/in-angular-what-is-pathmatch-full-and-what-effect-does-it-have/62476799#62476799) with a good example under the section titled **Empty path (path: '')**
