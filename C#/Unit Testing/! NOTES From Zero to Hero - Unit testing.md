[Source](https://courses.dometrain.com/courses/take/from-zero-to-hero-unit-testing-for-csharp-developers)

# Unit testing fundamentals
### The 3 core unit testing concepts
- Testing library
	- Runs the tests
	- xUnit
	- nUnit
	- MSTest
- Mocking library
	- Helps mock any dependencies
	- Moq 
	- NSubstitute
	- Fakeiteasy
- Asserting library
	- Validate the actual outcome and the asserted outcome match
	- Fluent Assertions
	- Shouldly
	- Also ones built into testing libraries.

### Why xUnit ?
- Most popular
- Built by makers of nUnit
- Used by Microsoft

### Writing your first Unit Test
- The `[Fact]` attribute makes your unit test method discoverable by xUnit.

### Structuring your solution
- The idea is to create a test project for other projects in the solution
- Therefore, avoid combining test projects alongside solution projects in the same folder.
- Create two folders, `src` and `test`
- All source including the solution file should be placed in `src`
- All testing code should be placed in `test`

### Naming in Unit Tests
- Testing project
	- *NameOfProjectUnderTest*.Tests.*TypeOfTest*
	- Examples 
		- CalculationLibrary.Tests.Unit
		- CalculationLibrary.Tests.Integration
- Testing class
	- *NameOfClassUnderTest*Tests
	- Examples
		- CalculatorTests
- Testing method
	- *MethodUnderTest*`_`Should*WhateverItShouldDo*`_`When*WhenSomeStateIsTrue*
	- Examples
		- Add_ShouldAddTwoNumbers_WhenTwoNumbersAreIntegers()
-  The above makes it easier to read things at a glance

### Arrange, Act, Assert
- Might not have Arrange (could be built in unit test class constructor)
- Act and Asset are sometimes combined together

### xUnit's test execution model
- Every test scope is self-contained.
- No global variables are shared
- Any global variables that are initialized outside of the unit test methods (e.g. constructor) will be re-initialized for every unit test.

### Test Setup and Teardown
- Setup
	- Done in unit test class `constructor`.
- Teardown (Cleanup)
	- Implement `IDisposable` interface on unit test class.
- *Setup and Teardown is called for each unit test method*
- What if you need `async` code in your Startup and Teardown
	- Implement `IAsyncLifetime` interface instead if `IDisposable`.
	- Contains `InitializeAsync` and `DisposeAsync` methods
	- InitializeAsync is similar to constructor *but is called after the constructor*.

### Parameterising tests
- You could have many unit test methods where only the parameter to the method under test is different
- We can combine them all into one method that is parameterised.
- Replace `[Fact]` attribute with the `[Theory]` attribute and a series of `[InlineData()]` attributes each representing a different parameter list.
	![[Pasted image 20240904212356.png|400]]

### Ignoring Tests
- Use the `Fact` attribute with the `Skip` parameter like so
	- `[Fact(Skip="Ignore this for now")]`
- Same works for `[Theory]` attribute
	- `[Theory(Skip="This breaks in CI")]`
- Can also skip an individual parameterised test with the `[InlineData]` attribute
	- `[InlineData(Skip="Ignore this for now")]`

# Unit testing techniques
### Writing fluent assertions
- Assertions used for the default Assert class are not very readable.
- Using `Fluent Assertions` or `Shouldly` gives us more readable assertions and better error messages when failures occur.
- An example of the functionality Fluent Assertions provides for testing numbers:
![[Pasted image 20240906221530.png]]

### Testing objects
- Use the following method in `Fluent Assertions` to compare objects by its properties:
	- `user.Should().BeEquivalentTo(expected)`

### Testing enumerables
- Check if *value* is contained within a collection:
	- `users.Should().Contain(expected);`
- Check if an *object* is contained within a collection
	- `users.Should().ContainEquivalentOf(expected);`

### Testing methods that throw exceptions
- Because an exception will be thrown at the `Act` stage, we need to wrap the call into an `Action` like so:
![[Pasted image 20240909184350.png|400]]
- Can further filter what exception to catch by using `WithMessage` and other methods.

### Testing private methods
- Private methods are tested when called by `public` or `internal` methods.
- *Don't change private method to public just to test them.*

### Testing internal methods
- Should absolutely be tested as if it where public.
- Need to make it available to Unit Test project.
- Old way
	- Using `InternalsVisibleTo` in a different class in the assembly to be tested
	- Not recommended
- New way
	- Using `InternalsVisibleTo` in the `csproj`.

# Unit Testing Concepts
### What are fakes?
- Create a class that implements the interface of the type you want to fake.
- The problem with fakes is the returned data is the same for every test that uses it.
- We would have to create a fake class for every use case of data we need to return.

### What is mocking?
- No new class required.
- Create one mock instance variable and pass it into the class under test.
- We can simulate what data is returned for every unit test individually that uses a method of the mocked type.
- Steps
	- Create mock reference of interface or abstract class.
	- Pass the mock into class constructor under test.
	- Mock out data returned from any method within the mocked class.

### Moq vs NSubstitute
- Most top engineers use NSubstitute
- Moq more convoluted 
	- Problematic when dealing with larger applications
- NSubstitute has cleaner more readable code.

# Unit testing in the real world
### The scope of our testing
- We need to be very selective with our testing
- No point in testing the Data Layer
	- This is more of an integration test
	- We will me mocking our data layer so no point in testing it
- Application layer
	- Correct path is taken
		- User data is returned correctly for example
	- Might want to check of Logging is done correctly
