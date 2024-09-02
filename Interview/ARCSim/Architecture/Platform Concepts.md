### Run Group
Taken from demo script I done:
- A run group is an isolated container with its own actions and configuration settings.
- Any changes made to one run group does not have affect the changes in any other run group.
- This also means you could have UserA working on RunGroupA, UserB working on RunGroupB and so on.
### RunGroupId
- Used to uniquely identify a run group
### RunId
- Every run across all run groups have a unique identifier.
- Also useful for error handling .
### Valuation Date
- The base date to which the projection to start from.
### Run Group Version
- Snapshot of run groups state.
- Incremented per re-run
- Useful for Run Group Compare feature
### SubRunName
- Represents the Shocks
	- MortalityUp
	- MortalityDown




