#### patchMatch: full
- Phenomenal explanation in this Stack Overflow [answer](https://stackoverflow.com/a/62476799/17385921). 
- TLDR: What is defined for the `path` property of the same `Route` config must match the entirety of the *remaining* URL.
- `pathMatch: full` configuration is basically saying this:
	- *"Ignore my children and only match me. If I am not able to match all of the remaining URL segments myself, then move on."*