- Testing API controllers
	- We want to test if the mapping responses are correct.
	- API action returns appropriately (Found, NotFound)
	- Some say it should be integration

### Testing the application layer
- Testing static and extension methods is really hard.
- Testing logging is difficult.
	- [ChatGPT answer](https://chatgpt.com/c/66e2e423-68ec-8012-bd9e-8536e6cbf293) explains why
	- Workaround is to create an adapter
	- *The adapter will be used the service code in place of the logging class.*
	- For a how to just follow on from 10:23 seconds in Nick Chapsas [video](https://courses.dometrain.com/courses/take/from-zero-to-hero-unit-testing-for-csharp-developers/lessons/53927162-testing-the-application-layer)
- Use `Arg.Is` API to check if argument with that value is passed in.
	- Can extend this by checking argument startsWith
	- Used in conjunction with `Received` method.
- Testing exceptions
	- We can get a method to throw an exception with `Throws`
		- Done in the arrange phase of the test
	- When the enclosing method that we are testing is called under the Act phase, we know that an exception will be thrown.
	- Then use `ThrowAsync`
	- ![[Pasted image 20240911114302.png|400]]

### Exercise: Testing the Application layer
- Use `ReturnsNull` and `Arg.Any<Guid>()` for testing if a method should return null
![[Pasted image 20240916163817.png|400]]
- For tests where we don't care about any particular user information, then just use `Arg.Any<Guid>()` as parameter call. We don't need to setup a user object.

### Testing the API layer
- Not common but recommends you should have them
- Test mapping and response codes
- Make sure to cast `// Act` stage to status code related type e.g. `OkObjectResult` for `Ok()` or `NotFoundResult` for `NotFound()` 

### Exercise: Testing the rest of the API layer
- `Create` is a bit tricky due to the auto generated Guid inside the method under test which mismatches the Guid that is generated during our `// Arrange` section of our unit test code.
- Nicks workaround is to use `Arg.Do<User>` like so at the `// Arrange` stage
	- `_userService.CreateAsync(Arg.Do<User>(x => user = x)).Returns(true);`
- This forces our local `user` object inside the unit test to match the `user` object created inside the `CreateAsync` method under test.
- Also make sure to move the following line down to the `// Assert` stage
	- `var userResponse = user.ToUserResponse();`
- We can also test the route values returned from the `Create` methods `CreatedAtAction` using the following syntax (notice the exclamation):
	- `result.RouteValues!["id"].Should().BeEquivalentTo(user.Id)`

# Advanced Unit Testing Techniques
### Observing the default test execution
- Each test of a test class will run in series and in no particular order.
- Each test also has it's own instance of the class it's contained within.

### Class Fixture
- What if we want the code of a test class to be shared amongst it's test methods ?
- Handy if you need to spin up database instances. Don't want to do it for every test method.
- Create a separate fixture class (which is just a normal class)
- Then in your test class, you implement the `IClassFixture<T>` interface where `T` is the name of the fixture class created in the previous step:
![[Pasted image 20240918213925.png|400]]
- The constructor of the fixture class will be called only once
- You could also implement `IDisposable` on the fixture class to cleanup any code.
- The constructor of the fixture is called before the first call to the constructor of the test class.
- Dispose is only called after all tests of test class in question have finished.
- Very common to use Class Fixtures (Db connections, docker, etc)

### Collection Fixture
- Class Fixture used for one class
- What if we want to share state amongst multiple classes
- Create a sort of marker class that implements `ICollectionFixture<T>` interface where T is the class fixture (same as Class fixture approach)
- This marker class should also have a `CollectionDefinition` attribute with a title of your choice.
	- The title is important because we will use that title to mark any test class that we wish to share the Class Fixture data amongst.
![[Pasted image 20240918215507.png|400]]
- Any test class that we want to share the data should have the `Collection` attribute declared with the unique title we gave the which in our case is "*My awesome collection fixture*".
- We still inject the `MyClassFixture` into the test classes.
![[Pasted image 20240918215817.png|400]]

### Running test in parallel
- Tests within a collection will run one after the other
- Tests in a separate collection will run in parallel.
- You can disable this like so: 
![[Pasted image 20240918220334.png|400]]
- Can also be applied at the ICollectionFixture level
![[Pasted image 20240918220446.png|400]]

### Advanced parameterization
- Avoid clunky `[InlineData]` attributes
- Declare the parameters in an array and reference through the `[MemberData]` attribute instead.
- Can also use the `[ClassData]` attribute and put the parameter data behind a class instead of a local variable. The class will implement the `IEnumerable` interface and thus the `GetEnumerator` method.
	- This approach is good for dynamic creation of data.

### Testing Date and Time
- Testing methods that use Dates related to current date and time.
- Solution is to implement an interface that declares a DateTime object and mock as shown in the [video](https://courses.dometrain.com/courses/take/from-zero-to-hero-unit-testing-for-csharp-developers/lessons/53927203-testing-date-and-time)

### Continuous Testing
- Tests are automatically run after you make a change in your tests.
- Can be annoying so not exactly recommended.

### Measuring code coverage ?
- Can use tooling that is not part of IDE
	- Handy if we want to use it as part of CI
- Dotnet specific tool called `coverlet.console`
- Run `coverlet` targeting the unit test `.dll`.
- We can exclude a class fro coverage by using the `[ExcludeFromCoverage]`.
	- Don't want to litter our code with this though
- Can instead declare what namespaces we want to exclude through the `coverlet.console`.
- We can generate code coverage report
	- Use a tool called `reportgenerator`
