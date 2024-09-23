# Single Responsibility Principle (SRP)
### What is the Single Responsibility Principle ?
[[SRP Explained#Definitions|Definitions]]

### +++ What exactly is a Responsibility ?
[[SRP Explained#What is a Responsibility ?|What is a Responsibility]]
- How something is done
	- Logging
	- Persistence
	- Validation
- Things that may change at different times and for different reasons.
- [[SRP Explained#Axes of Change|Axes of Change]]
	- Source of changes

### +++ How can you determine if a class has multiple responsibilities ?
[[SRP Explained#SRP Violation|SRP Violations]]

### Can you provide an example of a class that violates SRP ?
- A class that contains most if not all of the following
	- Validation
	- Logging
	- Persistence
	- I/O
	- Displaying

### Can you provide an example of a class that violated SRP in Athora ?
- CreateRunGroup
- Broke it down into classes that done the following
	- Setup Inputs
	- Created actions based on inputs
	- etc

### Why is it important for a class to adhere to SRP ?
[[SRP Explained#Purpose|Purpose]]

### How can you resolve issues around SRP ?
[[SRP Explained#Implementation|Implementation]]

# Open/Closed Principle (OCP)
### What does the Open/Closed Principle state ?
[[Open-Closed Principle Explained#Definition|Definition]]

### How to detect if a class has violated the Open/Closed principle ?
[[Open-Closed Principle Explained#Violations|Violations]]

### How can you apply the Open/Closed Principle in a real-world application ?
[[Open-Closed Principle Explained#Implementation|Implementation]]

### Can you provide an example of a class that violates the Open/Closed principle ?
- Suppose you have a Report class that generates reports in different formats. If the class has a method generatePDFReport() and you need to add support for generateHTMLReport(), a violation of OCP would be if you modify the Report class to include logic for HTML reports directly. Instead, a design adhering to OCP would use an abstract ReportGenerator class with a method generateReport(), and you would create subclasses like PDFReportGenerator and HTMLReportGenerator that extend the ReportGenerator class.

# Liskov Substitution Principle (LSP)
### What is the Liskov Substitution Principle ?
[[Liskov Substitution Principle (LSP)#Definitions]]

### Why is the Liskov Substitution Principle important in inheritance ?
[[Liskov Substitution Principle (LSP)#Purpose|Purpose]]

### Can you provide an example of a situation where a subclass violates the Liskov Substitution Principle ?
- [[Liskov Substitution Principle (LSP)#Violation Examples|Violation Examples]]
- [[Detecting LSP Violations]]

### What are Preconditions and Postconditions and why are they important for LSP ?
- [[Preconditions and Postconditions#Overview|Overview]]
- [[Preconditions and Postconditions#In the Context LSP|In the Context LSP]]

### How can you ensure that subclasses adhere to the Liskov Substitution Principle ?
- Ensuring the subclass does not have stricter preconditions or weaker postconditions 
- [[Preconditions and Postconditions#In the Context LSP|In the Context LSP]]

# Interface Segregation Principle (ISP)
### What is the Interface Segregation Principle ?
[[Interface Segregation Explained]]

### Why should an interface be segregated into smaller, more specific interfaces ?
[[Interface Segregation Explained#Purpose|Purpose]]

### Can you provide an example of a class that violates ISP and how to refactor it ?
- Unit of Work that Entity Framework uses
- [[Interface Segregation Explained#Violations|Violations]]
- [[Interface Segregation Explained#Implementation|Implementation]]

# Dependency Inversion Principle (DIP)
### What does the Dependency Inversion Principle entail ?
[[Dependency Inversion Explained#Definitions|Definitions]]

### What are some violations of DI ?
[[Dependency Inversion Explained#Violations|Violations]]

### How can you achieve dependency inversion in a software system ?
- Use Interfaces in conjunction with a Dependency Injection container framework.

### What are the benefits of using dependency injection to adhere to the Dependency Inversion Principle ?
- Mocking Unit Tests.
- Changes in dependency class would not require changes in the dependent class.
