### Overview
- Restrict access to certain paths

### Use Cases
- User not authorized to view a route.
- Route is behind a [[feature flag]] that is not yet ready for production.
- Users have not yet completed a workflow.

### Types of Route Guards
##### canActivate
- Controls navigation to a route
- Will not show the view from the route if the the guard returns false.
##### canActivateChild
- Controls navigation to child routes of a route
- In the event of this guard returning false, the router will navigate to the route but will not navigate to the children of the route.
- Use Cases
	- Dashboard application where the user has some permissions but not others
##### canDeactivate
- Prevents navigation away from the route if the guard returns false
- Use Cases
	- If the user has not submitted a form, this guard will prevent navigation away from the form component until the user either submits or cancels.
##### canMatch
- In the event of this guard type failing, the router will continue to check any remaining routes.
- This guard type is very useful when working with [[Feature Flag|feature flags]].
	- The `canMatch` guard may refer to a component that holds a new feature or some refactor.
	- If the feature is turned off, the `canMatch` route will fail and the router will continue on to the next route in the tree which will hold the original feature or un-refactored code.

### Resolvers
- Fetches data for a route before a route can be activated
- Does not dictate whether a route is restricted
- With recent versions of Angular, we can bind an Input property of a component to the data returned from a resolver.
- *Blocks navigation until the function returns.*
	- Not a great solution if fetching data from slow endpoints.
- *With modern state management tools and reactive programming patterns, the situations in which you need a resolver are extremely rare*
	- Some teams do still use them however.

### Functional Route Guards
- Inject dependencies into the route guard functions to make server requests or obtain values from a store which will aid in resolving the guard. 
- Angular 14+

### URL Tree
- Returning a URL tree allows altering a route or redirecting to an alternative view.
- Think of it like a redirect.
- If a guard returns a URL tree, the current navigation is cancelled a new navigation to the URL tree is started.
- Use Cases:
	- If we want to redirect a user to a "You are not authorized view" 
	- If a route needs query params appended to it.
- All guard types except `canMatch` have the option of returning a URL tree.
- The `parseUrl` function of the `Router` class returns a URL tree:
```typescript
router.parseUrl('./not-authorized')
```

### Implementation
- Each guard type has an associated property in the Route object
	- It's not unusual for a route to have more then one restriction
- In the event of a guard type failing, all guard types except `canMatch` will cause the router to cancel checking any remaining routes in the tree.
- Must return an actual boolean or a URL tree (except for `canMatch`). Cannot be a truthy or falsey. 
	- If a non-boolean value is returned, the guard will be skipped and the route will be activated.
	- Use `!!` in your expressions to ensure the resulting type is a boolean (true or false).
		- `!!permissions?.includes(route)`

### Code Snippets
- [Module nine start](file:////Users/conorlambert/New%20Job/Angular%20Routing%20and%20Navigation%20Playbook/angular-routing-navigation-playbook/09/demos/module-nine-start/src/app/app.routes.ts)



