# Overview
- Concepts that help ensure that objects or functions behave correctly when inherited or substituted.
- Particularly related to the [[Liskov Substitution Principle (LSP)]]

# Preconditions
- Conditions or requirements that must be true before a function or method is executed. 
- They specify the assumptions or constraints that must be satisfied for the method to work correctly.
- For example, if a method requires a non-null object as an argument, the precondition would be that the argument must not be null.

# Postconditions
- Conditions that must be true after a function or method has been executed. 
- They define the expected state of the system after the operation is completed.
- If a method is supposed to add an item to a list, a postcondition might be that the size of the list has increased by one.

# In the Context LSP
By adhering to these preconditions and postconditions, you ensure that derived classes can be used interchangeably with their base classes, maintaining the integrity of the application.
##### Preconditions
- Preconditions in a derived class should not be stricter than those in the base class. 
- If a base class method expects an argument to be non-null, a derived class method should not require that argument to be of a specific type or have a specific value. 
- The derived class must maintain or weaken the precondition.
##### Postconditions
- Postconditions in a derived class should not be weaker than those in the base class. 
- If a base class method guarantees that a list size will increase after adding an element, the derived class method should also ensure this guarantee or provide an even stronger guarantee (e.g., the list is sorted after adding the element).