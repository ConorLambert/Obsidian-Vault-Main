#### Overview
- An inverted index is a database index storing a mapping from content, such as words or numbers, to its locations in a table, or in a document or a set of documents.
- This allows you to quickly find documents that contain a given word
- It is the most popular data structure used for search engines

#### Example
- Imagine we have the following database table, which stores different written phrases

	![[Pasted image 20240723152350.png|200]]

- Below is an inverted index for that table. As you can see, this index lists the location of each word (called a **token**) in the table.

	![[Pasted image 20240723152422.png|250]]