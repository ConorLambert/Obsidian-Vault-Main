[Source](https://app.pluralsight.com/library/courses/angular--unit-testing/table-of-contents)

# Introduction to Unit Testing in Angular

### Testing Overview
- Angular Integration Tests
	- Special type of Angular test
	- Test component and template

### Mocking
- Types of mocks
	- Dummies
		- We just need it to exist and not do anything
	- Stubs
		- Return a value when called
	- Spies
		- How many times its called
		- What parameters where used when called
	- True Mocks
		- Tell exactly what calls you expect to have happened against it and then it will tell you whether or not those calls happened.

### Unit Tests in Angular
- Isolated
	- Test piece of code like component, pipe, service
	- We construct it by hand, giving it it's parameters, etc
- Integration
	- Same as isolated but use special tooling call `TestBed`
	- `TestBed` allows to use component and template together
	- Type of Integration tests
		- Shallow tests are for single component and it's template
		- Deep tests for when a component has children and we can test the component and it's children.

### Tools
- Unit Testing
	- Karma
	- Jasmine
	- Jest
		- Started out in React
	- Web Test Runner
		- Becoming the default unit testing tool for Angular
- End to End Testing
	- Cypress, Playwright, Selenium & WebDriver

### Writing Good Unit Tests
- Structure your tests (Arrange, Act, Assert)
- DAMP vs DRY
	- With unit tests, we don't want to fully remove duplication
	- We will often repeat ourselves in our tests
	- DAMP: Repeat yourself if necessary
	- You shouldn't need to look around much to understand the test
	- Keep critical setup within it
		- Whatever is important to understand about the test
	- Move less interesting setup into beforeEach

# Shallow Integration Tests
### Debugging Techniques with Angular and Karma
- Always have console window open of browser window that is displaying Karma
- Some errors only show up there.

### The TestBed
- `TestBed` is used to create a testing module that is setup similarly to an NgModule in that it declares the component under test in it's `declarations` array on any services or other directives that the component uses.
- `ComponentFixture` is wrapper around a component that has a few additional members related to functionality.
- One such member is `componentInstance` which is the component itself. We can access any public members of the component including any `@Input` and `@Output` properties.
- Another important member is `detectChanges()` which triggers change detection and updates any data bindings.

### Testing Rendered HTML
- `fixture.nativeElement.querySelector('a').textContent`
- Most functionality to access rendered HTML is native JavaScript functionality.

### nativeElement vs debugElement
[ChatGPT answer](https://chatgpt.com/c/66ee0944-9140-8012-8614-d67be3a204e0)
- `nativeElement` exposes the underlying DOM API
- `debugElement` wraps the native DOM element. It is helpful for testing Angular-specific functionality, such as components and directives.
- For example, `debugElement` has extra functionality used to access specific things like `routerLink` directives etc or even back to the component instance.

### Mocking an Injected Service
- `TestBed.configureTestingModule` has a providers array that we can inject a mock using the `provide` and `useValue` constructs:
	`providers: [{provide: HeroService, useValue:mockHeroService}]`
- We can mock the service using the following:
		`mockHeroService = jasmine.createSpyObj(['getHeroes','addHereos','deleteHero'])`

### Mocking Child Components
- Create a component that will be a mock component inside the test class and add it to `declarations` array of `TestBed.configureTestingModule()`.
- The component name can be different than the component being mocked but it must have the same selector.
- Make sure to remove `export` from component declaration.

### Dealing with Lists of Elements
- `<ul>` lists or `ngFor` loops can be tested using the following:
	`fixture.debugElement.queryAll(By.css('li')).length).toBe(3)`