## Don't Overdo it
- You could follow the SOLID principles down to the letter and still end up with bad code.
- Dependency Inversion is great but generally only one class ever implements an interface. It really shines in situations where we need to mock out functionality like in Unit Tests.

## PDD (Pain Driven Development)
- Write using the simplest code you know to get the problem solved
- Don't worry about SOLID
	- ==Trying to apply all the SOLID principles up front is a form of [[Premature Optimisation]]==
- As your application grows, look for places where the application is painful to work with
	- Difficultly with testing 
	- Excess duplication
	- Too much coupling
- ==When you feel that pain, see if any of the SOLID principles can be applied.==