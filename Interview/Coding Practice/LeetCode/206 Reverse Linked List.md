[Source](https://leetcode.com/problems/reverse-linked-list/description/)

## Solution
- Problem is there's no previous reference in the `ListNode` type
- Explained in detail [here](https://medium.com/outco/reversing-a-linked-list-easy-as-1-2-3-560fbffe2088)
```c#
public ListNode ReverseList(ListNode head) {
	ListNode previous = null;
	var current = head;
	var following = head;

	while(current != null) {
		following = following.next;
		current.next = previous;
		previous = current;    
		current = following;
	}

	return previous;
}
```
- We use `previous` to keep reference of the previous node each iteration. 
- At the start `previous` is `null`
- Each iteration `previous` will reference the current node (near the end of the algorithm) and be used in the subsequent iteration to point backward (near the start of the algorithm).
	- `current.next = previous`
- It would be impossible to solve this problem without this variable.
- The order of steps in the while loop is important
	- We need to reference the `next` node before reassigning it.

