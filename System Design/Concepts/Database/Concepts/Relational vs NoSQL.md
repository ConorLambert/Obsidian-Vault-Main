### Guidelines
- ???

### Crossover
- Relational Databases can provide the same capabilities that a NoSQL database can provide and vice-versa.
	- For example, PostgreSQL has a native JSONB data type and the ability to query JSON documents and even build indexes against their complex structure. 
	- On the other hand, some NoSQL databases also have ACID capabilities that are often associated with relational databases.

### Checklist
- https://backendinsights.com/p/backend7-picking-the-right-database

### Discussion (Reddit, YT Comments)

##### Reddit:
[Which database is better suited for this project, NoSQL (specifically MongoDB) or SQL?](https://www.reddit.com/r/node/comments/15oztau/which_database_is_better_suited_for_this_project/)
- *The answer is always a relational database, like Postgres, unless you have extremely strong reasons to use something else.* 
- *Always default to SQL, and it will be the right choice 99% of the times. ==If you don't know if you need NoSQL, then you probably don't.==*
- *My systems that i worked on have dozens of tables each with millions of records (there was one with 800 tables) and they are going fine. Remember: NoSQL is fairly recent, which mean the whole internet run on SQL less than a decade ago. That include those gigantic corporations like Facebook, Twitter, Google, Microsoft, etc. And even reddit*
- *As others have said, it's generally better to just default to relational unless you really know why you're opting for NoSQL. Postgres would be my recommendation.*
- *I would consider a document db like mongo for flatter data, like only a listing of movies, only a message board, a wiki etc.*
[What are the advantages of using NoSQL databases vs relational databases?](https://www.reddit.com/r/Database/comments/rtnnyq/what_are_the_advantages_of_using_nosql_databases/)
- Check the highlights in the article
##### YouTube:
[How to choose the right database for your application - Zoe Steinkamp - NDC Oslo 2023](https://www.youtube.com/watch?v=hj2yFugmpz8)
- *For over 99% of companies PostgreSQL and the extensions available are FOSS and can do anything they need. Relational, document, vector, time series, graph, KV, etc. Postgres has you covered. Want row store, compressed row store, column format storage or even parquet storage? Postgres has that covered. Want scale out? Postgres has that covered too. It’s all free and you can deploy it anywhere. If you want to start with something start there. If you then realise that you need something that is a little bit better because it is very specialised then change. However, I cannot think of anything where there is an order of magnitude difference between Postgres + extensions and more specialised publicly available DB that more than at most 1% of companies might need.*
