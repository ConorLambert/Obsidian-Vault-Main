### Purpose
- Before Standalone Components where introduced to Angular, there were only two types of injectors:
	- [[ModuleInjector]]
	- [[ElementInjector]]
- Now that there is a possibility to have a complete [[Standalone Application]] in Angular, resolving Injector dependencies based on modules is no longer possible. This is where the `EnvironmentInjector` comes in.
- Used to provide dependencies to standalone components, lazy-loaded routes, and other parts of your application that are not part of the component hierarchy.

#### Lazy-Loaded Modules
- For each lazy module, Angular creates a new environment injector, which contains a copy of the root environment injector and all the providers declared in the modules that are in the lazy loaded module tree.

#### Configuration
- The `EnvironmentInjector` can be configured in one of two ways by using:
	- `@NgModule.providers` array
	- The `providedIn` property of [[@Injectable()]] where the value is set to `root` or `platform`.
	- `providers` as a parameter of the `bootstrapAplication` function
	- `providers` within the `routing` statement