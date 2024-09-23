[Source](https://exercism.org/tracks/csharp/exercises/rotational-cipher)

# Reflection
#### Convert collection to string
- Convert an `IQueryable` or `IEnumerable` to a string by converting the `IQueryable` to an `Array` and wrapping the whole expression into a newly created string
	- `new string(text.Select(x => Rotate(x, shiftKey)).ToArray())`

# Solutions
[1003cora solution](https://exercism.org/tracks/csharp/exercises/rotational-cipher/solutions/1003cora)
- Why create an inner method rather than a separate method ?
	- Inner method only requires the char as parameter
	- inner method will have access to the shiftKey from the enclosing method so we don't need to pass that in. 
	- Therefore, we can use the inner method in a Select query without having to use a lambda expression.
- The shift expression explained
	`(b + ((c - b + shiftKey) % 26))`
	- From the test's point of view, there are 26 letters from 0-26
	- But in the real world, letters are mapped out in the ASCII table.
	- The variable `b` represents the base ASCII (starting at 65 for lowercase 'a').
		`(c - b + shiftKey)`
	- This is used to put the current ASCII character into the test world of 0-26 by subtracting it away from the value of the current character.
		`% 26`
	- We also need to modulo by 26 because the `shiftKey` may result in a character being shifted past the 26 mark which means it needs to wrap back around to the beginning.
		`b + `
	- Once that part of the expression is done, we need to map it back into the ASCII world again by adding back the base ascii value (variable `b`)