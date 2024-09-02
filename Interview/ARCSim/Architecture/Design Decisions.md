==Important to think of the disadvantages of each decision made.==

### Why was run groups done per shock ?
- Required format by downstream teams like risk management
- Easier for them to make decision early on.

### Store results as Hexadecimal
- Compactness compared to binary and decimal systems.
- A single hexadecimal digit can represent a group of four binary digits.
- The results output of the Calculation Kernel contains numerical values so it's a perfect fit.

### MSMQ
- Reliable persistent backing store
- System Restarts
- Asynchronous tasks are added to the thread pool via MSMQ, ensuring the first triggered is the first added to the pool. 

### .NET Framework vs .NET Core
- .NET Core had more advanced features
- More lightweight
- Recommended by Microsoft going forward.

### Queue Table vs MSMQ
- .NET Core does not support MSMQ
- Queue table approach but a limit of 20 rows to manage load.

### How where errors handled ?
- An error in a step of an action would cause subsequent actions of the same run group to halt.

### Why use Console over Service class
- Already had Console setup from initial version

### Why not use a Queue for Console -> GUI communication
- GUI specifically designed for incoming HTTP requests.
- Difficult to design if listening on a Queue

### Angular
- Needed an SPA
- A lot of stuff happening in real-time
- Disadvantages
	- Limited hiring pool
	- Steep learning curve

### Why Angular over Blazor ?
- UI very complex, Blazor was limited at the time.

### Angular vs other languages like React
- [[Interview Questions - Angular#Questions: Framework Comparison|Framework Comparison]]

### NGRX vs NGXS
- Initially used NGRX but felt it was too much boilerplate code
- Then start using NGXS to reduce boilerplate code.
- More Angular friendly.

### AWS vs Azure
- Rest of business was moving to AWS

### C#/.NET vs other languages (Java, etc)
- Web API functionality
- Standard and a high level language that easily supports web applications.

### Python
- Intuitive language to develop in for both software engineers and actuaries, 
- Quick to perform mathematical calculation (matrix multiplication), 
	- Uses the extension capabilities of C based libraries such as NumPy to do so.
- Financial Industry Standard