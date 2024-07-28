##### Overview
- Created when an application is getting bootstrapped. 
- Serves as the **root** injector of our Dependency Injection system.
- Sits below the [[PlatformInjector]] in the hierarchy.

##### Module Based
- Configured using the `providers` property of the root `NgModule` class in a module based application.
- Associated with the root module (AppModule) in the [[Module Injector Hierarchy]]
- Represented by the [[Injector]] class.

##### Standalone Based
- Configured using the `providers` array of [[ApplicationConfig]] in a [[Standalone Application]].
- Represented by the [[EnvironmentInjector]] class.
