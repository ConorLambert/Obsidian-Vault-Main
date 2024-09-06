[Source](https://exercism.org/tracks/csharp/exercises/clock)

# Reflection
- This one I completed on my own.
- Modulo checksum is a great help in problems like this.
- Need to understand `string.Format` better to utilize it's full capabilities.
- The following one liner sufficed for outputting the correct time
	- `return string.Format("{0:00}:{1:00}", _hours, _minutes);`
	- 0:00
		- the first `0` represents which string parameter to use (`_hours`). 
		- The `:` indicates that we would like to format this string (as opposed to just displaying it) 
		- the trailing `00` indicates what way we would like to format it.
	- More info [here](https://stackoverflow.com/questions/12480444/adding-a-0-if-number-is-less-than-10) on the 00 formatting
- Can just use the overridden `.ToString()` method for `GetHashCode` and `Equals` like so.
```c#
public override int GetHashCode()
{
	return ToString().GetHashCode();
}

public override bool Equals(object other) {
	if(other is null)
		return false;
	return this.ToString() == other.ToString();
}
```