## Overview
- A database built for indexing and querying information. 
- These databases are optimized for searching through large volumes of stored data based on user queries and then return results ranked by relevance. 
- They are generally considered to be a type of NoSQL or non-relational database and use indexes (such as an [[Inverted Index]]) to categorize data to make searching faster and more efficient.
- Clear leader in Search Engine Databases is [[Elasticsearch]].

## Terminology
##### Tokenization: 
- The process of breaking a piece of text into individual words. 
- This allows you to map from words to documents in the [[inverted index]].
##### Stemming: 
- The process of reducing words to their root form. 
- This allows you to match different forms of the same word. 
- For example, "running" and "runs" would both be reduced to "run".
##### Fuzzy Search:
- The ability to find results that are similar to a given search term. 
- This works by using algorithms that can tolerate slight misspellings or variations in the search term. 
##### Scaling: 
- Just like traditional databases, search optimized databases scale by adding more nodes to a cluster and sharding data across those nodes.

## Use Cases
- [[Full-text search]]
- Other [examples](https://www.influxdata.com/search-engine-database/#use-cases)
