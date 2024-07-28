## References
- https://www.bytehide.com/blog/private-constructor-csharp


## Overview
- A private constructor is a special instance constructor. It is generally used in classes that contain static members only.
- If a class has one or more private constructors and no public constructors, other classes (except nested classes) cannot create instances of this class.
- Note that if you do not use an access modifier with the constructor it will still be private by default.


## Private Constructors & Inheritance
- A class that has a private *default* constructor cannot be inherited.
- However, if an overloaded constructor and not the default constructor is made private then inheritance is allowed but that overloaded constructor cannot be used in the derived class.


## Private Constructor Use Cases
##### Enforce Overloaded Constructor Creation
- You don’t want to allow anyone to create an object of a class with an empty constructor but all other overloaded constructors. Then, you can make the empty constructor private and rest of the constructors public. 

##### Use a Singleton Class
- The [[singleton design pattern]] ensures that a class can only have one instance and provides a global point of access to that instance. This is useful when you want to centralise access to resources or services, such as configuration settings or database connections.

##### Preventing Object Instantiation
- Sometimes, you may have a class with only static members, and there is no need to create instances of that class. By using a private constructor, you can prevent object instantiation, forcing the use of static members only.

##### Limit Instance Count
- Similar to the `Singleton` example but allow for more then one instance.


## Private Constructor vs Static Classes
- If you need a class that cannot be instantiated use a `static` class. Only use a `private` constructor instead of a `static` class if you need to initialise static members (or a singleton pattern).

