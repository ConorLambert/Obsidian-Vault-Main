### Data Maintenance
- Archiving strategy.
- Disk space monitor that would send email if space threshold is breached
- AdminManager runs in console (in it's own thread) and checks space on local drive and sends email to administrator

### Typical concurrent users on the system
- 5

### AWS vs On-Prem
- Cost a lot more but we where planning on scaling up anyway due to onboarding of new business units.

### ARCSim vs Prophet
![[Pasted image 20240827150143.png|400]]

### Bottlenecks
- CalculationKernel
	- Most time intensive
	- Setting up run package
	- *Reading in external data*
- Data validation
	- Errors outside of platform control often caused re-runs to occur