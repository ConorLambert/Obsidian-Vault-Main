[ChatGPT Source](https://chatgpt.com/c/de28f696-d180-4d9f-b336-db618ad84543)

### Overview
- ???

### Use Cases
- Calculation sum of elements in a subarray
- Other range related queries

### Problem
- The problem at hand might just require a specific subarray `i-j` in which a simple iteration starting at `i` and ending at `j` will give you the result in `O(n)` time.
- However, what if the subarray was not fixed and instead had multiple queries. The time complexity here would downgrade to `O(n * m)` where `n` is the array length and `m` is each subarray length.

### Implementation
- Create **prefix sum** array that contains the cumulative sum of elements of the original array up to each index.
- Example
	- `arr = [2, 4, 6, 8, 10]`
	- `prefix_sum = [2, 6, 12, 20, 30]`
- ??? Check source

### Complexity
##### Time Complexity
- O(n)
- Brute force approach is `O(n * m)` .
##### Space Complexity
- `O(n)`.
- Additional array is needed for the **prefix sum**.

### LeetCode Related Questions
- 303
- 525
- 560