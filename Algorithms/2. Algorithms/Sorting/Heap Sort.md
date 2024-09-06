### Explained
[ChatGPT Source](https://chatgpt.com/c/23e07a28-fdc0-4a03-831c-db8179b707dc)
- Utilises a [[heap]] data structure to efficiently sort elements.
- Operates in two main phases: 
	- Building a heap
	- Repeatedly extracting the maximum (or minimum) element to produce the sorted order.
- Building the Heap
	- Arrange array elements *in-place* into a binary tree structure
	- Recursively [[Heapify]] starting at the last non-leaf node moving upward

### Collection Conditions
- NAN

### Time Complexity
- O(n log n)
	- Building the heap: O(n)
	- Heapify: O(log n)

### Space Complexity
- O(1)
- All done in-place

### Use Cases
- [[Queue#Priority Queue|Priority Queue]]

### Comments
- Not used as much as [[Quick Sort]] and [[Merge Sort]] which have better average performance due to lower constant factors.

### Example
- Consider the array `[4, 10, 3, 5, 1]`
	1. Build a Max Heap:
		- Initial array: `[4, 10, 3, 5, 1]`
		- After heapifying: `[10, 5, 3, 4, 1]`
	2. Sorting:
		- Swap the first and last element: `[1, 5, 3, 4, 10]`
		- Heapify the remaining array: `[5, 4, 3, 1, 10]`
		- Continue the process until the array is sorted: `[1, 3, 4, 5, 10]`