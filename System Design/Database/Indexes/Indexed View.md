[Source](https://www.sqlservertutorial.net/sql-server-views/sql-server-indexed-view/)
#### Explained
- Unlike regular views, indexed views are materialised views that stores data physically in the database like a table.
- When the data of the underlying tables changes, the data in the indexed view is also automatically updated. 
	- Therefore, ==you should only create an indexed view against the tables that have in-frequent data updates==.

#### Limitations
- The view definition can’t reference other views, or tables in other databases.
- It can’t contain COUNT, MIN, MAX, TOP, outer joins, or a few other keywords or elements.
- You can’t modify the underlying tables and columns. 
	- Will have to drop and re-create index

#### How to Create
- Check Source.