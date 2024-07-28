### Overview
- A container is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another.
- Containers include all the dependencies that an application might need to run on *any* host operating system, such as libraries, binaries, configuration files, and frameworks, into a single lightweight executable.
- Containers can run on any host operating system and are isolated from other software and hardware objects, making them versatile tools to build applications that can be built once and run anywhere.
- Multiple containers can run on the same machine and share the OS kernel with other containers, each running as isolated processes in user space.


### Containers vs Virtual Machines

![[Pasted image 20240726152600.png]]
###### Containers
- Containers are an abstraction at the app layer
- Multiple containers can run on the same machine and share the OS kernel with other containers, each running as isolated processes in user space.
###### VMs
- VMs are an abstraction of physical hardware turning one server into many servers.
	- The hypervisor allows multiple VMs to run on a single machine.
- Each VM includes a full copy of an operating system, the application, necessary binaries and libraries – taking up tens of GBs. 

### Real World Examples
- From Google Search to YouTube and Gmail, everything at Google runs through containers.

### Technologies
- [[Kubernetes]]
- [[Docker]]
