#### Overview
- A heap is a tree that is a [[complete binary tree]] and satisfies the heap property: 
	- the value of each node is greater than (or less than depending on the heap type) or equal to the value of its children.
- This property makes sure that the root node contains the maximum or minimum value and the values decrease or increase as you move down the tree.

#### Implementation
- A heap can be represented using an array.

#### Min-Heap
- If each parent node is _less than_ or *equal* to its child node
- When people say Heap, they usually mean Min-Heap.

#### Max-Heap
- If each parent node is _greater than_ or *equal* to its child node

#### Use Cases
- Heaps are usually used to implement [[Queue#Priority Queue|priority queues]], where the smallest (or largest) element is always at the root of the tree.
- [[Heap Sort]] is a sorting algorithm that uses a heap to sort an array in ascending or descending order.
- Heaps are used in graph algorithms like Dijkstra’s algorithm and Prim’s algorithm for finding the shortest paths and minimum spanning trees.
