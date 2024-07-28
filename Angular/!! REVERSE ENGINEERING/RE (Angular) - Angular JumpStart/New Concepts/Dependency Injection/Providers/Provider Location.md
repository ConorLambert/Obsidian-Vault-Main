Where the dependency is provided will determine the scope of the dependency:
#### Application Level
###### Location
- Using the `providers`field in the *root* `NgModule` of the application:
```typescript
export const appConfig: ApplicationConfig = {
    providers: [
      { provide: HeroService },
    ]
};

bootstrapApplication(AppComponent, appConfig)
```
###### Scope
- The same instance of a service is available to all components, directives and pipes of the application.

#### Module Level
###### Location
- Using the `providers`field in an `NgModule` that is not the root module. 
###### Eagerly-Loaded Modules
- Same rules as Application Level.
- All providers of eagerly loaded modules are merged into the root injector at compile time.
###### Lazy-Loaded Modules
- The same instance of a service is available to all components, directives and pipes within the scope of that module.
- Lazy loaded modules have their own injector.

#### Component Level
###### Location
- Using the `providers` field of the `@Component` decorator:
```typescript
	@Component({
	  standalone: true,
	  selector: 'hero-list',
	  template: '...',
	  providers: [HeroService]
	})
	class HeroListComponent {}
```
###### Scope
- New instance of the service for each new instance of that component.
- In the above example, an instance of `HeroService` is created for each instance of `HeroListComponent` and other components and directives used in it's template: