#### LoginModule Eagerly Loaded
- Eagerly loaded since we *may* need to go here right away as browser loads based on route user enters.

#### CoreModule vs SharedModule
- CoreModule is for singleton objects (services, components that are loaded only once, etc).
- SharedModule is for shared (multi-instance) objects.

#### NgModule Constructors
- NgModule constructors can use dependencies that are declared in the providers array of the module itself or in the providers array of any module it imports (explained [here](https://www.bennadel.com/blog/3180-ngmodule-constructors-provide-a-module-level-run-block-in-angular-2-1-1.htm)).

#### Re-exporting RouterModule
[Source](https://stackoverflow.com/questions/41823772/angular2-export-of-routermodule-why-it-is-required)
```typescript
@NgModule({
  imports: [RouterModule.forChild(routes)],
  exports: [ RouterModule ]
})
export class LoginRoutingModule {
  static components = [LoginComponent];
}
```
- We don't have to re-export
- Another option is to explicitly import the `RouterModule` into the `imports` array of the feature or root module that will use the `LoginRoutingModule`.
- Remember, because we have created a separate module specifically for our routes (seen as `LoginRoutingModule` above), that module will be imported by a feature or root module. The components of that feature or root module will therefore be using functionality of the `RouterModule` such `router-link` and `RouterLink`. 
- If we don't declare the `RouterModule` in the `exports` array of the `LoginRoutingModule` then it will need to be imported explicitly by the feature or root module (which the user may forget to do). 
- Better to export it from the `LoginRoutingModule` so that it is implicitly imported by any feature module that uses it.
- If the components of the feature module do not use the functionality and instead just create a set of routes then importing RouterModule is not needed