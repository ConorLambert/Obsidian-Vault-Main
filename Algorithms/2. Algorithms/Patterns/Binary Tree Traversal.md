### Overview
- Binary trees are about traversing it in a specific order
- Choose the correct traversal order depending on the current situation.

### PreOrder
###### Explained
- [ChatGPT explanation](https://chatgpt.com/c/66d9c830-a09c-8012-a156-c2871b979422)
	1. Root
	2. Recursively Left subtree
	3. Recursively Right subtree
###### Use Case
- To create a copy of a tree (serialization)

### PostOrder
###### Explained
- [ChatGPT explanation](https://chatgpt.com/c/66d9ca74-5358-8012-9fb1-401774eae885)
	1. Left subtree
	2. Right subtree
	3. Root
###### Use Case
- When you want to process child nodes before the parent

### InOrder
###### Explained
- [ChatGPT explanation](https://chatgpt.com/c/66d9c8e7-2408-8012-945a-364fecbbc977)
	1. Left Subtree
	2. Root node
	3. Right subtree
###### Use Case
- Retrieve values from of a binary search tree in sorted order

### LevelOrder
###### Explained
- [ChatGPT explanation](https://chatgpt.com/c/66d9cad4-8cd0-8012-be37-d047ed7ae1c2)
	1. Root node
	2. Next Level (traverse each root node at this level)
	3. Repeat
###### Use Case
- When you want to explore all nodes at current level before next

### LeetCode Related Questions
- PreOrder
	- 257
- PostOrder
	- 124
- InOrder
	- 230
- LevelOrder
	- 107