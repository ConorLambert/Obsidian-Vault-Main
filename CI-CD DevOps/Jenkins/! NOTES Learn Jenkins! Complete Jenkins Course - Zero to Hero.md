[Source](https://www.youtube.com/watch?v=6YZvp2GwT0A)

### Master Server and Agents
[ChatGPT Source](https://chatgpt.com/c/66da0706-b5bc-8012-bcce-59468a9d7f86)
- Master Server manages, distributes and schedules builds.  
- Agents execute the builds. 
	- Workhorses that run your actual builds
- Example
	- Commit is made by
	- Master Server becomes aware of this commit and triggers pipeline
	- Agent selected based on Configured labels
	- Agent distributed to run build

### Agent Types
- Permanent Agents
	- Standalone windows or linux servers configured to run Jenkins jobs
	- Make sure to have the following installed on the servers
		- Need SSH installed as Master Server connects via SSH
		- Build tools used by Jenkins (Maven, Gradle)
- Cloud Agents
	- More popular choice
	- Docker, Kubernetes
	- Jenkins can dynamically spin up agents based on the agent templates you configured

### Build Types
- Freestyle Build Projects
	- Simplest way to start of with Jenkins
	- Shell scripts that run on the server that respond to specific events e.g code commit
- Pipelines
	- Use Jenkins files written in the groovy syntax to specify what happens during the build 
	- Pipelines are commonly broken into different stages:
```groovy
stages [
	stage('Clone') {
		step {
			...
		}
	}
	stage('Build') {
		step {
			...
		}
	}
	stage('Test') {
		step {
			...
		}
	}
	stage('Package') {
		step {
			...
		}
	}
	stage('Deploy') {
		step {
			...
		}
	}
]
```

### Common Items
- Mostly deal with Freestyle Projects and Pipelines
![[Pasted image 20240909180943.png|500]]

### Naming Conventions
- Don't use spaces in the name (Use underscores and dashes)
- Jenkins will create a folder based on this name.

### Settings
###### Build Triggers
- What is triggering your job
- Common options
	- Build periodically
		- Like a cron Job
		- Schedule a repeated time that Jenkins will run your job
	- GitHub hook triggers
		- Sends a web hook to your Jenkins server.
		- Difficult if firewall is in the way
	- Poll SCM
		- Jenkins will periodically reach out to GitHub
###### Build Environment
- Common options
	- Delete workspace before build starts
		- Delete artefacts left over from last run
		- This could be a text or log file that was generated from the previous run
###### Post-build Actions
- Common Options
	- Generate reports
	- Change GitHub Status
	- Send Email

### Workspace
- Actual folder in the Jenkins directory
- Contains a sub-folder for each job we have created
- Each sub-folder contains the generated artefacts for our run.
- Common to access this folder via SSH/CMD to troubleshoot.