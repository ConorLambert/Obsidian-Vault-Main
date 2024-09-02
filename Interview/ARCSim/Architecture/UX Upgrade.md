### Why was it needed ?
- Needed SPA
	- Having to keep refreshing the Queue page
- Controller over bloated with logic
- More and more different types of inputs where required
- Moving to AWS servers
- More actions/stages where needed (MPG)
- New business units where required
- So many inputs available, the process was becoming error prone
- More and more changes where made to the CalculationKernel (which was easier to update as it was hidden away from user) but front-end was not being updated to match it's new capabilities.


### Design Decisions

###### Onion Architecture
- Separate logic from controllers into Application layer
###### Angular
- SPA
- Don't have to refresh the page
###### No More MSMQ
- Wasn't available anymore
- Just used database table and polling system.
###### SharePoint
- At the time, the company was moving from OneDrive to SharePoint
- The Reporting team where heavy on SharePoint so we utilized this.

### What where the performance benefits ?
###### AWS Costs
- ??? How much did we save
###### ReRun Metric
- 15 down to 3.
###### Less Issues Being Raised
- Not being bothered as much.