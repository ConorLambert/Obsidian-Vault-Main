---
	tags: as, operator, boolean, casting
---

#### Overview
- The `as` operator is used to **explicitly convert a value** to a compatible reference type or nullable type. 
- The `as` operator never throws an exception
- If the conversion is not possible, it will return null.

#### Code Example
```csharp
Object obj2 = new Bus();
Car car2 = obj2 as Car;
```