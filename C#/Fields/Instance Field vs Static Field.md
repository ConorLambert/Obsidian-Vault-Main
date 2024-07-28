A class or struct may have instance fields, static fields, or both. 

### Instance Field
- Instance fields are specific to an instance of a type. 
- If you have a class T, with an instance field F, you can create two objects of type T, and modify the value of F in each object without affecting the value in the other object. 

### Static Field
- A static field belongs to the type itself, and is shared among all instances of that type. 
- You can access the static field only by using the type name. 
- Static fields are available to callers at any time, *even if no instance of the type exists*.