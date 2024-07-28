### Explained
Good illustration in this [video](https://youtu.be/XEmy13g1Qxc?t=219&feature=shared)
- Uses the same overall approach as [[Quick Sort]], choosing one element as a pivot and partitioning the data in two based on the pivot, accordingly as less than or greater than the pivot. 
- However, instead of recursing into both sides, ==quick select only recurses into one side== – the side with the element it is searching for. 
- This reduces the *average* complexity from O(n log n) to O(n) , with a worst case of O(n$^2$)

### Collection Conditions
- NAN

### Time Complexity
- Worse case **O(n$^2$)**
- Average and best case is **O(n)**

### Space Complexity
- **O(n)**
- Sorted in-place

### Use Cases
- [[Top-k Largest Elements]]

### Comments
- ???

### Code Example
- ???