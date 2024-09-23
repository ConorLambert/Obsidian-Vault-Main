[Source](https://exercism.org/tracks/csharp/exercises/spiral-matrix)

# Solution
### miuarary's solution
[Source](https://exercism.org/tracks/csharp/exercises/spiral-matrix/solutions/miurary)
- The `i` is responsible for generating the natural numbers. 
	- It starts from 1 and increments by 1 each iteration up to `size * size`
- The `x` and `y` variables are used to decide what position in the array the `i` value is to be inserted into.
	- Both `x` and `y` start at 0.
	- `y` represents the row, `x` represents the column.
- The two other variables `min` and `max` decide the spiral boundaries
	- These variables start at `0` and `size - 1` respectively.
	- These variables are changed to restrict the size of the spiral at a certain point.
- The `if`/`else` statements decide where the next value for `i` will be inserted.