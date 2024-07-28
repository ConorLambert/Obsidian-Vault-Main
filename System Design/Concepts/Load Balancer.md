### Overview
- A device that sits between the user and the server group and acts as an invisible facilitator, ensuring that all resource servers are used equally.

### Algorithms
- https://aws.amazon.com/what-is/load-balancing/
- Cloud Providers will handle this for you in most cases
- Round Robin
	- Each request is passed on to the adjacent server to the previously assigned request.
- Least Connection
	- Assigned to the server with fewest current connections
- Hash Balancing
	- A value is computed based on the request (userId, IP Address) and the result dictates what server will process the request.