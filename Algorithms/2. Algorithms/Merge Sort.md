### Explained
- Follows the **divide-and-conquer** approach
- Recursively divide the input array in half until all the elements are separated individually
- Pairs of elements are then compared, placed into order and combined.
- Then merge them back together to obtain the sorted array:

	![[Pasted image 20240701165756.png|300]]

###### How The Actual Merge Is Performed
- Notice how the index referencing the smaller value stays the same per iteration:

	![[1_uT7I4U6f56EobbTlPdBhRw.gif|300]]

### Collection Conditions
- NAN

### Time Complexity
- O(n log n)

### Space Complexity
- O(N) + O(N) = O(N)
- Additional space is required for the temporary array used during merging.

### Use Cases
- ???

### Comments
- ???

### Code Example
- https://www.geeksforgeeks.org/merge-sort/#implementation-of-merge-sort