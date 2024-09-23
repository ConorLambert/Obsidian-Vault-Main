[Source](https://courses.dometrain.com/courses/take/getting-started-solution-architecture/lessons/54121793-welcome)

## Design Patterns
##### Thinking in Patterns
- Think patterns first, not specific services or implementation details (e.g. AWS services)
	- Think in an abstract way and avoid implementation details
- Gather the business requirements you have and use that to apply patterns.
	- From there, add the required services you might need
- Allows people to understand your architectural intention
	- For example, if your design has a Queue then other people can see that availability is important. The Queue acts as a buffer so that must mean you also require durability. 

##### API First Design
- Avoid developing the domain model before the API
- This can lead to a leaky abstraction
	- You want to hide your domain model to the outside world so you can develop it independently.
- You want to first describe the API 
	- API meaning the interface between two systems which includes REST over HTTP or events to an Event Bus.
- Collaborate with the team in question and discuss what the contract between the two systems will look like.
	- Both teams can now implement this functionality separately 
- Service orientated architecture where each service is managed by a team. Both teams communicate to decide contract.
- Also handy in a Layered Architecture where you have front-end and back-end teams:
	- Agree on API first so FE team can temporarily mock out request/response and BE team can implement business logic based on request/response
- MY NOTE: This conflicts with System Design In a Hurry
		- It does Core entities before API.
		- Maybe this Dometrain module applies to lower level design ?

##### Streaming vs Batch Processing
- Both styles used when building point-to-point integration.
	- One system to one other system
- Both can do the same thing
	- *Producers* and *consumers* communicating over a *channel*
- Stream
	- Constant continuous stream of data.
	- Allows you to process the data as it arrives in real-time.
- Batch processing runs on some type of *schedule*
	- Consumer will do some work on a scheduled time and at that scheduled time, it will trigger and reach out and process through the data. Once its processed the data, it will shutdown or wait for the next schedule.
- Use Cases
	- Batch Processing
		- Plant based pizza needs to periodically check it's inventory levels so it doesn't run out of ingredients. We don't wan't to make 100s of small orders but instead. We could run a batch process at the end of each day that checks inventory levels and if these levels are low, then perform an order.
	- Stream Processing
		- Plant-based pizza needs the orders to be monitored as they come in to check for fraudulent orders. In this case, we need to check it in real-time.
- Both can work in conjunction also
- Always choose based on business requirements.

##### Integration Styles
- Approaches to integrate two systems together. 
- File Transfer (File Format Integration)
	- System A sends file to some file server where System B then reads that file from the server.
	- Agree to file format (API first design)
	- Can be extremely decoupled if done well
	- A lot of systems use this with good results
	- Advantages
		- Simple and easy way to get started.
	- Disadvantages
		- Slow
		- Error prone
			- *Athora used this for source file imports*
- Shared Database
	- System A reads/writes to database, System B reads/writes to the same database.
	- Common in monolith applications
	- Should not be used in Microservices architecture.
	- Athora used this for Queue system
	- Advantages
		- Highly concurrent
	- Disadvantages
		- Deciding on a schema
			- Okay when small but hard to change as it grows
- Remote Procedure Call (RPC)
	- One system makes a call to another system remotely
	- Done using HTTP method (REST, gRPC)
	- Each system is developed independently but exposes an interface to those who want to communicate with it.
	- System orientated architecture can be built using entirely this approach
	- Also common in microservices.
	- Disadvantages
		- Vulnerable to failure because it involves a communication system, another machine and another process.
		- RPC systems aren't always suited for transferring large amounts of data.
- Message Based Integration
	- Best approach
	- Asynchronous
	- Channel in the middle. Producer and consumer on either side.
	- System A puts message onto bus, System B takes message of the bus.
	- Low coupling
		- Neither channel needs to know about the other or that it even exists.
	- Multiple consumers
	- Types of Message Channels
		- Point to point
			- One producer and one consumer
			- Very specific message
			- Implemented using something like a stream or some type of queue
			- More direct
		- Pub/sub
			- One producer puts messages onto message bus.
			- Multiple subscribers subscribe to the message bus with their own rules.
	- Can use two types together

##### Message and Reactive System Design
- Asynchronous message systems with a pub/sub in the middle are quite effective.
	- One system is not affected by the failure in another system.
- Can be difficult though
	- System A doesn't know if System B has processed it or if a message is missing.
- A heuristic that is good:
	- When communicating between different teams and microservices, default to a more publish/subscribe based communication. Make it asynchronous and decoupled as possible.
	- When your in a single domain, process or service, something that you have full control over, then use more durable message channels (e.g Point-to-Point)
	![[Pasted image 20240716105448.png|500]]

##### Architect for Failure
- "Everything fails all the time"
- Change and failure are the only constants in software development
- *It's not the boxes on the diagram that you need to worry about, it's the lines.*
- ==When designing, always ask yourself:==
	- "What would happen if this component failed"
	- "What would happen if a development team pushes out a release that contains a bug or slows down the latency".
- Options
	- Retry
		- If request fails, then resend the request
		- Important to increase the time exponentially for every subsequent retry request
			- Don't want to overload the system
				- It could have too many requests at that moment for example
		- Also add a Circuit Breaker so that retry requests stop after a certain limit.
- Always decide based on business requirements
	- We could have a system that needs to be available 24 hours a day, 365 days a year.
		- In this case, we could use multi-regional architecture where if one region is down, traffic is redirected to another region
		- *But the cost, complexity and effort to do this is immense.*

##### Integrating with External Systems
- Not all coupling is bad
	- Sometimes it may suit the situation at hand particularly if you have full control over those sub-systems
- Low coupling is absolutely needed when dealing with something external to your system such as third-party APIs.
- Options
	- Integration layer or Anti-Corruption layer
		![[Pasted image 20240718103227.png|300]]
		- Sits between your sub-systems and the external API
		- Reads data from external API and translates it into something your internal system understands
		- The internal system is kept away from the details of the external API so that any changes to the external API *will only require changes to the Integration layer*.
	- Cache
		- When reading data from 3rd party API, write it to a local cache so that the systems will always read from the cache. If the 3rd party API is down, then the systems will read from the cache.

## Documenting Decisions
##### Architecture Decision Records (ADR)
[Source](https://courses.dometrain.com/courses/take/getting-started-solution-architecture/lessons/54122128-architecture-decision-records)
- Document about why you made a decision *at that point in time*.
- Here is an example [repository](https://github.com/joelparkerhenderson/architecture-decision-record?tab=readme-ov-file) that details ADRs made on numerous things like database technologies, CSS frameworks, why certain languages where chosen, etc
- An ADR is *immutable*. 
	- If you change your mind on something, you create a new ADR and reference back to the previous one.

##### Documenting Use Cases
- Short and easy to read Use Case stories are effective
- Step by step of what the user needs to do in your system.
- Each Use Case you write, adds another piece to the puzzle

##### Architect in Patterns
- Notice any common patterns based on the characteristics of the system detailed in the requirements.
- Document these patterns and why they would work.
- Don't delve into specific technologies or services (Kafka, DynamoDB, etc).

##### The Importance of Context
- Make sure you include the wider context of the system in your architectural diagrams.
- Think about the other things that your little component needs to communicate with.
- If making a change later on, you can see from the diagram what other parts will be affected.
- Also good for new people joining the team.

##### Context Mapping
- Shows the communication patterns between teams
- Logical grouping around the functionality.
- *You have the same concepts, but within the different contexts it means something different.*
- Can give you insight into organisational issues.

##### The Importance of Interoperability
- Embrace standards and protocols that are common and open
	- REST, HTTP, etc 
- Design user-friendly APIs 
- Consider data format
	- JSON is good 
- Regular test schema interactions
- Provide good documentation on your interface in such a way that some third party can easily understand how to use it.

# Architecture Considerations
### Evolutionary as a default
- Change is a constant
- Ability to meet that change is a key differentiator
- *Evolveability is the most important -ility you need to consider in any software architecture*
- The key idea to evolutionary architecture is to define the characteristics important to your specific system.
- EA builds out whats called **Fitness Functions** which monitor that your system meets the characteristics that you defined as important.
- Can be automated
- Could be related to coupling or cohesion, availability or a whole matter of other things.
- Once these fitness functions and automation are in place, you can focus on **incremental change** which is another important part of evolutionary architecture.
- *Treat evolveability as a fundamental building block of your system.*

### The Importance of Observability
- You need to be able to see into your system.
- Therefore, observability is also a core part of your architecture.
- *A fundamental building block of observability is tracing.*
- This doesn't mean that it's just a bunch of log entries.
- Particularly in a distributed system, being able to trace a request across your system is something you will be happy to have once something goes wrong.
- Metrics should also be a key part of your system.
- However, *make sure the metrics focus on user happiness*
	- No point in having a metric that shows something good if it has no impact on the user.
	- Good user focused metrics are things like failed logins or orders taking a certain amount of time to process.
- Let the metrics be driven by the traces
	- Can analyse a subset of requests that might be taking a long time
		- Maybe a particular user has lot's of data in their requests.

### Fitness Functions
- Provides an objective integrity assessment of some architectural characteristic.
- Will be different per business
- Express your intent of your architecture.
- Collaborate closely with your developers to determine what is important and how to measure it.
	- An architectural characteristic might be that response times need to be no longer than 100ms. Don't just dump that on your dev team from your ivory tower. If it can't happen, why can't it happen ?
- Fitness functions can be automated or triggered manually. 
- Can only happen if you have clearly and explicitly defined business requirements that have guided your most important functional and non-functional requirements.
- We test our code as a normal part of the development process, *but we should also test our architectural decisions*.

### Human-Centric Architecture
- It's all of our responsibility to build more sustainable software.
- It's a way of thinking about your systems with a human focus.
- 4 human stakeholders in any software system:
	- Users
	- Business stakeholders
	- Developers
	- Wider human population
- Human-centric should be just as much of a default in all architectures as evolutionary is.
- First two seem obvious but we often forget about the developers.
- Last stakeholder should remind you of how much technology is used in the wider population. The generations in years to come that will need it to work.

# Architecture In Practice
### Architecture In Practice
[Source](https://courses.dometrain.com/courses/take/getting-started-solution-architecture/lessons/54122156-architecture-in-practice)
