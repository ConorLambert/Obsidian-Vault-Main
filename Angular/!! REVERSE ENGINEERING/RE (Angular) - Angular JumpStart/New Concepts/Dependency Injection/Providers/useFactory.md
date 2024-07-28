## Explained
- Use a factory method to create a dependency.
- Useful when we want to get some value from the information that is not available before the run application.
- With this approach you can create a dynamic value based on information available in the DI and elsewhere in the app.

## Example
- Below example is explained further [here](https://angular.io/guide/dependency-injection-providers#factory-providers-usefactory)
- If the factory function has dependencies that put them in the `deps` array
```typescript
[
	...,
	{ 
		provide: HeroService, 
		useFactory: 
			(logger: Logger, userService: UserService) => 
			new HeroService(logger, userService.user.isAuthorized),
		deps: [Logger, UserService] 
	},
	...
]
```

## Use Cases

#### URLs per Environment
- Explained [here](https://medium.com/@hungbui/factory-usefactory-in-angular-di-a9c432cc466b)
- Creating HTTP services with different base URLs for different environments (prod, staging, development or testing )
#### Some Other Example
- Use case example [here](https://developer.okta.com/blog/2022/10/11/angular-dependency-injection#configure-with-usefactory)