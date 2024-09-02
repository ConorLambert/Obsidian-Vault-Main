==Might need to update this to match CI/CD== 

### Agile
- 3 week release schedule target

### Requirements Management
- JIRA
- Add bugs/new feature request
- Prioritise
- Track status of request

### Release Approach
- Development
	- Complete development and unit tests for each feature/bug fix
- Release package
	- A release package is created and validated (Tracked in JIRA).
- BAU
	- Release Package is then applied to an integration environment and parallel (daily) processing is carried out for multiple days.
- UAT
	- Carried out on integration environment
	- Manual process where the operations team follows a testing script to make sure the buttons et al do as expected.
- Testing is signed off and a release note is created in JIRA that links the Development and the Testing JIRAs.
- The release note contains instructions on how to execute and validate the release package.
- IT execute release package on server using their elevated credentials.
- Post Release
	- Number of manual post release tests are carried out to ensure release was successful.

### Testing Approach
- Unit tests (automated)
	- Used xUnit
- Integration test (manual)
- UAT (manual)
	- Duplicate run groups and re-run comparing the results
	- Check new functionality is working as expected

### Who tests it ?
- Actuarial reporting team
