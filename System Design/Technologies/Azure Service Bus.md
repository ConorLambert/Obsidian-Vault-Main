[Source](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview)
## Overview
- Azure Service Bus is a fully managed enterprise message broker with [[Message Queue]]s and [[Publish-Subscribe]] topics. 
- Service Bus is used to decouple applications and services from each other, providing the following benefits:
	- Load-balancing work across competing workers
	- Safely routing and transferring data and control across service and application boundaries
	- Coordinating transactional work that requires a high-degree of reliability
- Service Bus is serverless messaging.
- Service Bus is a platform-as-a-service (PaaS) offering

## Comparison and Advantages
- Concepts are similar to other message brokers like Apache ActiveMQ. 
- The difference is that Azure takes care of those chores for you:
	- Worrying about hardware failures
	- Keeping the operating systems or the products patched
	- Placing logs and managing disk space
	- Handling backups
	- Failing over to a reserve machine

## Use Cases
- List [here](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-messaging-overview#overview)

## Concepts
##### Messages
- Data is transferred between different applications and services using messages. 
- A message is a container decorated with metadata, and contains data. 
- The data can be any kind of information, including structured data encoded with the common formats such as the following ones: JSON, XML, Apache Avro, Plain Text.

##### Queue
- Messages are sent to and received from queues. 
- Queues store messages until the receiving application is available to receive and process them.
- Queues is often used for [[Point-to-Point Communication]].

![[Pasted image 20240719150149.png|400]]

##### Topic
- Used instead of a Queue to send and receive messages. 
- Useful in [[Publish-Subscribe]] scenarios.
- Can have multiple, independent subscriptions, which attach to the topic and otherwise work exactly like queues from the receiver side. 
- A subscriber to a topic can receive a copy of each message sent to that topic.
- You can define rules on a subscription. 
	- A subscription rule has a filter to define a condition for the message to be copied into the subscription and an optional action that can modify message metadata.

![[Pasted image 20240719150205.png|400]]

##### Namespace
- A namespace is a container for all messaging components (queues and topics). 
- A namespace can have one or more queues and topics and it often serves as an application container.
- A Service Bus namespace is your own capacity slice of a large cluster made up of dozens of all-active virtual machines. 
- It optionally spans three Azure [[Availability Zones]]. So, you get all the availability and robustness benefits of running the message broker at enormous scale. And, you don't need to worry about underlying complexities. 