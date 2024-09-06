# Definitions
- *"A sub type should behave like a super type as far as you can tell by using the super type method"* - Barbara Liskov
- Objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program.
- If it talks like a duck and quacks like a duck but it needs batteries than it's probably not a duck.
- The `IS-A` relationship is insufficient and should be replaced with `IS-SUBSTITUTABLE-FOR`.

# Purpose
- This principle ensures that a subclass can stand in for its superclass and behave in the same way without altering the desirable properties of the program e.g., correctness, task completion. Example [here](https://youtu.be/kF7rQmSRlq0?t=229)

# Violation Examples
- This Pluralsight [video](https://app.pluralsight.com/ilx/video-courses/c0ed5511-3776-457e-b06a-259fbb2144f7/e795d116-ff98-4784-88ce-ea8fbd4cf083/cd2c7a0c-fae2-4990-86ce-2038ed46e893)
	- Trying to make a Square class inherit from a Rectangle class
	- Square has all equal sides, Rectangle can have two unequal sides
	- A Square instance might be used in a method that takes a Rectangle instance and incorrect behaviour will emerge.
	- Solution is too separate the two classes with no connection between them.

# Implementation
### Reconsider the Class Hierarchy
- Using the example video linked above, we would create a Human base class that has common behaviour between an Adult and Child. Both Adult and Child would inherit from this Human class.
### Covariance and Contravariance
- Covariance and contravariance are crucial for the LSP, which states that objects of a superclass should be replaceable with objects of a subclass without altering the correctness of the program. They ensure that subclass types can be substituted in a way that maintains the integrity of method signatures and behavior.