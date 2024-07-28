### General Problem
- Imagine that an application has a dependency on a module that by its turn imports another module which then provides a service class.
- Now imagine that this imported service class is effectively not used anywhere in our application, by whatever reason!
- If you are using for example AngularFire or other large third-party modules with tons of functionality, these modules contain all sorts of services that you might need in your application, or not.
- You might use some of the services, but probably not all of them.
- *The idea is that we should be able to import a module, but if we don't use some of its services then we shouldn't need to include them in our production bundle.*

### Angular Problem
- When the Angular CLI is building our application bundle, it will try as much as possible to "tree shake" any code that is not necessary out of the bundle, in order to reduce its size as much as possible.
- The CLI will try to do by statically inspecting the Typescript dependencies of our code, and determine if a dependency is being used or not.
- If it finds that the dependency is not being used, it will remove it from the bundle and so reduce its size.
- But if we are adding the module with the unused services directly in the `providers` property of a module or component, we need to first import that module or service directly via a Typescript import.
- *And this Typescript import will effectively prevent the tree shaking service from removing the unused service.*
- The tree shaker sees that the service is being imported explicitly via a Typescript import, and so it will wrongly think its being used and it won't remove it from the production bundle.

### Solution: Tree-Shakeable Providers
- Rather then declaring the service inside the `providers` array of the module in question, we instead declare the module inside the service using the `providedIn` property of the [[@Injectable]] decorator.
- We are essentially flipping the order of dependencies so that the module is defined inside the service class and not vice-versa.
- The example below illustrates a `CoursesService` class that is part of the `CoursesModule` but `CoursesService` is not declared in the providers array of `CoursesModule`. Instead we declare  `CoursesModule` in the `CoursesService` class using the `providedIn` property:
###### courses.module.ts
```typescript
@NgModule({
  imports: [
    CommonModule
  ],
  declarations: [
      CourseCardComponent
  ],
    exports: [
        CourseCardComponent
    ]
})
export class CoursesModule { }
```
###### courses.service.ts
```typescript
@Injectable({
  providedIn: CoursesModule
})
export class CoursesService() {

  constructor(private http: HttpClient) {

  }
...
}
```