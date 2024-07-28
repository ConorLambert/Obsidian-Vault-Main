- Available in **Angular v16+**
- Need to add `withComponentInputBinding()` to `appConfig`
``` typescript
export const appConfig: ApplicationConfig = {
  providers: [
    provideAnimations(),
    provideRouter(ROUTES, withDebugTracing(), withComponentInputBinding()),
  ],
};
```
- An example of a route with a parameter:
```typescript
{
	path: `shop/:categoryId`,
	component: ProductsViewComponent,
},
```
- Create Input setter on activated component (`ProductsViewComponent` in our example) with the name of the parameter (`categoryId` in our example):
```typescript
export class ProductsViewComponent {
	@Input() set categoryId(val: string) {
		this.pieService.setSelectedCategory(val);
	}
}
```