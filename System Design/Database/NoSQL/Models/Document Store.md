https://aws.amazon.com/nosql/document/
#### Differences with [[Key-Value Store]]
- Good StackOverflow [answer](https://stackoverflow.com/a/3076781/17385921).
- The value part of [[Key-Value store]] is **opaque**
- The value part of Document Store is transparent and thus databases are aware of the structure (which means they can index them). 
	- Users of the document store can access the objects values using the programming languages dot notation (`product.price`).