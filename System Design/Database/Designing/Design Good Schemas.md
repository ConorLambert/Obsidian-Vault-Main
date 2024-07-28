[Design Good Schemas - Get a Better Database - Nuri Halperin - NDC Oslo 2023](https://www.youtube.com/watch?v=iDWwoz9ZUzw)

# Design Good Schemas - Get a Better Database - Nuri Halperin - NDC Oslo 2023
![](https://i.ytimg.com/vi/iDWwoz9ZUzw/maxresdefault.jpg)



[Source URL](https://www.youtube.com/watch?v=iDWwoz9ZUzw)

## Introduction [(00:00:00)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=0s)
- Nuri Halperin, the speaker, introduces the topic of designing good database schemas to achieve better results.
- He shares his experience as a developer, highlighting his work with backend development, databases, data migrations, and various programming languages like C#, Python, and JavaScript.
- Nuri aims to share his insights on what has worked effectively in the short and long term, emphasizing the importance of optimizing for long-term success.

## Design good schemas [(00:00:45)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=45s)
- The speaker is discussing the importance of designing good database schemas, emphasizing the need to avoid future regrets.
- The speaker acknowledges that developers often make decisions that seem optimal at the time but later prove to be suboptimal.
- The speaker poses the question of what constitutes a "good" schema, highlighting the need to define clear criteria for evaluating schema quality.

## Fitness criteria [(00:01:37)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=97s)
- The schema should directly address a business problem. The schema should be designed to solve a real-world business need, not just internal technical requirements or personal preferences. 
- The schema should be easy to understand and reason with. It should be clear and concise, allowing for easy communication and collaboration within the team. Complex schemas can lead to confusion and difficulty in querying data.
- The schema should be adaptable to future changes. The schema should be designed to evolve with the product and business needs, minimizing the impact of future changes. This ensures that the schema remains relevant and effective over time.

## Model vs Schema [(00:04:10)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=250s)
- The speaker distinguishes between "model" and "schema" in the context of database design.
- "Model" refers to a representation of the real world, encompassing things like people, their attributes (height, hair color), and their relationships.
- "Schema" is a more specific term, referring to the structure of the database itself, which is used to store and organize the data derived from the model.

## Design vs Schema [(00:04:50)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=290s)
- In the database world, "schema" refers to the structure of how data is stored, which dictates how it will be processed.
- The most important aspect is the "design," which involves translating the real world into a schema.
- A "model" represents the real world and serves as a bridge between the real world and the schema.

## Model [(00:05:28)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=328s)
- The "model" in database design represents real-world entities and their observable properties.
- The model focuses on capturing the characteristics of an entity that are relevant for business purposes.
- For example, a "catalog item" might have properties like name, measurements, and weight, depending on what information is considered important for the business.

## Schema [(00:06:31)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=391s)
- Schema translates real-world concepts into a database's language. While we might talk about "weight" in the real world, databases use numbers to represent it. Schema allows us to define how these real-world concepts are represented in the database.
- Schema defines relationships between entities. It creates a graph of how different elements in our model are connected. For example, a catalog might contain items, and an invoice might detail the items in a customer's shopping cart.
- Schema defines constraints on data values. This ensures data integrity. For example, a "country" field might be defined as a two-letter ISO code, limiting the possible values. This can be done through domains or domain tables, depending on the database system.
- Schema choices impact performance. The way you structure your schema can significantly affect how quickly your database performs. Understanding database engines, indexing strategies, and partitioning can help optimize performance.

## Regrets [(00:11:25)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=685s)
- Nuri Halperin emphasizes the importance of avoiding regrets in database design, meaning making decisions today that won't cause problems tomorrow.
- He shares his regrets from past experiences, including using the Entity-Attribute-Value (EAV) model, which he found to be overly complex and unsuitable for relational databases.
- He also regrets situations where changes to the database required significant downtime, leading to disruptions in applications and increased workload.

## Impact of change [(00:12:35)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=755s)
- Impact of DDL Changes: The speaker discusses the impact of changes made to the data definition language (DDL), which defines the structure of tables in a database. They emphasize that the cost of a change depends on the interconnectedness of the table with other tables.
- Cost of Different DDL Operations: Creating a new table is generally inexpensive, while dropping a table can be more costly if it has relationships with other tables. Adding a column with a null value is considered low-cost, but populating it with values can be more expensive, especially for large tables. Changes to columns involved in key constraints or foreign keys can be complex and require careful consideration.
- Importance of Mapping Change Impact: The speaker suggests that it's beneficial to mentally map the potential impact of changes to the database schema. This helps in understanding the cost of a change and making informed design decisions. By considering the potential for future changes, developers can design schemas that are more adaptable and less prone to costly modifications.

## Data types [(00:16:25)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=985s)
- Opaque data types are data types that don't represent a single thing or don't represent anything meaningful to the database. For example, storing a full name as a single string field makes it difficult for the database to perform operations like sorting by last name. It's better to break down the full name into its constituent parts (first name, last name, middle name) for better data management.
- Blob data types are also problematic because they are essentially raw data that the database cannot interpret. This includes things like images, binary data, and byte strings. It's best to store these types of data in a separate system like a file system or cloud storage and store a pointer to the data in the database.
- Incorrect data types can lead to issues with data comparison and manipulation. For example, storing dates as strings can make it difficult to perform date-related operations like sorting or calculating differences. It's best to use the appropriate data type for the data you are storing, such as a date or timestamp data type for dates.
- Non-domain values are values that don't belong to the defined domain of a column. For example, using a "0" value to represent an unknown country code is incorrect because "0" is not a valid country code. It's better to use a null value or a separate category for unknown values. This ensures that the database can properly handle comparisons and operations on the data.

## How to fix data types [(00:21:55)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=1315s)
- The speaker discusses the challenges of using opaque data types in SQL, highlighting that the language is not designed for this purpose.
- These data types lead to limited support, making it difficult to work with and understand the data.
- The speaker emphasizes that using opaque data types introduces unnecessary complexity and logic, which can become difficult to manage and maintain throughout the organization.

## Denormalization [(00:22:34)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=1354s)
- The speaker introduces a method for designing database schemas that resembles denormalization but avoids the term "denormalization" itself.
- The method starts by examining a value in the domain and determining if it is atomic, meaning it can be directly mapped to a SQL data type. If it is atomic, the process is complete.
- If the value is not atomic, the speaker suggests analyzing its non-atomicity. If the value is a set of properties (like a dictionary), it should be represented as a key-value pair, with each key becoming a column in the database. The process then repeats for the value associated with each key, checking if it is atomic. If not, the process continues to break down the value into its atomic components.

## Multientity table [(00:25:13)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=1513s)
- The chapter discusses the concept of a "multi-entity table," which is a generalized table that attempts to store both parent and child data within a single row.
- This type of table is often identifiable by rows that exhibit a pattern of null values in certain columns, with these null values alternating between rows.
- The speaker acknowledges the difficulty in explaining this concept verbally and suggests using an example to illustrate it further.

## Catalog item example [(00:26:05)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=1565s)
- The speaker describes a table representing catalog items, which have a unique SKU code, a name, and size information.
- The table includes both numeric and letter size columns, but these are not always populated for all items. For example, a shirt might have a letter size but not a numeric size, while pants might have a numeric size but not a letter size.
- This difference in data representation reflects the inherent differences between products in the real world. Shirts and pants are manufactured and designed differently, and therefore require different size specifications. Despite these differences, the speaker has chosen to represent them in a single table, potentially leading to data inconsistencies and challenges in querying and analysis.

## How to fix this [(00:27:48)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=1668s)
- To address the issue of null values in a database schema, the speaker suggests creating separate tables for different types of catalog items, such as numeric size catalog items and letter size catalog items. This eliminates the need for null values as each table will only contain data relevant to its specific type.
- By establishing relationships between these tables, data can be joined effectively, ensuring that relevant information is always present. This approach allows for clear identification of item types based on the presence of specific columns and their associated values.
- The speaker emphasizes the importance of avoiding "OPEC" data types, which involve storing data as strings and relying on the application to handle interpretation. This approach can lead to inconsistencies in sorting and other data operations, making it less efficient and potentially problematic.

## Abnormal Form [(00:30:11)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=1811s)
- The "Abnormal Form" problem arises when data is not stored atomically and in its proper tables. This leads to issues like storing exam scores directly within the enrollment table, which limits the number of exams per semester and creates null values for exams that haven't occurred yet.
- This approach results in several negative consequences:
 - Sparse columns: Columns with many null values, which can decrease flexibility and query performance.
 - Duplicated data: Storing teacher information within the enrollment table instead of referencing a separate teacher table leads to data duplication and consistency issues.
 - Predicting the future: The design assumes future events, like the completion of courses or the need for teaching assistants, which may not be accurate.
 - Decreased query optimization: Null values in columns make it difficult for query optimizers to efficiently determine the best execution plan, leading to slower queries.
 - Increased index size: Indexes need to include references to null values, increasing their size and potentially impacting performance.
 - Lock contention: Updating multi-entity tables with abnormal form can lead to higher-level table locks, slowing down other operations.
 - Complex queries: Queries become more complex and require additional logic to handle null values and different scenarios, making them harder to write and maintain.

## References [(00:36:28)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=2188s)
- Natural keys are observable in the real world and exist in the model. They are meaningful and part of the model. Examples include ISO two-letter codes for countries or user names on a platform.
- Artificial keys are meaningful in the real world but are foreign to the entity itself. They are associated with the entity but not inherent to it. An example is a person's citizenship, which is associated with them but not part of their identity.
- Exposed locators are identifiers that exist in the database but not in the real world. These include primary keys, row IDs, and UUIDs. They are only meaningful to the database engine and can lead to drift and collisions in different environments.
- Real surrogate keys are identifiers that are not even exposed to programmers. They are used internally by the database for storage purposes and should not be used for primary keys.
- Using meaningless keys (artificial or exposed locators) can lead to increased complexity in the database. It requires more joins to access related information, increases the number of indexes and tables, and can impact clustering indexing efficiency.
- Natural keys are preferable because they are meaningful and readily available in the data. They eliminate the need for joins and simplify data access.
- The impact of changing a natural key depends on the nature of the change. Additive changes are similar to adding a new column, while changes to the primary key can have cascading effects.
- The decision to use natural or artificial keys should be based on the specific use case and the potential pain points associated with each approach.
- Domain tables can be avoided by using constraints to enforce domain values, reducing the need for separate tables to store domain information.
- The impact of using sequences for primary keys can vary depending on the database engine. In some cases, it can create hotspots due to frequent updates at the end of the table.
- Understanding the specific behavior of the database engine is crucial when choosing primary key strategies and considering the potential impact on performance and data integrity.

## Sequential Keys [(00:45:36)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=2736s)
- Sequential primary keys, also known as auto-generated keys and sequences, are surrogate keys that lack real-world meaning. They are simply invented identifiers assigned to objects, making them difficult to migrate between systems. This can lead to issues when trying to replicate production data in development environments, as collisions between keys can occur.
- Sequential keys can cause synchronization problems between different systems. If a key is meaningless in one system, it may not have the same meaning in another, leading to inconsistencies and data conflicts.
- Sequential keys can also create hotspots and drift between environments. This can cause significant problems, especially when trying to migrate schemas. The text also mentions that sequential keys are essentially "exposed locators," which are different from surrogate keys.

## Primary Keys [(00:48:09)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=2889s)
- A primary key should be meaningful and easily understood by someone familiar with the domain. This means it should be something like an email address, username, or a unique identifier that makes sense in the context of the data.
- A primary key should be stable, meaning it rarely changes. While it's not immutable forever, changes should be infrequent and handled with care. Most relational and NoSQL databases require primary keys to be immutable, and those that support transactions allow changes under a transaction cover.
- A primary key should be convenient, meaning it's simple, compact, and easy to work with. Avoid complex combinations of multiple columns or data that requires extensive logic to generate. The primary key should be straightforward and appear consistently in queries for efficient data retrieval.

## ORM [(00:50:58)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=3058s)
- ORMs (Object-Relational Mappers) are a popular tool for developers, but they can lead to problems when used for database management. While ORMs simplify the process of interacting with databases by mapping database tables to classes, they can create a disconnect between the database schema and the application's object model.
- ORMs encourage the "repo pattern," where data is loaded into memory and treated as objects. This can result in inefficient queries and heavy operations, as the database engine is unable to optimize for the in-memory manipulation of data.
- ORMs can lead to rigidity and difficulty in making changes to the database schema. Changes to the database schema require corresponding changes to the ORM-generated classes, which can be complex and time-consuming. This can also lead to concurrency issues, as changes made to the database may not be reflected in the in-memory objects.

## RMS [(00:55:57)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=3357s)
- The speaker, a consultant, acknowledges that the usefulness of ORMs (Object-Relational Mappers) can vary depending on the context. 
- They highlight some benefits of ORMs, such as connection management, connection pooling, and mapping between tabular data and programming language types.
- However, the speaker expresses strong dislike for the command marshalling aspect of ORMs, finding it unnecessary and preferring to use the database driver directly for stored procedures and functions. They also find the abstractions provided by ORMs, like repository patterns, to be ultimately counterproductive. Additionally, they find change detection and concurrency handling features of ORMs to be frustrating and not enjoyable to work with.

## Adhoc DDL [(00:57:47)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=3467s)
- The chapter discusses the issue of "ad hoc DDL," which refers to the practice of manually adding columns to a database schema without a structured process.
- The speaker highlights the lack of repeatability and reliability associated with manual DDL changes. This makes it difficult to automate the process, replicate changes across different environments, and track the history of modifications.
- The speaker emphasizes the potential for confusion and troubleshooting difficulties when manual changes are made without proper documentation. This can lead to situations where it's unclear who made the change, when it occurred, and why, making it challenging to identify the root cause of issues.

## Migration scripts [(00:58:42)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=3522s)
- The speaker recommends using migration scripts for database changes, suggesting popular tools like Flyway and Liquibase.
- Migration scripts are stored as files, allowing for on-demand execution and rollback functionality in case of errors.
- The speaker emphasizes the importance of automation and CI/CD for database changes, which migration scripts facilitate.

## Summary [(00:59:33)](https://www.youtube.com/watch?v=iDWwoz9ZUzw&t=3573s)
- The speaker recommends using natural keys whenever possible, as this aligns with the intended use of relational databases.
- They advocate for storing atomic values and normalized data, using concise data types to represent information effectively.
- The speaker discourages the use of JSON and XML within relational databases, suggesting that document databases might be a better fit for such data. They also express a preference for avoiding ORMs, highlighting the potential for conflicts and the need to bypass them in certain situations.

