### Overview
###### Sending
- Opening your message queue, sending a message, and closing the queue.
- Closed by the `using` statement (MessageQueue implements IDisposable)
###### Receiving
- Receiving messages generally happens asynchronously in MSMQ. 
- You add a `ReceiveCompleted` event to the queue and begin listening for new messages to arrive. 
- When a message arrives, your event is triggered, passed a message object, and you can then deserialize the body and process the contents. 
- Each time a message is received, the listening process stops. This helps provide a thread-safe environment. However, it also means it’s the developer’s responsibility to resume listening to the queue.
- Therefore, *the final call in the ReceiveCompleted function would be to start listening again for new messages.*

### Creating a Message Queue in Windows
- Computer Management -> Services and Applications
- Right click Public Queues, New-> Public Queue, give and name and press create.
- The name we have given will be used inside the C# code to reference that message queue.

### GUI
- Two approaches for sending
	- Fire and forget
	- Wait for response
		- `.SendResponse = true`
		- Examples are ArchiveActions, DeleteRunGroup, SignOffRunGroup
- GUI referenced two Message Queues, one for send and one for response (response queue only created when a response is required).
- We had a custom class called `MessageInfo`, containing all details needed for functioning of Message Queue (including the return queue).
	- Main property is `FunctionName` which would dictate what function is executed on the console end e.g. AddActions, ArchiveActions, etc

### Console
[Diagram](https://drive.google.com/file/d/17RExxkPQSQe4A39z_NLcoe3fAULw1O70/view?usp=sharing)
- On Console startup, the Message Queue is created and referenced
- The Message Queue has a specific name that matches the one we setup on the server.
- The Message Queue type has a `ReceiveCompletedEventHandler` which takes a delegate as parameter and this delegate is executed every time a message is received from the Message Queue.
- We created a custom function handler for this.
- Inside this custom function, a switch statement was used against the `FunctionName` property of `MessageInfo`. 
- `FunctionName` refers to what exact task is to be taken
- Some examples include
	- "AddActions"
	- "DeleteRunGroup"
- One of it's tasks is to add actions to the Queue but it is not the message queue that processes those actions. The pollers do this.
- *The Message Queue would add, remove data to/from the Queue table in an initial state. The Pollers continuously poll this table based on the StatusId to see what needs to be processed.*

### Priority
##### Overview
- Certain tasks where of higher importance
- Examples are "ArchiveAction", "ArchiveMultipeActions"
	- Others include "UpateQueueStatus"
		- Useful so progress to next step or action will be prioritised.
- *Tasks that when executed, can reclaim server resources or progress a run group further.*
##### How was priority handled
- Setting the `Priority` property of `Message` class to `MessagePriority.Highest`.
- MessageQueue would then add these items near the front of the Queue to be processed on the other end.

### How was messages encoded ?
- XmlMessageFormatter

### How where errors handled ?
- Poisoned Messages
	- E.g. file has incorrect format and that file is processed in other end of queue
		- If it fails and we retry, then it will result in the same error but clogs up resources
- In our case, we would not retry the process but instead investigate