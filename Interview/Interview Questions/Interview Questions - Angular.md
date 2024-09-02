# Questions: General
### What is Angular ?
- Angular is an open-source, JavaScript framework written in TypeScript that is used to build web applications.
- It is used to build professional and modern user interfaces
- It's a component based architecture which at it's core is just sectioning off parts of a larger project into smaller logical and functional pieces that can be used and re-used throughout the application.
- Angular comes with everything out of the box in order to develop complex web applications without the need to install third party packages.
### What are Single Page Applications ?
- More responsive experience
### What is the Purpose of the Angular CLI ?
- Converts Angular code into native JavaScript code so it can run in the browser.
- The Angular CLI can also setup projects, runs tests and many other things.
### Explain the files and folders in an Angular project ?
###### angular.json
- This is the file which has various properties and configuration of your Angular project. 
- This is the file which is first referred by the builder to look for all the paths and configurations and to check which is the main file.
###### package.json
- Lists the npm packages required for your project.
###### package-lock.json
- It stores an exact, versioned dependency tree rather than using starred versioning like `package.json` itself (e.g. 1.0.\*).
- This means you can guarantee the dependencies for other developers or prod releases, etc.
- We may control our own dependencies but we don't have control over the dependencies of our dependencies. 
- More info [here](https://stackoverflow.com/questions/44297803/what-is-the-role-of-the-package-lock-json)
###### tsconfig.json
- The presence of a `tsconfig.json` file in a directory indicates that the directory is the root of a TypeScript project. 
- Specifies the root files and the compiler options required to compile the project.
###### main.ts
- Entry point of the application
- Holds the bootstrapping code i.e. `bootstrapModule` or `bootstrap` for Angular 14+
- The **bootstrap** array in this file lists the components that should be known to the CLI at the point of time that it analyses the **index.html** file.
- Generally this component is the **AppComponent** contained within the **app.component.ts** file
###### index.html
- Acts as the *single page* that is core to the SPA functionality.
- `index.html` references the root component via the `app-root` tag.
- Compiler dynamically adds all the transpiled javascript files at the end of this file.
###### app.component.ts
- The component that acts as the *root* component of the application.
- Called from inside the **index.html** file using the `app-root` selector
- Added to the **bootstrap** array inside the **main.ts** file so the **index.html** file can render it
### Explain how an Angular application is bootstrapped
1. The Angular CLI first reads the `angular.json` file to determine the projects configuration.
2. The value defined for the `main` property in `angular.json` is read to determine the main entry point of the application (which is `main.ts` by default).
3. The `main.ts` file is then executed which contains the necessary bootstrapping code. 
	- For module based applications, the function which performs the bootstrapping is called `bootstrapModule` which takes the root module (named `AppModule`) as parameter.
	- For standalone based applications, the function is called `bootstrapApplication` which takes the root *component* (named `AppComponent`) as parameter. Note here that the `bootstrapApplication` function also takes as parameter an `AppConfig` object that contains information related to global services, routing and other possible configurations.
4. For module based applications, the `bootstrapModule` call will internally check the `bootstrap` array defined in the root module which holds the root component of our application (which is `AppComponent`). This additional step is not required for standalone applications.
5. Now that the root component is setup and configured, it's selector can be called from inside the `index.html` file.

------------------------------------------------------------------------
# Questions: Framework Comparison

### Why use Angular over other Frameworks ?
-  Angular for larger team environments. 
	- Scales well if new teams are added.
- Angular is better for larger applications where a standard must be followed.
- Comes with everything installed out of the box.
### What are the advantages of Angular over React ?
- Angular comes with a complete suite of tools out of the box that can be utilized to implement complex web applications.
- Because React relies heavily on third party packages, there is a chance that those third party packages lose support.
- Due to Angular being an opinionated framework, it has better code maintainability particularly for larger projects. React offers multiple ways of doing things which can result in a messy code base in the long run. Different developers will use different plugins for functionality throughout the application.
- People who are familiar with HTML and CSS find it more difficult to jump into React because the functional code is tied so heavily into the HTML and CSS. With Angular, the files are kept separately automatically.
- Angular is built on TypeScript so you get type safety out of the box but with React projects this is not required and often is not followed by developers.
- More info [here](https://www.reddit.com/r/angular/comments/1b4a3gk/angular_vs_react/).
### Why choose React over Angular ?
- Much easier hiring people due to the popularity of React.
- Angular has a steep learning curve.
- Much easier to get something out quickly due to it's lightweight nature.
- React provides much more flexibility for experienced developers.
### Angular vs Vue ?
- More info [here](https://www.simform.com/blog/angular-vs-vue/)


------------------------------------------------------------------------
# Questions: New Features
### What are Standalone Components ?
- A feature introduced in Angular **14** 
- Allows components to be created that don't need to be declared in an Angular module (NgModule). 
### What are the benefits of Standalone Components ?
- Reduces boilerplate code.
- Simplified dependency management
	- Import into component itself rather than importing at a module level.

### What new features are in Angular ?
- Ivy default rendering engine
- Standalone Components
- Signals
- Component Input Binding
- Inject services into functional routes

------------------------------------------------------------------------
# Questions: Concepts Basic
### What are Components ?
- Fundamental building block
- TypeScript class with an associated view and encapsulated logic
- Created using the `@Component` decorator.

### What are Modules ?
- Organize and structure an application.
- Group related components, services, directives and pipes together
- Makes application more modular, maintainable and scalable.

### What are Directives ?
- Directives are classes that add additional behaviour to elements in your Angular applications.
- Directives are special markers in the DOM that Angular's compiler uses to manipulate elements, apply specific behaviours, or dynamically change the structure of the view.

### What are the three types of directives in Angular ?
###### Component
- Directive with a view template and logic
###### Structural
- Adding, removing, or manipulating elements
###### Attribute
- Change appearance or behaviour of *existing element*

### What is data binding ?
- Synchronise data between the component (model) and the view (template). 
- Enables dynamic communication between the UI elements and the application's underlying data, ensuring that changes in the model are reflected in the view and vice versa. 

### What is two-way data binding ?
- Bind data in both directions - from the component to the view and from the view back to the component. 
- This is commonly used in form elements where the user can input data.

### What are Decorators and their types ?
- Special functions that attach metadata to classes, methods, properties, or parameters, to modify their behaviour and provide information that Angular uses to perform various tasks.
- Class
	- Meta-data for classes e.g. `@Component`, `@Directive`
- Property
	- Bind properties to specific behaviours e.g. `@Input`, `@Output`
- Method
	- Modify behaviour of methods e.g. `@HostListener`
- Parameter
	- Inject dependencies into class constructors e.g. `@Inject`

### What are Annotations ?
- Same as Decorators but where used in earlier Angular 2 version.
- TypeScript then came up with the concept of Decorators and Angular adopted them instead.

### What are Pipes ?
- Transform the data displayed in the template. 
- Takes data as input and return the transformed output for display. 
- Pipes are often used for tasks like formatting dates, numbers, currencies, or strings, and they can also be used to filter or sort data.

### What are pure and impure Pipes ?
###### Pure
- Only re-computes its output when its input values change. 
- Optimization that allows Angular to avoid unnecessary recalculations, leading to better performance.
- Checked only during change detection and and checked based on *reference equality*.
- All pipes in Angular are pure by default
###### Impure
- Re-computes its output every change detection cycle 

------------------------------------------------------------------------
# Questions: Concepts Moderate

### Difference between `canActivate` and `canLoad` ?
- `canActivate`:
	- Prevent unauthorised access to routes
- `canLoad`:
	- Prevent application from loading entire modules lazily if the user is not authorised

### What are HTTP interceptors ?
- Used to intercept and handle HTTP requests and responses globally.
- Modify requests or responses before they are sent or received by the application. 
- Useful for various tasks such as adding headers, logging, error handling, or authentication

### What is Eager and Lazy Loading ?
###### Eager Loading
- Loading all modules and their components upfront when the application starts.
- All modules and components are immediately available.
###### Lazy Loading
- Modules and their associated components are loaded on demand, rather than at application startup. 
- Helps improve initial loading time of the application by deferring the loading of modules until they are actually needed (e.g., when a user navigates to a specific route).

### How are Observables different from Promises ?
###### Observables:
- Handle multiple values over time, support lazy execution, provide cancellation, and have a rich set of operators for data manipulation. 
- They are particularly useful in scenarios with continuous data streams and complex asynchronous operations.
###### Promises:
- Handle a single future value or error, start execution immediately, do not support cancellation directly, and offer basic chaining methods. 
- They are suitable for simple asynchronous tasks that produce a single result.

### Explain each lifecycle hook in Angular and their sequence of execution ?
- [[! NOTES (The Complete Guide - Udemy Course)#Lifecycle Hooks & Sequence]]

### What is the Component Decorator in Angular ?
- It marks a class as an Angular component and allows Angular to handle its lifecycle, rendering, and dependency injection

### What exactly is the Router state ?
- Represents the current state of the router, including information about the active route, route parameters, query parameters, and the navigation history.

------------------------------------------------------------------------
# Questions: View Encapsulation

### What is View Encapsulation ?
- Defines whether the template and styles defined within a component can affect the whole application or vice versa.

### What are the strategies available for View Encapsulation ?
###### Emulated
- Styles are scoped to the component using unique attribute selectors.
###### None
- No style encapsulation is applied
- Styles from one component can affect other components.
###### ShadowDom
- True encapsulation using native Shadow DOM
- Compatibility issues with older 

### Explain the native Shadow DOM in browsers ?
- Shadow DOM is a web standard that allows developers to encapsulate styles and markup in a way that is isolated from the rest of the document. This encapsulation helps to avoid conflicts between styles and scripts in different parts of a web application.
- Shadow DOM creates a "shadow tree" for an element, which is a separate DOM subtree that is hidden from the main document’s DOM. The styles and markup defined within this shadow tree do not affect the rest of the document, and vice versa.

### Why not just use `ShadowDom` instead of `Emulated` as a View Encapsulation strategy ?
- Shadow DOM is a part of the Web Components standard and is supported in most modern browsers. 
- However, there may be issues with some older browsers or environments that do not fully support Shadow DOM.

### What is a shadow root ?
- A container that encapsulates a subtree of DOM elements, providing style and script encapsulation for that subtree. 
- The shadow root is created when you attach a shadow DOM to an element, isolating the element's internal structure and styles from the rest of the document.
- The shadow root contains a **shadow tree**, which is a subtree of DOM elements that are part of the shadow DOM. This tree is completely isolated from the main document's DOM, and its styles are scoped to elements within the shadow tree.

### How does Angular implement the `ShadowDOM` View Encapsulation strategy ?
- Angular attaches a shadow root to the component’s host element when the component is initialized. This shadow root contains the component's template and styles.
- Styles defined in the component’s CSS are applied only to elements inside the shadow root.

### How does Angular implement the `Emulated` View Encapsulation strategy ?
- The following explains how Angular implements View Encapsulation so that the browser will apply the component styles only to that component:
	- For every component, Angular creates a unique attribute.
	- This unique attribute is appended to every HTML element of that component. 
	- Each selector in the CSS file for that component is updated so that the unique attribute is prepended to the selector declaration.

------------------------------------------------------------------------
# Questions: Dependency Injection
### What is dependency injection in Angular ?
- A way for Angular to achieve Inversion of Control (IoC), where the framework is responsible for creating and managing the dependencies rather than the components themselves.
- **Injectors:**
	- Responsible for creating and providing instances of services or dependencies to components or other services.
	- Dependencies are specified as parameters in the constructor of a class, and Angular's injector provides instances of these dependencies when creating the class.
- **Providers:**
	- Instructions for Angular on how to create an instance of a dependency. 
	- They are used to configure how the DI system should supply the service or dependency.

### What are services in Angular ?
- Classes that provide specific functionality, which can be shared across multiple components or other services.

### Explain how Angular resolves a dependency.
- Angular's dependency injection system uses a hierarchical structure of injectors to resolve dependencies.
- [[! Resolution Process]]

### How does Angular resolve a dependency defined in a service used by a component ?
- [[! Resolution Process#Service Resolution Process]]

------------------------------------------------------------------------
# Questions: RxJS

### What is RxJS, and how does it work in Angular ?
- ???

------------------------------------------------------------------------
# Questions: Forms

### What are Template and Reactive forms?
- ???

------------------------------------------------------------------------
# Questions: Modules
- ???

------------------------------------------------------------------------
# Questions: Concepts Advanced
### Explain the Ivy Compiler
- ???
### What is NgZone ?

### What is transpiling ?
- Transpiling in Angular refers to the process of converting TypeScript code into JavaScript code that web browsers can execute.

### What is an JIT compilation ?

### What is an AOT compilation and what are it's advantages ?

### What type of DOM does Angular implement ?

### What is a bootstrapping module ?

------------------------------------------------------------------------
# Questions: Change Detection

### How does change detection work in Angular ?
### How would you optimize change detection ?
- Use OnPush with immutable data structures
	- Medium [article](https://medium.com/@connecttosurajpatil/angular-change-detection-immutable-data-structures-98bc402b6756)

------------------------------------------------------------------------
# Questions: Explainer

### How do you handle HTTP requests in Angular ?

### How do you debug an Angular application ?

### How do you structure your Angular application ?

------------------------------------------------------------------------
# Questions: Decision Making

### Why use lazy-loaded modules ?

### How to share data between components ?

### When to use Template vs Reactive Forms ?

### How do you deal with errors in observables?
- `catchError` operator can be used to handle and recover from errors. 
- This operator allows you to provide a fallback value or execute alternative logic like error handling.
### How do you reference an element from component code ?
- [[! NOTES (The Complete Guide - Udemy Course)#Template Reference|Template reference variables]] combined with @ViewChild and @ViewChildren directives. 
- Make sure to put any initialization code for the @ViewChild and @ViewChildren directives  inside ngAfterViewInit as explained [[! NOTES (The Complete Guide - Udemy Course)#`@ViewChild` and `ngAfterViewInit` hook.|here]].

------------------------------------------------------------------------
# Questions: Coding Questions

### How do you implement routing in Angular ?

### How would you invalidate a user's session and redirect them to login ?
- {{It is mainly trying to get them to mention Interceptors at the HttpClient level}}
###  RXJS question to combine the data from 2 observables into a different formatted data as an observable

------------------------------------------------------------------------
# Questions: Experience
### What is most favourite feature of Angular ?

### What is your least favourite feature of Angular ?
- It was modules but something else ???

### What project are you most proud of ?
- Implementation of a simple relation database using the C programming language.
- Athora upgraded project.

### What is the most complex feature you have built ?

### What are some ways you have used RxJS ?


