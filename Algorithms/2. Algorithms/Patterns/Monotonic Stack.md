### Overview
- Uses a stack to find the next greater/smaller element in an array. 

### Use Cases
- Find the next greater/smaller element in an array

### Implementation
- Given the following problem: "Given an array, find the next greater element *for each item*."
- Brute force approach would O(n$^2$) because each item will require iterating all other items.
- Monotonic Stack approach visualised [here](https://youtu.be/DjYZk8nrXVY?t=299)

### Complexity
##### Time Complexity
[ChatGPT Source](https://chatgpt.com/c/68d70081-a287-40d7-8b49-f9fdc019719c)
- O(n)
- Worse case, each element is pushed and popped exactly once.
##### Space Complexity
[ChatGPT Source](https://chatgpt.com/c/7db05647-a670-4fc5-aab2-1f99992a5ed7)
- O(n)
- Worse case, all elements from array are pushed onto stack without any being removed.

### LeetCode Related Questions
- 84
- 496
- 739