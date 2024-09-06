### Explained
- BFS is a graph traversal algorithm that systematically explores a graph by visiting all the vertices at a given level before moving on to the next level. 
- It starts from a starting vertex, enqueues it into a queue, and marks it as visited. 
- Then, it dequeues a vertex from the queue, visits it, and enqueues all its unvisited neighbours into the queue. 
- This process continues until the queue is empty.
- This approach ensures that elements across the same level of the tree are next to each other on the Queue. This way, we can process them one after the other.

![[Breadth-First-Tree-Traversal.gif|300]]

### Collection Conditions
- NAN

### Time Complexity
- O(V+E) (V is *vertices*, E is *edges*).

### Space Complexity
- O(V) (V is *vertices*)
- BFS uses a queue to keep track of the vertices that need to be visited. In the worst case, the queue can contain all the vertices in the graph. Therefore, the space complexity of BFS is O(V).

### Use Cases
- If you have a problem like “find the shortest X between two nodes"
- Detect cycle in a directed and undirected graph
- Printing all nodes of a tree level by level
- Finding all connected components.
- Finding the shorted transformation sequence from one word to another.
	- "hit" -> "hot" -> "dot" -> "dog" -> "cog"
- Full list on [GeeksForGeeks](https://www.geeksforgeeks.org/breadth-first-search-or-bfs-for-a-graph/#applications-of-bfs-in-graphs)

### Comments
- ???

### Code Example
- ???