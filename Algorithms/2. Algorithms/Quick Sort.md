### Explained
- Divide-and-conquer algorithm
- Excellent [video](https://www.youtube.com/watch?v=pM-6r5xsNEY) explaining how it works
- It works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays, according to whether they are less than or greater than the pivot.
- This process is known as **partitioning** as is performed recursively until the array is sorted.
- Any element can be chosen to be a pivot but most common is to choose the middle index.

### Collection Conditions
- NAN

### Time Complexity
- `O(n^2)` in the worst case
	- The chosen pivot is either the smallest or the largest element in the array.
	- It's important to note that while the worst case scenario sounds quite bad, it is quite rare in practice, especially if the pivot is chosen randomly.
- `O(n log n)` in the best and average case

### Space Complexity
- The total space complexity is proportional to the height of the recursion tree.
- `O(N)` in the worse case
	- Imagine picking a pivot that is the largest or smallest in the array.
	- Due to this unbalanced partitioning, a skewed recursion tree will form requiring a call stack of size `O(n)`.
- `O(log n)` in best and average case
	- The height of the recursion tree is always at least O(log n)

### Use Cases
- In computer graphics, quick sort is used for *image rendering*.
- Used for data *visualisation*.
- In numerical computations, quick sort is used for *matrix sorting*.

### Comments
- ???

### Code Example
- ???