- Properties promote good OO design i.e. [[Encapsulation]]
- If you don't have a very good reason for doing it, **always** choose a property over a public variable / field.
- It affects already compiled code. For example, if you are developing a library that is used by several applications, changing a field to a property in that library would require a recompile of each application. If it were a property, you could update the property without worry.
	- Unless the field in question has an `internal` access modifier.