# .NET App host technology and why ?
- Elastic Beanstalk
- `m5.4xlarge`
- Easier to setup and manage

# SQL Database host technology and why ?
- RDS
- Pricing (IT team decided the above pricing themselves, we just had a 1TB requirement)
	- General Purpose SSD. Pay 0.0127 by the hour per GB
	- Reserved Instances
		- Reserve a DB instance for a one to three years and get a discount.
- Come pre-installed with SQL Server

# Compute Instance technology and why ?
- EC2
- C5

# Was it scaled ?
- No scaling
- Manually turned on and off servers from ARCSim Console

# How where deployments managed ?
##### Source Code
- From Visual Studio using the **AWS Toolkit**
- Explained in this [ChatGPT answer](https://chatgpt.com/c/f71c87cd-75ee-4eeb-abc2-8486f40acee8)
##### Database Changes
- ???

# How where test environments setup ?
- Integration/Staging environment (aws-arcapp-i01, aws-arcsql-i01)
- Take snapshot of **aws-arcsql-p01** onto **aws-arcsql-i01**
- Deploy changes to **i01** using **AWS Toolkit** from Visual Studio