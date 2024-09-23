# Definitions
- Each software module should have one and only one reason to change.
- It does not mean your class should do one job or thing, it means everything it does should be very closely related

# Purpose
- Bugs
	- The more responsibilities your class has, the more likely a bug will be introduced when a change in that class is required.
- Merge Conflicts
	- Avoids too many people working on the same file in the repository thus causing merge conflicts. 

# What is a Responsibility ?
#### Overview
- It's a decision our code is making about the specific implementation details of some part of what the application does.
- *A responsibility in your code represent things that may change at different times and for different reasons.*
#### How Something is Done
- It's the answer to the question of how something is done
- Some examples of responsibility:
	- Persistence
		- Is the class using files, database, Web API?
	- Logging 
		- Is there a particular framework being used
	- Validation
		- How is input to the system validated 
	- Business Logic
- Mixed into the above are the business rules that define how the system should behave from the stakeholders perspective.
	- They don't care about the low level details of how files are stored or logs are written but they care that the system models the business problem effectively.
#### Axes of Change
- Each responsibility is an **axes of change**
- The potential *sources of changes* to your application can help identify when you might be violating SRP
- Think about *where change requests may originate* in terms of different executives within a large company:
	- **CIO/CTO** may require a change to persistence because of a company wide change in database vendors
	- **Security Officer** may require a more robust logging framework installed to help detect and protect against attackers 
	- **COO** requires update to validation rules to integrate effectively with the companies newly acquired subsidiary.
	- **Marketing** announced a special offering and now the price calculations that your business rules model need to account for this new offer.

# SRP Violation
[ChatGPT Source](https://chatgpt.com/c/66db62d5-18ac-8012-9d22-05f8a754dc07)
##### Large Class: 
The class has a large number of methods and/or properties, making it complex and difficult to understand.
##### Large Methods: 
The class has large methods that handle multiple tasks, rather than being broken down into smaller, focused methods.
##### High Coupling: 
The class is tightly coupled with many other classes, meaning that changes in one part of the system can have unintended effects on the class.
##### Frequent Changes: 
The class changes frequently for different reasons, indicating that it might be handling multiple aspects of the system.
##### Difficult to Test: 
The class is hard to test in isolation because it deals with many different concerns.

# Implementation
#### Class Breakdown
- Break down the large class into smaller classes, each handling a single responsibility.
#### Method Breakdown: 
- Large methods should be broken down into smaller, more focused methods.
- Ensure that each method in the class has a single, well-defined purpose. 
#### Delegate Responsibilities: 
- Delegate some of the responsibilities to other specialized classes or objects.
#### Interfaces
- Define interfaces for different responsibilities and implement these interfaces in separate classes. This can help in maintaining a clear separation of concerns.