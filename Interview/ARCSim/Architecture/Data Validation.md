Data Validator operates in 3 main steps:
1. **Extract:** Retrieve data from file server and apply minor transformation to formatting
2. **Correct:** Checks that the provided data is complete and well formed (will be accepted by the Model). This is done using Manual Corrections which are user-defined and managed on the front-end. 
	- General data transformation at source has been the cause of issues in the past so it is preferable to have all rules defined and viewable by the user.
3. **Validate:** Joins all valid data from the multiple validated tables into a single data source that is easily searchable.
	- The complexity of the source files has been merged into a policy specific and fund specific set of tables. Views are provided to allow for user searches.