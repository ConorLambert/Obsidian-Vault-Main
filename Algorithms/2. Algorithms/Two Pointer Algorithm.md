### Explained
- Two pointers is really an easy and effective technique that is typically used for searching pairs in a sorted array
- A common problem it solves is finding a pair of elements in a *sorted* array such that their sum is equal to `X`:
- Without using the Two Pointer technique, a naive approach would compare each element in the array with each other element in the array until it matches the sum. This would result in O(n$^2$).
- The two pointer approach:
	- Takes two pointers, one representing the first element and other representing the last element of the array, 
	- Then we add the values kept at both the pointers. 
	- If their sum is smaller than X then we shift the left pointer to right or if their sum is greater than X then we shift the right pointer to left, in order to get closer to the sum. 
	- We keep moving the pointers until we get the sum as X.
- This YT [video](https://www.youtube.com/watch?v=On03HWe2tZM) gives a good explanation from an interview standpoint.
	

### Collection Conditions
- Sorted

### Time Complexity
- O(n log n)

### Space Complexity
- O(n)
- Only needs the input array itself

### Use Cases
- In many problems involving collections such as arrays or lists, we have to analyze each element of the collection compared to its other elements.

### Comments
- ???

### Code Example
- ???
