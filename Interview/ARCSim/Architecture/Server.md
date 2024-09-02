### AWS
##### Overview
- Predefined list of servers
- `aws-arcsim-001` all the way to `aws-arcsim-030`

##### Spot Servers
[ChatGPT Source](https://chatgpt.com/c/715593fe-20e6-4a51-a33c-92740fd7a582)
- Bid on unused EC2 capacity.
- A small number given to us.
- Used mostly for testing something out.

##### How where they scaled ?
- All predefined servers had tickbox beside them on admin panel
- Admins can add and remove servers to pool of servers as needed.

##### How did Console Monitor Server Usage ?
- For some server A, Console will check against other runs in the queue that are using server A and see if there is enough room for another run.

##### How did Console know about new servers available ?
- The `GetAvailableServers` method would continuously poll the Configuration table for the row associated with available servers and see if any of those servers where in use
	- Called on Console startup and periodically in WorkerStepPoll
- Not ideal but it did allow us to not recompile or restart console to pick up changes.

### Specs
##### Worker Servers
- 32 Physical Cores
- 64 GB memory
##### Host Servers
- On-Prem
	- Virtual
	- 16 cores
	- 32 GB RAM
	- 500 GB
- AWS
	- Virtual
	- 16 cores
	- 32 GB RAM
	- 100 GB
##### AWS Database
- 1TB

### Installed Applications
- `PyCharm` on the worker servers so we could debug packages.

### Installation Setup
- Install .NET Hosting Bundle

### Naming Conventions
###### Overview
- Development started with `d`
- Integration started with `i`
- Production started with `p`
###### Examples
Worker Servers
- aws-arcsim-001
- ...
- aws-arcsim-030
- aws-arcsim-sp01 (Spot instance)
- aws-arcsim-sp02 (Spot instance)
Application Servers
- aws-arcapp-d01 (development)
- aws-arcapp-i01 (integration)
- aws-arcapp-p01 (production)
Database
- aws-arcsql-d01 (development)
- aws-arcsql-i01 (integration)
- aws-arcsql-p01 (production)



### On-Prem
###### Setup
- A number of virtual servers to host applications and database
	- Development
	- Integration
	- Production
- Number of physical servers
	- dub-arcsim-p01
	- dub-hedging-p01
	- dub-hedging-p02
	- dub-prophet-p05
	- dub-prophet-p06

