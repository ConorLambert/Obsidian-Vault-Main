### Logging
- [[Logging]]

### Angular
[ChatGPT Source](https://chatgpt.com/c/9a38a8a6-3046-496d-b6bd-5bc6ed872919)
- Service calls
	- HTTP Interceptors
- Global Error Handler (using `ErrorHandler` provider)
- Friendly display message using Material Snackbar

### .NET
###### GUI
- Always logged to GUI.Log.Error
- `Filter` used to handle errors around the controller endpoint outside of Application layer logic
- Each CQRS handler in the Application layer had its own try/catch exceptions
###### Console
- Always logged to Console.Log.Error
- Each step had try catch block
- Initial part of Program.cs to catch any unhandled exceptions
- Other methods had their own try/catch blocks where needed

### Python
- error.txt contains the stack trace
- Manually log onto server, setup project in specific state
	- Number of sims 1
	- Output: CSV
- Debug project in PyCharm installed on the server
- Kill all the processes in TaskManager on server machine