### Overview
- Mainly used for the [[Angular/Routing/Directives/routerLink|routerLink]] directive

### Path Segment Prefixing
![[Pasted image 20240724155936.png|500]]

### Best Practices
- Use relative paths whenever possible
- Avoid absolute paths
	- Massive problems if URLs that lead to the component doing the routing are changed.
- Define constant route tokens that can be shared throughout application