#### Overview
- Decorator that marks a class as available to be provided and injected as a dependency.
- Marking a class with `@Injectable` ensures that the compiler will generate the necessary metadata to create the class's dependencies when the class is injected.
- `@Injectable` is actually a shortcut for having to decorate every parameter in your constructor with [[@Inject()]].
#### providedIn
- The `providedIn` property determines which injectors will provide the injectable.
- The following options specify that this injectable should be provided in one of the following injectors:
	- `'root'`:   The application-level injector in most apps.
	- `'platform'`: A special singleton platform injector shared by all applications on the page.
	- `NgModule`: The name of an NgModule in the application.

``` typescript
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class ItemService {
  name = 'telephone';
}
```

#### @Component and @Directive are Injectables
- Classes decorated with @Component and @Directive are automatically marked as @Injectable, so there is no need to explicitly use the @Injectable decorator for these classes.