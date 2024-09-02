### How large was the database at any one time?
- 400-500 GB

### What was the capacity ?
- On-Prem was 500 GB
- AWS was increased to 1TB

### Where Indexes used and how ?
- **ConfigSet.RunDefinition** and **ConfigSet.Inputs** on `ConfigSetId` column
	- These rows where never changed once added

### Views
- We relied a lot on views

### Results Database
- Stored as Hexadecimal

### Stored Procedures
- For complex tasks that required quick completion, we used stored procedures
- Some examples
	- Archiving actions
	- Deleting run groups
	- Formatting data during Import phase.