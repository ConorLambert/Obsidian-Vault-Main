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
- No leading or trailing slashes (`/`).