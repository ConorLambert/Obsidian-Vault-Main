### Explained
- A result set of a query that is a [[Virtual Table]]

### Use Cases
Views are typically created for one of three reasons:
###### Security: 
- We create views so that a user can read specific columns out of certain tables, but not all the data.
###### Simplification: 
- Sometimes, it’s easier to write a SELECT against one view than a SELECT against multiple tables, with joins – repeatedly.
###### Aggregation: 
- Again, it can be easier to SELECT already-aggregated data than to write the query – repeatedly.