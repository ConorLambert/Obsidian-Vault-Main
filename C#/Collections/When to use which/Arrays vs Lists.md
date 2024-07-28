#### Overview
- Nearly always use List over Array
- Use List when:
	- You don't know the size of the collection 
	- You need to add and/or remove items
- Use Array when:
	- You know the data is fixed length and you want to micro-optimise for some **very specific** reason (after benchmarking).
	- A rectangular structure is required (e.g multi-dimensional arrays).
	- Image bitmap data
		- Bitmap images are built using 2 dimensional arrays
	- Other low-level data-structures (i.e. network protocols and network buffers)
		- Stream.Read and Stream.Write work with byte[]
	- To imply that the data is **fixed length**. If I won't add or remove any items from that data collection, I want to make sure that the type reflects that. 
		- It provides a signal to other programmers that it is a fixed size, and helps prevent misuse where someone adds or removes an element - breaking expectations elsewhere in code.

#### References
- https://stackoverflow.com/questions/434761/array-versus-listt-when-to-use-which
- https://learn.microsoft.com/en-us/archive/blogs/ericlippert/arrays-considered-somewhat-harmful

