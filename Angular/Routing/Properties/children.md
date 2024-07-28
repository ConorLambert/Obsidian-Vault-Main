- Child routes configured via the `children` property do not use the full absolute path. 
- They only declare the relative child path segments. 
	- This is the same pattern that is followed for lazy loaded routes (using the [[loadChildren]] property)
- In the example below, notice how the string `home/` is prepended to the path property of the `child-one` and `child-two` routes.

![[Pasted image 20240717171458.png|500]]
![[Pasted image 20240717171445.png|500]]