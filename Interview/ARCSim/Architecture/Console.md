### Dependency Injection
- No DI needed in Console

### Hosting
- The Console is started by a Task Scheduler job in windows server
- This was so the console was run under the right credentials.
- Also needed it to kick back off if a restart happened
- IT had to setup tasks under their credentials.

### Polling
- Core functionality in console was polling
- Different polling methods all in their own threads
- Continuously checking the `dbo.Queue` table based on the `StatusId` column

### Run States
- Waiting
	- Another run needs to complete before this can start
- Triggered
	- Intermediary step between waiting and running.
	- Triggered poller would check CPU usage on host machine before setting to Running
- Running
	- CPU is executing the task.
- Completed

### Why not put status from Waiting to Running ?
- Triggered state had a load balance like feature to ensure not too many runs are happening.
- CPU usage has not breached the threshold.

### How was Console started and stopped
- Stopping
	- System.Diagnostics.Process
		- .GetProcessesByName
		- .Kill
- Starting
	- ProcessStartInfo
		- Console is started from Scheduled Tasks in windows
	- Process
		- .Start(processStartInfo)

### Dependency Injection
- No DI used in Console

### How to access to DbContext
```c#
	public ModellingDataDbContext GetModellingDataDbContext()
	{
var context = new ModellingDataDbContext(ConfigurationManager.ConnectionStrings["ModellingDataDb"].ConnectionString);
			return context;
		}
		catch (Exception ex)
		{
			Log.Error(ex);
			return null;
		}
	}
```

### Startup Process
- `SetCurrentDirectory()`
- `ConfigureServices()`
	- Logging
- `PopulateServers()`
	- Read from configuration table
	- Called repeatedly in `WorkerStepPoller` to see if new servers added again.
- `StartMessageQueuePollers()`
	- All execute in their own threads
		- `PreReqPoller()`
		- `StandardStepPoller()`
		- `WorkerStepPoller()`
- `SetupConsole()`
	- Listen for cancel keystrokes

### Finding Available Servers
- Goal is to get list of candidate servers and choose one
- GetAvailableServers
	- Check available servers based on *number of cores a run requires*
		- Iterate through available servers (checked servers on admin screen)
		- Checking any current runs are using that server and how many cores it's using.
- In the case of AWS, check when the server was turned on
	- Paid by the hour