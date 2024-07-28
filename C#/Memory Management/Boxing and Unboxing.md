## Boxing
- Boxing a value type allocates an object instance on the heap and copies the value into the new object.
- Hence the name “boxing”, you are creating a box (an object) then storing something (a value) inside of it
- Boxing is **implicit** (compiler does it for us)

```csharp
int i = 123;
object o = i;  // boxing
```

![[Pasted image 20230927194031.png]]


## Unboxing
- Unboxing is an **explicit** conversion from the type `Object` to a `Value Type` or from an Interface type to a value type that implements the interface. An unboxing operation consists of:
	1. Checking the object instance to make sure that it is a boxed value of the given value type.
		- For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.
	2. Copying the value from the instance into the value-type variable.
	
```csharp
int i = 123;
object o = i;  // boxing
i = (int)o;    // unboxing
```

![[Pasted image 20230927194108.png]]


## Examples

##### Reflection
- The .NET framework's reflection API makes heavy use of Object.

##### Integer to Object
```csharp
int i = 123;
object o = i;  // boxing
i = (int)o;    // unboxing
```

##### String Concatenation
- Concatenating a value type to a string using the `+` operator:
```csharp
int salary = 2000;
string text = "Salary is " + salary;
```
- `salary` gets boxed into an object.
- To avoid boxing from happening here, manually call the `ToString()` method on `salary`:
```csharp
int salary = 2000;
string text = "Salary is " + salary;
```

##### String Interpolation
- Introduced in C# 6.0, it makes use of the **String.Format** functionality:
```csharp
int salary = 2000;
string text = $"Salary is {salary}";
```
- Unfortunately, this causes boxing to occur
- To avoid boxing, manually call the **ToString()** method:
```csharp
int salary = 2000;
string text = $"Salary is {salary.ToString()}";
```


## Performance
- Boxing and Unboxing are computationally expensive processes. 
	- Unboxing to a lesser degree
- Don't forget that by boxing a value type, you are creating another object that the garbage collector has to manage.