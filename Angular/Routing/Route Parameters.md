## Types of Router Parameters

#### Required Path Parameters
- Named parameters
	- The name we give it is important
- Only accessible to the activated route (including children) but not parent or siblings
```typescript
{
	path: 'shop/:categoryId',
	component: ShopsComponent
}
```

#### Query Parameters
- Only available on the activated route
- Separate from the path segments
- Can be accessed from any class and not just the activated route.
- Avoid using [[Component Input Binding]] with the `set` method
	- Query params are globally available so any number of components could have Input properties with the same name as the query parameter causing some confusion.
###### queryParamsHandling='merge'
- Any existing query parameters on the current route will be retained when adding a new parameter.
- Basically, if the same route was activated again but with a different query parameter `QueryParamB`, then the current value of `QueryParamA` would still be retained. 
- Explained further [here](https://www.digitalocean.com/community/tutorials/angular-query-parameters#preserving-or-merging-query-parameters-with-queryparamshandling)

```typescript
// Template approach
[queryParams]="{ productId: 22 }"
queryParamsHandling="merge"

// Component approach
this.router.navigate(['../shops/cakes'], {
	relativeTo: this.activatedRoute,
	queryParams: { productId: 22 },
	queryParamsHandling="merge"
})
```


#### Matrix Parameters
- Only available on the activated route
- Considered a [[path#Segments|path segment]]
```typescript
// Example navigating to the following path
	// http://my-app.com/some/path;showModal=true;

// Template approach
<button [routerLink]="['some/path', {showModal: true}]">Show Modal</button>

// Component approach
this.router.navigate(['some/path', {showModal: true}], {
	relativeTo: this.activatedRoute
})

```