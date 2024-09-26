# Questions: General
### What is Angular ?
- Angular is an open-source, JavaScript framework written in TypeScript that is used to build professional and modern web applications.
- It's a component based architecture which allows you to build applications using smaller units of functionality.
- Angular comes with everything out of the box in order to develop complex web applications without the need to install third party packages.

### What are Single Page Applications ?
- The whole page doesn't refresh when navigating around web application.
- Only the part that is required to change will update.
- More responsive experience

### What is the Purpose of the Angular CLI ?
- Converts Angular code into native JavaScript code so it can run in the browser.
- The Angular CLI can also setup projects, runs tests and many other things.

### Explain the files and folders in an Angular project ?
###### angular.json
- Various properties and configurations for your Angular project. 
- First referred by the builder to look for all the paths and configurations and to check which is the main file.
###### package.json
- Lists the npm packages required for your project.
###### package-lock.json
[ChatGPT answer](https://chatgpt.com/c/66e980ba-1994-8012-b04b-18af0cdf9c9c)
- While `package.json` defines the required dependencies and their versions (or version ranges), `package-lock.json` stores the exact version of each installed dependency, ensuring that the same versions are installed when other developers or deployment environments run `npm install`.
- This tree includes the dependencies of your dependencies.
- This guarantees consistency across different environments, reducing the risk of unexpected behavior caused by installing slightly different versions of a package.
###### tsconfig.json
- Specifies the *root files* and the *compiler options* required to compile the project.
- The presence of a `tsconfig.json` file in a directory indicates that the directory is the root of a TypeScript project. 
###### main.ts
- Entry point of the application
- Holds the bootstrapping code i.e. `bootstrapModule` or `bootstrap` for Angular 14+
- Angular 14+
	- The **bootstrap** array in this file lists the components that should be known to the CLI at the point of time that it analyses the **index.html** file.
- Angular < 14
	- bootstrapModule takes the root module of the application (likely the AppModule)
	- AppModule has the **bootstrap** array
- Generally this root component is the **AppComponent** contained within the **app.component.ts** file
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
###### Tools
- Angular comes with a complete suite of tools out of the box that can be utilized to implement complex web applications.
- Because React relies heavily on third party packages, there is a chance that those third party packages lose support.
###### Opinionated
- Due to Angular being an opinionated framework, it has better code maintainability particularly for larger projects. 
- React offers multiple ways of doing things which can result in a messy code base in the long run. Different developers will use different plugins for functionality throughout the application.
###### HTML, CSS Familiarity
- People who are familiar with HTML and CSS find it more difficult to jump into React because the functional code is tied so heavily into the HTML and CSS. 
- With Angular, the files are kept separately automatically.
###### TypeScript and type safety
- Angular is built on TypeScript so you get type safety out of the box but with React projects this is not required and often is not followed by developers.
- More info [here](https://www.reddit.com/r/angular/comments/1b4a3gk/angular_vs_react/).
### Why choose React over Angular ?
- Much easier **hiring people** due to the popularity of React.
- Angular has a **steep learning curve**.
- Much easier to **get something out quickly** due to it's lightweight nature.
- React provides much more **flexibility for experienced developers**.
### Angular vs Vue ?
- More info [here](https://www.simform.com/blog/angular-vs-vue/)

------------------------------------------------------------------------
# Questions: New Features
### What are Standalone Components ?
- Allows components to be created that don't need to be declared in an Angular module (NgModule). 
- A feature introduced in Angular **14** 
### What are the benefits of Standalone Components ?
- Less boilerplate code.
- Learning curve
- Simplified dependency management
	- Import into component itself rather than importing at a module level.

### What new features are in Angular ?
- Ivy default rendering engine
- Standalone Components
- Signals
- Component Input Binding
- `@Inject` services into functional routes

------------------------------------------------------------------------
# Questions: Concepts Basic
### What are Components ?
- TypeScript class with an associated view and encapsulated logic
- Created using the `@Component` decorator.
- Fundamental building block of Angular

### What are Modules ?
- Group related components, services, directives and pipes together
- Organize and structure an application.
- Makes application more modular, maintainable and scalable.

### What are Directives ?
- +++ Directives are *classes* that add additional behaviour to elements in your Angular applications.
- Directives are special markers in the DOM that Angular's compiler uses to manipulate elements, apply specific behaviours, or dynamically change the structure of the view.

### What are the three types of directives in Angular ?
###### Component
- Directive with a view template and logic
###### Structural
- Adding, removing, or manipulating elements
###### Attribute
- Change appearance or behaviour of existing element

### What is data binding ?
- Synchronize data between the component (model) and the view (template). 
- Enables dynamic communication between the UI elements and the underlying model, ensuring that changes in the model are reflected in the view and vice versa. 

### What is two-way data binding ?
- Bind data in both directions - from the component to the view and from the view back to the component. 
- This is commonly used in form elements where the user can input data.

### What are Decorators and their types ?
- Special functions that attach metadata to classes, methods, properties, or parameters, to modify their behaviour and provide information that Angular uses to perform various tasks.
- TypeScript construct
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
- Checked only during change detection and based on *reference equality*.
- Optimization that allows Angular to avoid unnecessary recalculations, leading to better performance.
- All pipes are pure by default
###### Impure
- Re-computes its output every change detection cycle regardless of whether the value has changed.

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

### Explain each lifecycle hook in Angular and their sequence of execution ?
- [[! NOTES (The Complete Guide - Udemy Course)#Lifecycle Hooks & Sequence]]

### What is the Component Decorator in Angular ?
- It marks a class as an Angular component and allows Angular to handle its lifecycle, rendering, and dependency injection

### What exactly is the Router state ?
- Represents the current state of the router, including information about the active route, route parameters, query parameters, and the navigation history.

------------------------------------------------------------------------
# Questions: Data Binding
### What is the difference between String Interpolation and Property Binding ?
###### String Interpolation
- Used to output text in the template
- Can only take strings or types that can be converted to string
- A function can be used as long as the function returns a string or a type that can be converted to a string.
###### Property Binding
- Used to bind properties of a HTML element or directive.
- Can only take the type of the property or a type that can be converted to the property type. For example, the `disabled` property of a button elements takes a boolean.
- A function can be used as long as the function returns the properties type or a type that can be converted to the properties type.

### What is Event Binding ?
- Used to bind events of a HTML element or directive.

### What is Two-way data binding ?
- A combination of **Property Binding** and **Event Binding**.

### What properties can two-way data binding work on ?
- Only works on certain properties that have been extended by Angular e.g. `ngModel`.

### How can you make a property of your component utilize two-way data binding ?
- Name your `@Output` property based on your `@Input` property but with the word "Change" appended. 
- For example, if your `@Input` property is called `size` then your `@Output` property should be called `sizeChange`

### How to get access to a Template Reference if element is not available on component initialization (e.g. maybe due to being wrapped in an `ngIf` block) ?
- `ViewChild` will not work if the template reference element is not available on component initialisation (e.g. could be wrapped in an `ngIf`). 
- Instead, you can pass the template reference to a method that is called in the template
![[Pasted image 20240118181011.png|500]]

### Why would you use a Property Alias ?
- It's a simple way to prevent your code from breaking if another dev ever changes that variable name. 
- If the variable changes in the component, you don't need to change it in your template because it's using the alias. 

### What are some naming conventions for your `@Output` properties ?
- Never use a property name that Angular or the native web uses
- Don't prefix `EventEmitters` with `on` (as per Angular [guidelines](https://angular.io/guide/styleguide#dont-prefix-output-properties))
- Use past-participles i.e. the past tense of a verb, which often ends in `ed` in English
	- Use *click**ed*** instead of *click*.

### What are some naming conventions for the event handlers of your `@Output` properties ?
- A handler is a method that is called when the event is emitted that is generally stored in the parent component.
- This should have the same name as the `EventEmitter` but prefixed with the word `on`.
- For example, if the EventEmitter is called `messageSendSucceeded`, then the event handler should be called `onMessageSendSucceeded`.
```html
<app-email-form  
(messageSendSucceeded)="onMessageSendSucceeded($event)"  
(messageSendFailed)="onMessageSendFailed($event)"  
[email]="user.email"  
>  
</app-email-form>
```

### What lifecycle hook should be used for initialization logic for a `@ViewChild` property and why ?
- Use the `ngAfterViewInit` hook to write any component initialization code that uses the references injected by `@ViewChild`.
- Depending on the situation, the template references _might_ already be present on `ngOnInit()`, but we shouldn't count on it.
- This is because the View has not been rendered until this stage.

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
- The element to which the shadow root is attached is called the **shadow host**. The shadow host is part of the main document, and it serves as the entry point to the shadow tree.

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
### What is an Observable ?
- A data stream that can emit multiple values over time. Observables can be thought of as collections that arrive asynchronously.

### What is a Subject ?
- A special type of observable that allows multicasting to multiple observers. 
- Subjects act both as an observable and an observer, meaning they can emit new data to their subscribers as well as listen to other observables.

### What are different types of Subject ?
- **Subject**: 
	- Doesn't revive data prior to their subscription.
- **Behaviour Subject**: 
	- Emits last value to all & new observers.
- **Replay Subject**: 
	- All observers will revive data prior to their subscription; uses a buffer to hold values and re-emits values on new subscriptions.

### What is the difference between Cold and Hot Observables ?
- **Cold Observables** 
	- Only emit data once subscribed to;
- **Hot Observables** 
	- Emit values even before the subscription is made. Used when sharing data among many subscribers.

### What is a Subscription ?
- Represents the *execution* of an observable. 
- When an observer subscribes to an observable, the observable starts emitting values to the observer, and a subscription is created. 
- You can use the subscription to *cancel the data stream* if needed.

### How are Observables different from Promises ?
###### Observables:
- Handle multiple values over time, support lazy execution, provide cancellation, and have a rich set of operators for data manipulation. 
- They are particularly useful in scenarios with continuous data streams and complex asynchronous operations.
###### Promises:
- Handle a single future value or error, start execution immediately, do not support cancellation directly, and offer basic chaining methods. 
- They are suitable for simple asynchronous tasks that produce a single result.

### What is RxJS ?
- Reactive Extensions for JavaScript
- A library for composing asynchronous and event-based programs using observable sequences.
- A powerful tool for managing complex data flows in JavaScript applications, especially when dealing with asynchronous operations like HTTP requests, user input events, or real-time data streams.

### What are Operators ?
- RxJS functions that enable the transformation, combination, and manipulation of observable data.

### What is an RxJS Stream ?
- Am RxJS stream is a sequence of data elements made available over time.
- It is called a *stream* because it acts as a data that is continuous and not really having an end, unless you explicitly define an end.
- A stream can emit three different things:
	- A value
	- An error
	- A "completed" signal

### What are the advantages of using RxJS ?
- Library of operators or functions
- Much easier to deal with asynchronous programming than Promises

### What is a disadvantage of RxJS ?
- Debugging can be difficult

------------------------------------------------------------------------

------------------------------------------------------------------------
# Questions: Forms

### What are Template forms ?
- ???

### What are Reactive forms ?
- ???

### How does ControlValueAccessor keep the HTML template and component in sync for a FormControl ?
- ???

------------------------------------------------------------------------
# Questions: Modules
### How are eagerly and lazy-loaded child modules processed during the build phase ?
- Modules do not have a hierarchy or tree structure like components do.
- The providers of all eagerly loaded modules are merged into the root injector at compile time.
- This is a flattening of all the providers and [[entryComponents]] arrays that can be reached by following the `NgModule.imports` recursively (explained further [[Eager Flattening|here]]).
- However, a lazy loaded module creates it's own `ModuleInjector` that then becomes the child injector of the root injector.

------------------------------------------------------------------------
# Questions: Optimizations
### How can you optimize a `for` loop in a View template ?
###### Tracking
- Using tracking with the `trackBy` function
- Allows Angular to identify which items have been changed, added or removed.
- Only those items are re-rendered rather than the entire list.
###### Lazy Loading / Virtual Scrolling
- Using the `cdk-virtual-scroll-viewport` functionality from Angular material
- Only render items that are visible in the viewport.

### Why should you avoid calling functions from the View template ?
- Executed on every change detection cycle because no caching is happening and thus the View doesn't know what the current value is.

#### Why use `Renderer2` instead of just `ElementRef` ?
- The `Renderer2` class is an abstraction provided by Angular in the form of a service that allows to manipulate elements of your app without having to touch the DOM directly. 
- *This is the recommended approach because it then makes it easier to develop apps that can be rendered in environments that don’t have DOM access, like on the server, in a web worker or on native mobile.*
- Better to pass `ElementRef` into `Renderer2` and let `Renderer2` find the element.

------------------------------------------------------------------------
# Questions: Concepts Advanced
### What is the Ivy Compiler and what are some of it's benefits
[ChatGPT answer](https://chatgpt.com/c/66db4101-de80-8012-8ae8-9ccde6db2d41)
- New compiler introduced in Angular 9
- Designed to enhance performance, reduce bundle sizes, and make development easier.
- Some of the main improvements
	- AOT compilation
	- Smaller bundle sizes using [[Tree-shaking]]
	- Better debugging (more readable)
	- Faster Builds and rebuilds (compiles only what has changed)
	- Factories no longer required for creating dynamic components.

### How does the Ivy Compiler differ from ViewEngine ?
[ChatGPT Answer](https://chatgpt.com/c/66db4392-69c4-8012-ae37-10b7df0bfd58)
###### Performance
- Ivy has less memory footprint, faster rendering times and better overall runtime performance.
###### Code Generation
- ViewEngine generates more complex JavaScript code that is harder to optimize
- Ivy compiles more efficiently, producing much smaller more straightforward JavaScript code that is easier to optimize.
###### Tree-shaking Effectiveness
- ViewEngine is less effective at tree-shaking which results in larger bundle sizes.
###### Reflection vs Incremental DOM
- ViewEngine renders templates using a reflective system to modify the DOM
- Ivy uses Incremental DOM which directly updates the DOM in a way that only changing the parts of the view that need to be updated.
###### Better Debugging Experience
- ViewEngine is harder to debug because the generated code is less readable. 
- Ivy has a much better debugging experience with human-readable error messages, better stack traces and direct component interaction with components in the browser's development console.

### What is tree-shaking ?
- Tree-shaking in Angular is a build optimization technique used to remove unused or dead code from the final JavaScript bundle, making the application more lightweight and efficient. 
- This process analyzes the code, identifies modules, functions, or classes that are never used, and eliminates them from the final output. 
- As a result, the application's bundle size is reduced, improving performance, especially in terms of load time.
- [[Tree-shaking]]

### How can tree-shaking be utilized ?
- Use ES6 Modules
- Run `ng build --prod` which performs optimization functionality including tree-shaking.
- Use static imports and avoid dynamic imports
- Only import the RxJS operators you require.
- Use the `providedIn: 'root'` approach for services.

### How to enable tree-shaking for services ?
- To enable tree-shaking for services, you can use the `providedIn` metadata in the `@Injectable` decorator. 
- This tells Angular that the service should be tree-shaken if it's not used anywhere in the app.

### Why does tree-shaking not work for services defined in the `providers` array ?
[ChatGPT answer](https://chatgpt.com/c/66db49ae-c678-8012-9a44-48ecc329264f)
- The services listed in the `providers` array are eagerly instantiated, meaning that Angular creates an instance of them as soon as the component or module that provides them is loaded. 
- Since they are part of the dependency injection (DI) system, Angular can't safely remove them because it assumes they might be needed during runtime.
- Even if a provider isn't used in a component, Angular can't reliably infer that it won't be used somewhere else or injected into another part of the app, so it leaves it in the final bundle. 

### How does `providedIn` enable Tree-shaking ?
[ChatGPT answer (second question)](https://chatgpt.com/c/66db49ae-c678-8012-9a44-48ecc329264f)
- `providedIn` makes services tree-shakable because it allows Angular to treat them as *conditionally injectable*. 
- Instead of eagerly registering services in the global DI system (which can prevent tree-shaking), Angular can defer registering the service until it is actually used. 
- Angular can safely omit the service from the final JavaScript bundle during the build process (thanks to tree-shaking).

### What is transpiling ?
- Transpiling in Angular refers to the process of converting TypeScript code into JavaScript code that web browsers can execute.

### What is NgZone and why would you use it ?
[ChatGPT answer](https://chatgpt.com/c/66db562d-b99c-8012-b2e8-fb47f330c68d)
- NgZone is a service that Angular uses to manage the process of monitoring asynchronous tasks and triggering change detection. 
- By default, every asynchronous operation (such as setTimeout, HTTP requests, or button clicks) triggers a new change detection cycle, which can sometimes be unnecessary or inefficient.
- To improve performance (like animations, background computations, or external library calls), you might want to control when Angular should detect changes and update the DOM. This is where NgZone comes in handy—it gives you manual control over the context in which your code runs, and when Angular should update the UI.
- There are a number of methods provided by NgZone
```typescript
this.ngZone.run(() => {
  // This code will trigger Angular's change detection
  this.counter++;  // Angular will update the DOM after this
});
```
```typescript
this.ngZone.runOutsideAngular(() => {
  // This code will not trigger Angular's change detection
  setTimeout(() => {
    // Still won't trigger change detection until we re-enter Angular's zone
  }, 1000);
});
```

### What is an JIT compilation and where is it used ?
[ChatGPT answer](https://chatgpt.com/c/66db57e7-2090-8012-9cf0-8d49d0e6201c)
- A process where the Angular application is compiled in the browser during runtime. 
- This means that the Angular templates and components are compiled just before the application runs, rather than during the build process.
- JIT includes the Angular compiler code in the final bundle
- JIT compilation is generally used during the development phase due to it's faster development due to their being no pre-compilation step.

### What is an AOT compilation and what are it's advantages ?
[ChatGPT answer](https://chatgpt.com/c/66db58b5-2968-8012-98e0-0e4ebce0f5d6)
- A process where your Angular templates and code are compiled into efficient JavaScript code during the build phase, before the application is run in the browser.
- Here are some key benefits of AOT compilation:
	- **Faster Render Times**: Since the application is already compiled, it can render faster because there's less work for the browser to do.
	- **Smaller Angular Framework Size**: The AOT compiler removes Angular's compiler code from the final bundle, which reduces the size of the application.
	- **Early Error Detection**: Compilation errors are caught during the build phase rather than at runtime, which can help in catching errors early.

### What type of DOM does Angular implement ?
- Virtual DOM

### What is a bootstrapping module ?
- A bootstrapping module is responsible for starting the Angular application. 
- It’s essentially the entry point for the application and sets up the root module, which Angular uses to bootstrap or initialize the application.

------------------------------------------------------------------------
# Questions: Change Detection

### What is a `zone` in `Zone.js` ?
- A zone is essentially an execution context that can intercept asynchronous events (like HTTP responses or user inputs) and notify Angular that a change might have happened.
- Whenever something happens in the zone (like a click event or a timer firing), Angular schedules a change detection cycle to run.

### What is shallow comparison in JavaScript ?
- Refers to comparing two objects or values by checking if their *references* are the same, rather than checking if the values inside the objects are identical. 

### Explain the different change detection strategies in Angular ?
###### CheckAlways
- Traverses the component tree from top to bottom and checks each component to see if any changes need to be reflected in the UI.
###### OnPush
- Only check for changes in that component
- Only checks when one of the following occurs:
	- One of its input properties changes (using shallow comparison).
	- An event (like a click or an async operation) is triggered inside the component.
	- The component explicitly calls `markForCheck()` or `detectChanges()`.

### How would you optimize change detection ?
- Use `OnPush` with immutable data structures
	- Medium [article](https://medium.com/@connecttosurajpatil/angular-change-detection-immutable-data-structures-98bc402b6756)

### When is the `@Input` property setter method called ?
- Triggered when initially set or changes.

### What triggers a change detection cycle ?
###### User Input (DOM Events)
- Typically originate from the browser's native event listeners, like click, keyup, change, etc.
	- Clicking button
	- Typing into text input
	- Selecting a value
###### Timers
- Triggers when the operation finishes.
	- `setTimeout`
	- `setInterval`
	- `requestAnimation`
###### XHR / HTTP Requests
- When an XHR/HTTP request completes
###### Promises
- When a JavaScript Promise is resolved.
###### @Input Property Changes
- When a component receives new values through its `@Input()` properties.
###### Zone.js (NgZone)
- The `NgZone.run()` function is used to run a callback within Angular's zone.
- When it finishes executing the callback, `NgZone` triggers a change detection cycle.
###### Manual Change Detection Triggers
- Manual triggers via ChangeDetectorRef or ApplicationRef
###### Structural Directives
- When structural directives like **ngIf**, **ngFor**, or **ngSwitch** update the DOM, change detection is triggered.

### How does change detection know if a template expression or binding has changed ?
- During a change detection cycle, Angular compares the current value of a property or expression to its previous value to see if it has changed. 
- This comparison is done for:
	- Component input bindings
	- Template expressions and interpolation
	- Directives that rely on property bindings
- If Angular detects that a value has changed, it updates the DOM accordingly.

### How does Immutability fit in with change detection ?
- When using OnPush, Angular optimizes change detection by relying on the immutability of data. 
- *Angular only checks for changes in input properties if the reference to the object changes.* 
- If the data is mutated but the reference remains the same, Angular won't trigger a change. This encourages the use of immutable objects (e.g., replacing an array with a new one instead of mutating it) to ensure that Angular knows when a change has happened.

### What library does Angular use for change detection ?
- `Zone.js`
- Angular uses Zone.js to track asynchronous operations. 
- When any asynchronous task finishes (like a timer, an XHR request, or an event), the framework automatically runs change detection.

### What approaches can be used to manually trigger a change detection cycle ?
###### ApplicationRef.tick()
- Manually triggers a full change detection cycle across the entire application.
###### ChangeDetectorRef.detectChanges()
- Runs change detection manually for the current component and its children.
###### markForCheck()
- Marks the current component and its ancestors for a change detection check in the next cycle.
###### NgZone.run()
- A function used to execute callbacks in an Angular zone
- It triggers a change detection cycle upon completion.

### Why would you want to manually trigger a change detection cycle?
[ChatGPT Extensive Answer](https://chatgpt.com/c/66d9efca-c368-8012-96ae-0e9b3e8047a8)
- When working with third-party libraries or browser APIs that operate outside Angular’s zone (e.g., event listeners, WebSocket data streams, or external services), Angular’s default change detection won't be triggered by these changes.
- A child component using `ChangeDetectionStrategy.OnPush` receives data through an observable that does not update the `@Input()` directly. Manual triggering of change detection can ensure the child component reflects the updated data.
- In forms or search inputs where the data changes rapidly, you can delay change detection until the user stops typing for a period of time.
- If you’re listening for window scroll events and want to update some UI elements based on the scroll position, manually triggering change detection ensures the changes are reflected in the view.
- Running calculations that involve numerous intermediate steps where the UI should only be updated after the entire calculation is complete.
- When writing tests for components with `OnPush` change detection, you may need to explicitly call `fixture.detectChanges()` to ensure the component’s template updates.

------------------------------------------------------------------------
# Questions: Explainer

### How do you handle HTTP requests in Angular ?
- `HttpClient` module and class with method calls for `get`, `put`, `post`, `delete`
- Subscribe to the above methods
```
.subscribe( 
	data => { 
		console.log('Data received:', data); 
	}, 
	error => { 
		console.error('Error:', error); 
	}
)
```
- Catch errors with `pipe(catchError(this.handleError))`
- Other code [examples](https://chatgpt.com/c/66df135e-7894-8012-8a93-252d5e01ab95) here in second question

### How do you debug an Angular application ?
###### Chrome Dev Tools
- Inspect elements to see if they have rendered
- Check console for errors.
###### Augury
- Chrome extension that provides a visual representation of the component tree, services, routes, and more. It can help you:
	- View the state of components and their dependencies.
	- Track changes in Angular’s change detection cycle.
	- Understand how your routing works.
###### Debugging forms
- Inspect forms state using `formGroup.value` or `formGroup.status`
- Check for validation errors using `formGroup.get('controlName').errors`
###### RxJS
- Use `tap` operator to console.log values
###### Error handling with HTTP Interceptor
- Catch global errors and log them
###### Network tab for HTTP requests
- Inspect payload
###### Console.Log statements
- Not ideal but can help when other options are not available
- Have used this when deploying Angular app to a server

### How do you structure your Angular application ?
![[Pasted image 20240909164950.png|600]]
##### Core
- Loaded once and shared across the app e.g. authentication.
##### Shared
- Buttons , loaders
##### Environment
- environment.ts
- environment.prod.ts


------------------------------------------------------------------------
# Questions: Decision Making

### Why use lazy-loaded modules ?
###### Improved Initial Load Time
- The application loads only the essential parts during the initial page load.
###### Better User Experience
- Faster interaction times and reduce waiting periods.
###### Optimized Performance
- Reduced memory usage as modules are loaded as user navigates through the app.
###### Scalability
- Lazy loading allows you to scale your Angular app without significantly affecting the initial load performance, as unused modules won’t impact the startup time.

### How to share data between components ?
###### Parent-to-child
- `@Input` decorator
###### Child-to-parent
- `@Output` decorator and `EventEmitter`
###### Siblings
- Shared Service class
###### NgRX State Management
- For larger applications
- Manage state in a centralised store.
###### @ViewChild
- Rarely used
- Access child component and it's public properties
	- `@ViewChild(ChildComponent) child!: ChildComponent;`

### When to use Template vs Reactive Forms ?
==Push for case of template driven.
Talk about Ward Bell lecture==
==Some other talking points [[Angular/Forms/! Reddit|Angular Forms Reddit]]==
###### Template-driven forms: 
- Good for simpler forms where ease of use and minimal code are preferred.
###### Reactive forms: 
- Best for complex, dynamic, and highly customizable forms where you need more control and scalability.

### How do you deal with errors in observables?
- `catchError` operator can be used to handle and recover from errors. 
- This operator allows you to provide a fallback value or execute alternative logic like error handling.

### How do you reference an element from component code ?
- [[! NOTES (The Complete Guide - Udemy Course)#Template Reference|Template reference variables]] combined with @ViewChild and @ViewChildren directives. 
- Make sure to put any initialization code for the @ViewChild and @ViewChildren directives  inside ngAfterViewInit as explained [[! NOTES (The Complete Guide - Udemy Course)#`@ViewChild` and `ngAfterViewInit` hook.|here]].

### When to use `[class]` vs `[ngClass]` ?
- Use `[class]` to add only a single class conditionally.
```html
<div [class.has-error]="hasError"> </div>
<div [class.is-adult]="age >= 18 ? true : false"> </div>
```
- Use `[ngClass]` to add multiple classes conditionally.
```html
<div [ngClass]="{'error': hasError, 'warning': hasWarning}"> </div>
```

------------------------------------------------------------------------
# Questions: Coding Questions
### How do you implement routing in Angular ?
[ChatGPT](https://chatgpt.com/c/66e162e5-1c34-8012-bc97-b6ef1c75fa02)
- `<router-outlet></router-outlet>`
- Main routing module
- Feature router modules
	- `{ path: 'admin', loadChildren: () => import('./admin/admin.module').then(m => m.AdminModule) }`
- Navigate
	- `routerLink`
	- `this.router.navigate(['/contact'])`
- Sending Parameters
	- Use array
- Handling parameters
	- `this.route.snapshot.paramMap.get('id')`
	- `@Input` set properties

### How would you invalidate a user's session and redirect them to login ?
[ChatGPT Answer](https://chatgpt.com/c/66e2a200-83cc-8012-86ba-c18b57b00905)
1. Clear user session (e.g., remove the token).
2. Use Router to redirect the user to the login page.
3. Optionally, handle session expiration with an HTTP interceptor to automatically redirect when a token becomes invalid.

###  RXJS question to combine the data from 2 observables into a different formatted data as an observable
[ChatGPT Answer](https://chatgpt.com/c/66e2a2de-8588-8012-b574-0b5adb4b58d6)
- combineLatest
- forkJoin
- zip

------------------------------------------------------------------------
# Questions: Experience
### What is your favourite feature of Angular ?
- Typescript
	- Type safety
- RxJS
	- Cleaner way to handle streams than Promises
- The structure it enforces on you.
	- Opinionated framework which is particularly good for team based environments.
- The CLI
	- Tooling used to quickly create project components, modules, services, pipes, etc.

### What is your least favourite feature of Angular ?
- It was modules but something but standalone components has solved this
	- Made the learning curve steeper IMO
- Recently, I still think the way Reactive Forms are done could be improved
	- Boilerplate code.
- Can't use ngIf and ngFor on the same element.

### What project are you most proud of ?
- Implementation of a simple relation database using the C programming language.
- Athora upgraded project.

### What is the most complex feature you have built ?
- InputsGrid
	- Cell based grid
	- Insurance product at top
	- Inputs on the left
	- Select one or more cells and apply the same update
	- Had color coding for cells that had the same input.
	- Highlight entire row.
	- ==Wasn't the complexity that I was proud off, it's what it solved.==
- The RunGroup comparer
	- Team found this very useful.

### What are some ways you have used RxJS ?
[ChatGPT source](https://chatgpt.com/c/612a9b5a-de9f-496e-9621-cd40bf6bfea3)
- Forms
	- debounce
	- distinct
	- filter (minimum character length)
	- combineLatest()
		- Can enable Submit button if username and password filled in
- Toasters
	- timers (for fading away)
- Transformation
	- map()
- HTTP Requests
	- switchMap()
	- mergeMap()
		- Make multiple side-by-side requests and merge the output of each request
	- share()
- Error handling
	- retry()
	- catchError()


