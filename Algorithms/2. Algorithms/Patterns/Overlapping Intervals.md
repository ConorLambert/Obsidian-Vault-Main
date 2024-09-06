### Overview
- Intervals or ranges that may overlap

### Use Cases
- Merging Intervals
	- Given a collection of intervals, merge all overlapping intervals into one.
- Interval Intersection
	- Find intersection between two set of intervals
- Insert Interval
	- Insert new interval into list of non-overlapping intervals.
- Find minimum number of meeting rooms needed for overlapping meeting times.

### Implementation
- [Example](https://youtu.be/DjYZk8nrXVY?t=417) for merging all overlapping intervals
	- Sort intervals by their start time
	- Iterate though intervals and see if current interval merged with last interval.
	- If no overlap, then add to output merged array
	- If merge exists, update the last value of the last element added to the merged array to the last value of the current interval
	![[Pasted image 20240905153948.png|300]]

### Complexity
##### Time Complexity
- ???
##### Space Complexity
- ???

### LeetCode Related Questions
- 56
- 57
- 435