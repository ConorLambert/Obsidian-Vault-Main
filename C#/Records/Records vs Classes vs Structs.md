# Don't Stress Over It
- If in doubt, just use a class. 
- If your environment is more critical than average about computation overheads, then decide whether a `record` or `struct` would be better.
	- Some examples of such environments
		- cloud/datacenter scenarios where computation is billed for and responsiveness is a competitive advantage.
		- Games/VR/AR with soft-realtime requirements on latencies

# Guidelines 
Really good answers on this [thread](https://stackoverflow.com/questions/64816714/when-to-use-record-vs-class-vs-struct) including ones where you ask yourself a number of questions.
#### Class
- Mutability.
- When your data structure requires encapsulating data and behaviours or when you need to manipulate the data after its creation.
#### Record
- Immutability
- DTOs
- Value Comparison
- Don't contain any logic or very small chunks of logic (helper methods rather than business ones)
#### Struct
- ???