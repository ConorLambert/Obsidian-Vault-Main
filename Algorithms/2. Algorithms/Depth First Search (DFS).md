### Explained
- Short YouTube [video](https://www.youtube.com/watch?v=Urx87-NMm6c).
- Differs from [[Breadth First Search (BFS)]] in that the graph is searched vertically.
- Makes use of the `stack` data structure (LIFO) to ensure vertical search:
	 ![[Depth-First-Tree-Traversal.gif|300]]
	 
### Collection Conditions
- NAN

### Time Complexity
- O(V+E) (V is *vertices*, E is *edges*).

### Space Complexity
- O(V) (V is *vertices*)
- Uses a queue to keep track of the vertices that need to be visited. In the worst case, the queue can contain all the vertices in the graph. 
- Therefore, the space complexity is O(V).

### Use Cases
- [GeekForGeeks](https://www.geeksforgeeks.org/applications-of-depth-first-search/?ref=lbp)

### Comments
- ???

### Code Example
- ???