[Source 1](https://aws.amazon.com/nosql/graph/)
[Source 2](https://www.reddit.com/r/cscareerquestions/comments/17ru9l3/can_someone_explain_a_graph_database_as_compared/)

### Overview
- A graph database is a systematic collection of data that emphasizes the relationships between the different data entities. 
- You have **nodes** that are connected to each other with **edges**, and those nodes and edges can have **properties**. 
- You can query these nodes and edges by their ID numbers or by filtering based on one of the properties.

### Purpose
- Most NoSQL databases store sets of disconnected aggregates. 
- They lack relationships and this makes it difficult to use them for connected data and graphs. 
- There are strategies to circumvent this but they quickly becomes prohibitively expensive.

### Storage Mechanism
- The underlying storage mechanism of graph databases can vary. 
- *Relationships are first-class citizens in a graph database and can be labelled, directed, and given properties.* 
- Some depend on a relational engine and store the graph data in a table. 
- Others use a key–value store or document-oriented database for storage, making them inherently NoSQL structures.

### Use Cases
- *When the relationship between two data points (the edges) is as (or more) important as the data points themselves.*
- Searching for *hidden and apparent **relationships***.
- More examples under the **What are the use cases of graph databases** heading [here](https://aws.amazon.com/nosql/graph/)
- This video [section](https://youtu.be/hj2yFugmpz8?t=1851) gives some good ones

### Real-World Users
- https://neo4j.com/who-uses-neo4j/

### Discussions (Reddit/YouTube)
##### Reddit
[Why no one uses graph databases?](https://www.reddit.com/r/ExperiencedDevs/comments/phzek0/why_no_one_uses_graph_databases/)
- The consensus here is that Graph databases are very difficult to implement so unless your getting a massive benefit out of it then it's not worth it. Only companies that are dealing with systems on a massive scale are really using it. Even then, many are using MySQL or Postgres and not even using a Graph Database.
[Graph Databases](https://www.reddit.com/r/dataengineering/comments/1008zi6/graph_databases/)
- Graph Databases are under utilized and people end up re-inventing the wheel using other technologies.
- One person [here](https://www.reddit.com/r/dataengineering/comments/1008zi6/comment/j2hyooj/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button) wrote that it can become a big mess though.