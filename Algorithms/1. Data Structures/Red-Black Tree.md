[Source](https://www.geeksforgeeks.org/introduction-to-red-black-tree/)
## Overview
- A [[binary search tree]] is a fundamental data structure, but their performance can suffer if the tree becomes unbalanced.
- Red-black trees are a type of self-balancing binary search tree.
- Uses a set of rules to ensure logarithmic time complexity for operations regardless of the initial shape of the tree.
- Each node has an additional attribute: a color, which can be either red or black.

### Properties of Red-Black Trees
These properties ensure that the longest path from the root to any leaf is no more than twice as long as the shortest path, maintaining the tree’s balance and efficient performance:
1. **Node Color:** Each node is either red or black.
2. **Root Property:** The root of the tree is always black.
3. **Red Property:** Red nodes cannot have red children (no two consecutive red nodes on any path).
4. **Black Property:** Every path from a node to its descendant null nodes (leaves) has the same number of black nodes.
5. **Leaf Property:** All leaves (NIL nodes) are black.

	![[Pasted image 20240821163709.png|200]]

## Rotations
[Source](https://www.youtube.com/watch?v=95s3ndZRGbk)
##### Overview
- Fundamental operation to maintain balance
- Remember the right subtree holds the bigger values and the left subtree holds the smaller values.
	- *Rotation will still maintain this*
- Occurs after Insertion and Deletion operations
##### Left Rotation
- ???
##### Right Rotation
- ???

## Operations
- Insertion
	- Same as [[binary search tree]] but with added rotation
- Deletion
	- Same as [[binary search tree]] but with added rotation
- Searching
	- Same as [[binary search tree]]

## Use Cases
- `SortedDictionary<K,V>`

## Time Complexity
- O(log n) -> Insertion, Deletion, Search
- O(1) -> Rotation
	- Only changing a few pointers in the tree

## Space Complexity
- O(n)
	- Only require additional storage bit for color

## Weaknesses
- ???


