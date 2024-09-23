[Source](https://exercism.org/tracks/csharp/exercises/tournament/solutions/countingquoll)

# Lessons Learned
#### Padding and Alignment
[StackOverflow Solutions](https://stackoverflow.com/questions/48478323/c-sharp-how-to-set-a-fix-field-width-using-string-interpolation)
- String interpolation has an additional parameter to define how many spaces you want before or after the string.
- This parameter can be used to align text *because the value we provide will be deducted from the length of the string being interpolated*. So a string with 10 characters and a string with 5 characters will be correctly aligned in the output.
- Setting it to a negative value will add the spaces to the right.

# Code Snippets
#### Referencing a line and checking for null
- `while ((line = reader.ReadLine()) != null)`
- `ReadLine` returns the next line or null
- We would otherwise have to check for null inside the for loop and exit.
- The above approach is more concise.

# Solutions
[countingquoll's solution](https://exercism.org/tracks/csharp/exercises/tournament/solutions/countingquoll)
- No new class or dictionary needed.
- Create a list of tuples, one for each match
- Project those tuples using `SelectMany` to find the match results.
	- This step produces more rows which is why `SelectMany` is used to make sure those extra rows are returned. 
	- If you use just `Select`, then the `GroupBy` won't work
- `GroupBy` results by the `team` property.
	- A `Select` after the `GroupBy` to project an anonymous type that has all the properties needed to printing the final result.
	- This GroupBy is important so look closely at it
	- This statement uses lots of Count and Sum methods to create a new type
- The above approach is good because the output tournament table is smaller than the input of matches. The `GroupBy` will collapse each match result by team.