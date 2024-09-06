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