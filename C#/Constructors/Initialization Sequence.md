There are several actions that are part of initialising a new instance. Those actions take place in the following order:

1.  **Instance fields are set to 0**
	- This is typically done by the runtime.
2.  **Field initializers run** 
	- The field initializers in the most derived type run.
3.  **Base type field initializers run**
	- Field initializers starting with the direct base through each base type to **System.Object**.
4.  **Base instance constructors run** 
	- Any instance constructors, starting with **Object.Object** through each base class to the direct base class.
5.  **The instance constructor runs**
	- The instance constructor for the type runs.
6.  **Object initializers run**
	- If the expression includes any object initializers, those run after the instance constructor runs. Object initializers run in the textual order.