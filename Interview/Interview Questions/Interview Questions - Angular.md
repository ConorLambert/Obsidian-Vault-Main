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

### What are the benefits of Standalone Components ?

### What new features are in Angular ?
- Component Input Binding
- Inject services into functional routes
- ???

------------------------------------------------------------------------
# Questions: Concepts Basic

### What are Components ?

### What are Modules ?

### What are Directives ?
- Attributes that allow the user to write new HTML syntax specific to their applications.
- They execute whenever the Angular compiler finds them in the DOM. Angular supports three types of directives.
### What is data binding ?

### What is two-way data binding ?

### What are Decorators and their types ?

### What are Annotations ?

### What are Pipes ?
- Simple functions designed to accept an input value, process, and return as an output, a transformed value in a more technical understanding.
### What are pure and impure Pipes ?

------------------------------------------------------------------------
# Questions: Concepts Moderate

### What are HTTP interceptors ?

### What is Eager and Lazy Loading ?

### How are observables different from promises ?

### What is dependency injection in Angular ?

### What are class decorators ?

### What are Method decorators ?

### What are property decorators ?

### What is the Component Decorator in Angular ?

### What are lifecycle hooks in Angular ?

### What exactly is the router state ?

### What is View Encapsulation ?
- Defines whether the template and styles defined within the component can affect the whole application or vice versa.
### What are the strategies available for View Encapsulation ?
- ???
### What is RxJS, and how does it work in Angular ?

### What are services in Angular ?

### What are Template and Reactive forms?

------------------------------------------------------------------------
# Questions: Concepts Advanced
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


