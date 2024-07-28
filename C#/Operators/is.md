---
	tags: is, operator, boolean, casting
---

#### Overview
- The `is` operator is used for checking if the run-time type of an object is compatible with a given type or not. 
- The result of the validation will return a boolean value (true or false)
- The is operator never throws an exception.

#### Code Example
```csharp
Person person = new Person();
Boolean b1 = (person is Person); // this will return true;
Boolean b2 = (person is Employee); // this will return false;
```

#### Internals
- The `is` operator uses a cast to make its determination.