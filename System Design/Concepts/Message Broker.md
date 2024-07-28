### Overview
- A message broker is software that enables applications, systems, and services to communicate with each other and exchange information. 
- The message broker does this by translating messages between formal messaging protocols. This allows interdependent services to “talk” with one another directly, even if they were written in different languages or implemented on different platforms.
- A software application uses the message broker protocol to send and receive messages to a central store, the message broker. The message broker store these messages in a [[message queue]] which stores and orders the messages until any application requests it. 
- Used synonymously with [[Message Queue]].

## Terminology
###### Message Ordering:
- Most Queues are FIFO but this can be configured.
###### Retry Mechanisms:
- A retry mechanism can be configured if a message fails to be sent to the Queue.
###### Dead Letter Queues:
- Store messages that cannot be processed
- Useful for debugging and auditing
	- Can inspect messages to see why they weren't processed.
###### Scaling with Partitions:
- Queues can be partitioned across multiple servers.
###### Backpressure:
- Slowing down the production of messages when the Queue is overwhelmed.
- Can slow down the rate at which messages are accepted or return errors to the sender.

## Use Cases
###### Point-to-point Communication: 
- Point-to-point application integration *at a small scale*
	- Doing so at a larger scale can cause serious headaches
###### Buffer for Bursty Traffic: 
- In a ride-sharing application like Uber, queues can be used to manage sudden surges in ride requests. 
- During peak hours or special events, ride requests can spike massively. 
- A queue buffers these incoming requests, allowing the system to process them at a manageable rate without overloading the server or degrading the user experience.
###### Distribute Work Across a System: 
- In a cloud-based photo processing service, queues can be used to distribute expensive image processing tasks. 
- When a user uploads photos for editing or filtering, these tasks are placed in a queue. 
- Different worker nodes then pull tasks from the queue, ensuring even distribution of workload and efficient use of computing resources.

## Synchronous Warning
- Be careful of introducing message queues into synchronous workloads. 
- If you have strong latency requirements (e.g. < 500ms), introducing a message queue will likely break your latency constraints.
- A [[Stream]] might be better suited here.
	- Also, check out [[Apache Kafka vs RabbitMQ]].

## Technologies
- [[Apache Kafka]]
- [[AWS Simple Queue Service (SQS)|SQS]]. 
- [[RabbitMQ]]