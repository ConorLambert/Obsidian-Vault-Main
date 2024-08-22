### Overview
- Also called code splitting
- Reduce initial bundle size
- Some routes will not be required for the main page load.
	- These routes will be loaded only until the user navigates them.

### Tips
- Lazy load routes that are not visible on the home view
	- Especially for larger enterprise applications
	
### Preloading Strategies
- Preload lazy loaded routes that we know the user is going to visit
- When user navigates to the lazy loaded route, the code is already downloaded.
- `withPreloading(PreloadAllModules)` for standalone applications
###### PreloadAllModules
- Preloads all lazy loaded modules after the main bundle has been downloaded
###### QuicklinkStrategy
- Preloads only the routes associated with links on the current page

### Lazy Loaded Module
- Use `loadChildren` and navigate to the module location.

### Lazy Loaded Components
- Use `loadComponent` instead of `loadChildren` and navigate to the component location.

### Lazy Loaded Routes
- Used to lazy load multiple components
- Lazy loading components only loads a single standalone component
- How do we load multiple standalone components?
- This is where lazy loaded routes comes in
- A route config generally contains multiple components so we want to load all of them when the route is activated.
- Done using the `loadChildren` method and navigate to the route file location.