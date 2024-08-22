### Difficult people on software projects
- [The idealist](https://neilonsoftware.com/difficult-people-on-software-projects/developers/the-idealist/)
### Return the most specific type, accept the most generic type
- [Source](https://enterprisecraftsmanship.com/posts/return-the-most-specific-type/)
- You should always try to make it easier for the clients of your code to use your API, *even if the client is you*.
- In-house software
	- Make your methods return values of the most specific type possible.
	- make your methods accept parameters of the most generic types possible.
- Out software is a 3rd party Library
	- You should always prefer interfaces over concrete collection types for methods that are parts of a redistributable library’s public API. This statement is true for both returning value and input parameter types.
	- This only applies to public API methods, private methods should follow in-house software rules.
- If a method returns a read-only collection, show that by using IReadOnlyList or IReadOnlyCollection as the return value type.