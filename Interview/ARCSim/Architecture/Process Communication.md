### Console -> GUI
- HTTP POST Request
	- Console -> GUI
	- `HTTPClient`

### GUI -> Console
- MSMQ (v1)
- Queue table (v2)
	- Console processed only 30 queue entries at a time
		- Ordered by ActionOrderId so early actions in all run groups where processed first.

### Console -> AWS Servers
- Copy run package to worker server including the KernelConfig.xml.
- Create a batch file with a command to run the `Main.py` and place that into the root of the run package folder on the server.
- Then we need to execute the batch file on a remote server using WMI functionality provided by .NET:
	- `WMI` stands for `Windows Management Instrumentation` and contains many uses but in our case, it was used for *remote management operations*.
	- In particular, we created a `ManagementClass`, which is a WMI class, to represent a `Win32_Process` process.
	- You can set command line arguments to this process process. The command line arguments we used where to run the batch file located inside the run package.
	- We create the process itself using the `InvokeMethod` of the `ManagementClass` instance and analyse the result to see if the process was created successfully and if not, handle the error.

### AWS Servers -> Console
- Console goes into while loop that ends when a `complete.txt` or `error.txt` is created inside the package on the server:
	- Inside this loop it will check `output.txt` file inside the package on the server for log information that we can update the front-end with.

### GUI -> Client
- SignalR
	- GUI -> Angular
	- `SignalR.IHubContext` (C#)
	- `@aspnet/signalr` (Angular)
- The User Interface required live information on the status/progress of current runs.
- These runs where managed by the Console.
- When a run progressed or failed in some way, the Console would issue a HTTP request to the to a controller action in the GUI layer. 
- The GUI would pass the request onto the Application layer (following the Onion Architecture) where a SignalR request would be formulated to send onto the client browser.
- Angular was listening via an RxJS request in a singleton service.
- We had a component with a table displaying the live progress information
- This component would react to updates in the singleton service and update the table accordingly.