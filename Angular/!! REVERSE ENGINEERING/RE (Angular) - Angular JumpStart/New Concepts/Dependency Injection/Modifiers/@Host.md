### Purpose
- Meant for directives only.
- Imagine that the component has a private instance of a service, created by its own provider.
- The directive is also part of the same module and that directive is designed so that it interacts closely with that particular component.
- Because that directive is closely coupled with the component, it might want to access some of the private services associated to that component, and no other.
- It says to Angular to search for a matching provider only on the providers of its host component, and nowhere else.

### Example
- Imagine a simple `HighlightedDirective`, that is meant to visually highlight a course card to which it's applied.
- Let's say that this directive is designed to interact tightly with the  `CourseCardComponent`, and would like to access its private instance of  `CoursesService`:

	![[Pasted image 20240307124758.png|400]]

- The directive could access the private component service in the following way:

	![[Pasted image 20240307124625.png|500]]

