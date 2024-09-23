[Source](https://courses.dometrain.com/courses/take/from-zero-to-hero-linq-in-net)

# Getting results from queries
### Retrieving a Single Item
- Avoid using `Where` followed by a `First` or `Last`.
	- Just use `First` or `Last` with a predicate.
- `Single` expects a single result and if more than one result is returned, then an error is thrown. An error is also thrown if no result is found which is why we have `SingleOrDefault`. 
	- `Single` will iterate through the entire list if none or one is found but it will stop and throw an error when a second one is found.
- `Last()` starts it's search from the end of the collection (check comments below, not always the case).
- `Last()` can contain a lambda expression like a `Where` clause.
- `Last()` efficiency issues:
	- Calling `Last()` on a `Where` clause or `IQueryable` will cause the iteration to start from the beginning and not the end.
	![[Pasted image 20240922222112.png]]
	![[Pasted image 20240922222056.png]]
	- However, calling `Last()` directly on an `IList` implementation will cause the iteration to start at the end (which is what we want).
	![[Pasted image 20240922222556.png]]
	- More Info
		- TLDR: In order to start the iteration from the end, the type you are calling `Last` on must provide a reverse enumerator.
		- The efficiency of calling `Last` on an `IQueryable<TSource>` will depend on the underlying data source for `IQueryable<TSource>`. The underlying data source many not provide support for fetching the last item 
		- Frameworks like Entity Framework or LINQ to SQL differ in how they implement IQueryable
		- This means the iteration may start at the beginning of the collection instead of the end thus producing a much slower execution time.
		- However,`IList` implementations provide a *reverse enumerator* that allows iteration to start at the back. So calling `Last` on a type that implements IList will be more efficient as it will start at the back.

### Projecting the data to another shape
- Instead of creating anonymous types, it's better to project as Value Tuples.
	- Much easier to use and pass around.

# Dealing with Partial Results
### Introduction to getting partial results
- Pagination is common applications
- Only want a certain chunk of data and not the whole result
- Wanting to Group By results is also common.

### Splitting results into chunks
- Can return a collection into equal sized chunks.
- `Chunk(count)` method returns an `IEnumerable` of arrays
- Each iteration will be an array.
- LINQ methods such as `Select` method have an additional `index` parameter
	- `Select((item, index))`

### Using `Skip`, `Take` and `TakeWhile` to retrieve a specific result
- `TakeWhile`
	[ChatGPT answer with use cases](https://chatgpt.com/c/66f12326-e284-8012-bed2-ad38a1b1288a)
	- Used to return elements from a sequence (such as a collection or array) as long as a specified condition is true. 
	- Once the condition becomes false for the first time, the method stops returning elements, *even if subsequent elements would satisfy the condition*.
- `Skip` and `Take` have last alternatives namely `SkipFirst`, `SkipLast`, `TakeFirst` and `TakeLast`.
- `SkipWhile`
	[ChatGPT Answer](https://chatgpt.com/c/66f12438-3894-8012-bf08-290ee0dddfe3)
	- Used to bypass elements in a sequence as long as a specified condition is true and then returns the remaining elements. 
	- Once the condition becomes false for the first time, the method stops skipping and yields the rest of the elements, regardless of whether they satisfy the condition or not.

### Dividing results into logical parts with GroupBy
- ???