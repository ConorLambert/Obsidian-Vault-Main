## Overview
- [Big-O notation in 5 minutes](https://www.youtube.com/watch?v=__vX2sjlpXU)
	- Excellent summary of Big O and how to calculate it
- Big O notation is used to describe how an algorithms runtime increases as the input size increases.

## Benefits
- Algorithm scalability is important:
	- [[Binary Search]] vs simple search when doubling the size of N.
- Compare algorithms
- Machine independent

## Complexity Chart

![[Pasted image 20240626102045.png|500]]
## Rules
- N represents the input size
- Drop lower order terms:
	- Higher order terms dominate as N moves to infinity (look at **Complexity Sheet**)
- An operation that does not depend on the input size is a **constant**:
	 `x = 5 * (15 * 20)`
- Constant operations are `O(1)`
- Big O notation is about the *worst-case scenario*.
	- It’s a reassurance - you know that the algorithm will never be slower than that.
- In Big O notation, the runtimes that are described using [[logarithms]] or `log` always means `log`$_2$.

## Calculation Examples:
- The linked [video](https://youtu.be/__vX2sjlpXU?t=114&feature=shared) has some good examples from the **Constant Time** chapter onward.

## Exercises:
- ???

## Important
- In practice, constant time is still important
	- You could have a small input size so the constant operations may be the thing that slows your algorithm down.
- Don't dismiss best and average cases
	- It may be applicable to your algorithm

