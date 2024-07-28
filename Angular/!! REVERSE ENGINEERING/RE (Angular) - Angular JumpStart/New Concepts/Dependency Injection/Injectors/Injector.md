- An object in the Angular dependency-injection system that can find a named dependency in its cache or create a dependency using a configured [[Provider]]. 
- Injectors are created for NgModules and Directives automatically as part of the bootstrap process and are linked to one another via Injection Hierarchies.
- An injector provides a singleton instance of a dependency, and can inject this same instance into multiple directives and services.
- Forms the base class for all other Injector types in Angular
- This class is used to represent the [[Root Injector]] in a [[Module Injector Hierarchy]].

## Anything with a Decorator is an Injectable
- Important to note that anything with a decorator such as `@Injectable`, `@Component`, `@Pipe`, and `@Directive` are also injectables and thus can be injected into a class like a service can.

## Internals
https://dev.to/this-is-angular/how-angular-dependency-injection-works-under-the-hood-mln
- The implementation of an Injector can be compared to a dictionary of records. 
- The structure of a record looks like this:

	![[Pasted image 20240307135345.png|300]]

- The Injector stores information about all injectable classes, which includes anything with a decorator such as `@Injectable`, `@Component`, `@Pipe` and `@Directive`.
- The Injector iterates over its records to locate the requested token. Once found, the Injector returns the value if it's not undefined, indicating that the service has already been instantiated. Otherwise, the Injector creates and stores a new instance using the factory function and returns that instance.
- In the case where a provider is configured with `useClass` then the record object is simply overwritten:

	![[Pasted image 20240307141159.png|500]]

	![[Pasted image 20240307141411.png|300]]

- This means that when `AppComponent` requests `RootService`, the Injector will provide a new instance of `OtherService`.