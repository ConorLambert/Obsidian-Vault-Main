# Definition
- *"Open to extension but closed to modification"*

# Purpose
- All the unit tests you wrote for a class would break
- Adding additional functionality into existing methods may cause unintended consequences.

# Violations
[ChatGPT answer](https://chatgpt.com/c/66db64a6-4c1c-8012-8bad-ed089e6b252b)
##### Frequent Changes to Existing Code: 
If you find yourself frequently modifying an existing class to add new functionality, it’s a sign that the class may not be adhering to OCP. Ideally, you should be able to extend or enhance behavior through new classes or methods without altering existing code.
##### Large or Complex Classes: 
Classes that handle too many responsibilities or have complex logic might be a sign that they are not designed with OCP in mind. These classes often need modification when new features are added.
##### Hardcoded Behavior: 
When a class includes hardcoded logic that would need to be altered to accommodate new requirements, it suggests a violation of OCP. A class should be designed in such a way that new behavior can be added by extending the class or using polymorphism rather than altering the class itself.
##### Lack of Abstraction: 
Classes that lack abstract interfaces or base classes might indicate a violation. Proper abstraction allows new functionality to be added through new derived classes rather than modifying existing code.

# Implementation
### Decorator Pattern (and Dependency Injection)
- ???
- Can switch at runtime to decide if and when the code is used.
### Extension Methods
- Add method to existing class without changing the file
### Inheritance
- ???
### Attributes
- ???
### Covariance and Contravariance
- Covariance and contravariance can help in adhering to the OCP, which states that software entities should be open for extension but closed for modification. By allowing methods to accept or return different types in a compatible way, you can extend classes and methods without changing their existing behavior.