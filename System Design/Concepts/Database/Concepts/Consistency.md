### Overview
- Pertains to how much your users can tolerate getting stale data. 
- A **strongly** consistent system will ensure that, after the data is written, all subsequent reads will reflect that write. 
- A **weakly** consistent or more commonly **eventually** consistent system will not make this guarantee, instead allowing for a period of time where the data is stale.

### Mixture
- Most real-life systems don't require **strong** consistency everywhere. 
- For example, a social media feed can be **eventually** consistent:
	- If you post a tweet, it's okay if it takes a few seconds for your followers to see it. 
- However, a banking system needs to be **strongly** consistent
	- If you transfer money from one account to another, it's not okay if the money disappears from one account and doesn't appear in the other.