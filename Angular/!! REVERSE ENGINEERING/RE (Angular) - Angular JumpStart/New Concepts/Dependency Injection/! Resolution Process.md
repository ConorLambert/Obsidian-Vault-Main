## Explained
- When a component declares a dependency, Angular tries to satisfy that dependency with its own [[ElementInjector]]. 
- If a provider is found in the ElementInjector then it first checks if the injector has any existing instances of that service. If a requested service instance doesn't yet exist, the injector makes one using the registered provider and adds it to the injector before returning the service to Angular.
- If the component's injector lacks the provider, it passes the request up to its parent component's ElementInjector where the above step is repeated.
- The requests keep forwarding up until Angular finds an injector that can handle the request or runs out of ancestor ElementInjectors.
##### Module Based
- If no dependency is found in the [[Element Injector Hierarchy]], then Angular goes back to the view that we started with and checks in which Module Injector Scope this component exists. 
- It then delegates the resolution process to the [[Module Injector Hierarchy]] starting at the Module Injector that our component belongs to. In the above example, the component exists in the Root Module Injector but if the component belonged to a lazy loaded module, then Angular would start at the Child Module Injector instead. The resolution process moves up the tree to the [[PlatformInjector]] and finishes at the [[NullInjector]].
##### Standalone Based
- If Angular doesn't find the provider in the [[Element Injector Hierarchy]], it goes back to the element where the request originated and looks in the [[Environment Injector Hierarchy]]. 
- This process then starts at the [[Root Injector]] and moves up the tree to the [[PlatformInjector]] and finishes at the [[NullInjector]].
- If Angular still doesn't find the provider at the [[NullInjector]], it throws an error.

## Service Resolution Process
- What is the resolution process when a service class is dependent on another service. 
- The same process is followed:
	- `ComponentA` consumes `Service1`
	- `Service1` consumes `Service2`
	- When resolving `Service2`, Angular will start the resolution process at `ComponentA`

## Examples
- Loads of good examples [here](https://dev.to/this-is-angular/how-angular-dependency-injection-works-under-the-hood-mln)
- Good examples on this Dev.to [article](https://dev.to/this-is-angular/how-angular-dependency-injection-works-under-the-hood-mln).

