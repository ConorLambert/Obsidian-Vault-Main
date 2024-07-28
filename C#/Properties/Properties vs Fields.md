#### Fundamental Difference
- A field is a position in memory where data of the specified type is stored. 
- A [[! What is a Property|property]] represents one or two units of code that are executed to retrieve or set a value of the specified type.

#### Other Differences
- Fields cannot be used in [[! What is an Interface|interfaces]] but properties can.
- Fields can be used as input to `out/ref` arguments. Properties can not.
- A field will always yield the same result when called multiple times (if we leave out issues with multiple threads). A property such as `DateTime.Now` is not always equal to itself.
- Properties may throw exceptions - fields will never do that.
- Properties may have side effects or take a really long time to execute. Fields have no side effects and will always be as fast as can be expected for the given type.
- Properties support different accessibility for getters/setters - fields do not (but fields can be made `readonly`)
- When using reflection the properties and fields are treated as different `MemberTypes` so they are located differently (`GetFields` vs `GetProperties` for example)
- The JIT Compiler may treat property access very differently compared to field access. It may however compile down to identical native code but the scope for difference is there.