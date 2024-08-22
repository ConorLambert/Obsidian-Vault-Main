### Overview
- Set up and navigate multiple independent routes in a single app. 
- Allow the user to access or toggle portions of the page, such as a side-bar or dialog, using the URL
- Each auxiliary router outlet must have a unique name.

### Important
- Prepend single forward slash at the start of any [[Angular/Routing/Directives/routerLink|routerLink]] that activates an auxiliary route.
	- Don't need to for [[navigate()]] because it is absolute by default.
- Always use [[Route Parameters#queryParamsHandling='merge'|queryParamsHandling='merge']] for both [[Angular/Routing/Directives/routerLink|routerLink]] and [[navigate()]].

### Implementation
- Configured using the `name` property of `routerOutlet`
- Added at the same level as the main router outlet
```typescript
...
<router-outlet />
<router-outlet [name]="cart"/>
...
```
- Added as a `Route` to the root router module
	- Note the use of the `outlet` property
```typescript
{
	path: 'checkout',
	outlet: 'cart',
	component: CartComponent
}
```
- Activated via the [[Angular/Routing/Directives/routerLink|routerLink]] directive using the `outlets` property which is a `key:value` pair
	- The `key` is the name of the outlet (which is `cart` in our example)
	- The `value` is the path
```typescript
[routerLink]="['/', { outlets: { 'cart': 'checkout' }}]"
queryParamsHandling="merge"
```
- Don't forget to put `/` at the start.
- Don't forget to set `queryParamsHandling` to `merge`

### Closing or Removing an Auxiliary Route
- Setting the outlet to `null` using the `outlets` property along with the name of the outlet we wish to close.
```typescript
this.router.navigate([{ outlets: { 'cart': null } }], {
  queryParamsHandling: "merge",
});
```
- Don't forget to set `queryParamsHandling` to `merge`

### Use Cases
- Create popups that are also accessible via URL like a shopping cart.
- A chat window that stays opened during navigation
- Link your application’s users to deep parts of your application with a simple URL, without them having to click anywhere
- Reduce the initial loading time by lazy loading the routes in the same way as we would do with normal full-page routes

### Warning
- Can cause huge headaches if not implemented properly.