#sequential #order #unique #poker
## Problem
##### Statement
- Given an array of ints, check if the numbers can be arranged in sequential order with no missing number and no duplicates.
##### Solution
``` c#
public static bool IsSequential(int[] numbers)
{
	return new HashSet<int>(numbers).Count == numbers.Count() && numbers.Max() -numbers.Min() == numbers.Count() - 1;
}
```
- `HashSet` can contain only unique values
- We can find if the numbers are sequential from value `x` through to value `y` by subtracting `x` from `y` and seeing if the value equals the count of items -1.
##### Example input
`numbers` = [3,4,2,5,1]
- Array count = 5
- `HashSet` will contain 5 elements
- Subtracting 1 (Min) from 5 (Max) = 4
- 4 is 1 less than the Array count.

## Performance
- ???

## Use Cases
- Finding a straight flush in poker (Ace,2,3,4,5)