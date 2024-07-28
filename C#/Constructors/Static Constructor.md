#### Overview
- A static constructor is used to initialise any static data, or to perform a particular action that needs to be performed only once.
- It is called automatically before the first instance is created or any static members are referenced. 
- A static constructor will be called at most once.

#### Initialisation Sequence
- Same [[Initialization Sequence|sequence]] as an instance constructor except there is no `Object Initializers run` (step 6).

#### Use Cases
- The class is using a log file and the constructor is used to write entries to this file.
- Creating wrapper classes for unmanaged code. Here the constructor can call the **LoadLibrary** method.
- Enforce run-time checks on the type parameter that cannot be checked at compile time via type-parameter constraints.
