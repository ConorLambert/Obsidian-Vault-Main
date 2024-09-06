### Overview
- Finding the K largest/smallest elements from an array is a common problem that often arises in various scenarios.

### Solutions:

##### The Naive Approach: Sorting
- Steps
	1. Sort the array in ascending/descending order
	2. Extract first K elements
- Time complexity is `O (N log N)`

##### The Optimised Approach: Utilising a [[Heap#Min-Heap|Min-Heap]] (Priority Queue)
- Explained [here](https://jaskirat-singh.medium.com/efficiently-finding-the-k-largest-elements-in-an-array-d745fe84a89b)
- Steps:
	1. Create a min-heap (priority queue) to store the K largest elements.
	2. Insert the first K elements from the array into the min-heap.
	3. Iterate through the remaining elements of the array.
	4. If the current element is larger than the minimum element in the min-heap, remove the minimum element and insert the current element.
- Time Complexity is `O(N log K)`
	- This optimisation can provide significant performance gains, especially when dealing with large datasets.
- NOTE: Use Max-Heap for largest element

##### Using Quick Select
- Use [[Quick Select]]
- Stack Overflow [answer](https://stackoverflow.com/a/73036179/17385921) and general overview of this approach
- Time Complexity is `O(n)`

### Choosing One
- Naive approach is much simpler
- Large datasets = Optimised Approach
- Smaller datasets = Naive Approach

### LeetCode Related Questions
- 215
- 347
- 373