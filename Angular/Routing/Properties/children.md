- Used to configures [[Child routes]] or [[Nested Router Outlets]]
- Routes configured via the `children` property do not use the full absolute path. 
	- They only declare the relative child path segments. 
- In the example below, notice how the string `home/` is implicitly prepended to the `path` property of the `child-one` and `child-two` routes.
	- The top image is what we declare in code and the bottom image is what Angular turns that into

![[Pasted image 20240717171458.png|500]]
![[Pasted image 20240717171445.png|500]]