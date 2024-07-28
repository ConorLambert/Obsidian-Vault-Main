#### Explained
- You can create a UNIQUE CLUSTERED INDEX only on a column (or combination of columns) that contains no duplicate data.
- A unique index guarantees that the index key contains no duplicate values and therefore every row in the table is in some way unique (for at least those columns).
#### Discussion
- In [Favour](https://stackoverflow.com/a/4333377/17385921) of uniqueness
- [Situations](https://stackoverflow.com/a/4333162/17385921) where it's better if *not* unique
#### Performance
- Adding a [[uniqueifier]] certainly adds some overhead in calculating and in storing it.
- If this overhead will be noticeable depends on several factors.
	- How much data the table contains.
	- What is the rate of inserts.
	- How often is the CI used in a select 
		- When no covering indexes exist, pretty much always.

