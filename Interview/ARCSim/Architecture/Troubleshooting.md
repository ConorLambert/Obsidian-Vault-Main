### Development
- During development, I would often have the **Diagnostic Tools** tool open to monitor the CPU and Memory usage (**.NET Memory Profiler**).
	- Needed in ARCSim due to large volumes of data.
- Also used **CPU Usage Tool** to find hot code paths.
	- More [info](https://learn.microsoft.com/en-us/visualstudio/profiling/profiling-feature-tour?view=vs-2022#analyze-cpu-usage) on how to do it?
	- CreateRunGroup had a lot going on.

### Production
- Notified by reporting team
	- Details like what screen it happened on.
- If error is related to a run, then get the `RunId`.
- Check front-end if error appears there
- Check logs on affected server
	- Check stack trace in the file.
- Check W**indows Event Viewer**
	- GUI.exe or Console.exe error
	- Related to abruptly ending 

### Compute Servers
- `error.txt` contains the stack trace
- Manually log onto server, setup project in PyCharm under specific state
	- Number of sims 1
	- Output: CSV
- Runs to the point of failure and stops, we can analyse the variables including panda dataframes throughout the call stack.
- Kill all the processes in TaskManager on server machine
	- Only needed if process didn't exit properly.