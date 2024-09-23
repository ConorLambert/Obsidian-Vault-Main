# Server Setup
- **Jenkins** and **SVN** installed on same machine

# Jenkins Setup
- Created a multi-branch pipeline and pointed it at our Tortoise SVN repository
- Created a Server Side hook that triggers after a commit (`post-commit.tmpl`). 
- SVN hooks would trigger a Jenkins build
	- Setup configuration for this to work explained [here](https://stackoverflow.com/questions/29432076/how-do-i-trigger-jenkins-build-with-svn-post-commit).
- A new commit will contain code changes that need to be tested but could also contain a new branch. 
	- The former case will trigger build pipeline for that branch *but no deployment* (only testing)
	- The latter case will trigger the multi-branch pipeline creating pipelines for new branches.
- The above feature branch approach is done for each technology i.e. dotnet, Angular and Python.
- This means multiple pipeline entries exist on the dashboard for each feature branch of that technology.
	- dotnet-*feature-x*
	- dotnet-*feature-y*
	- angular-*feature-x*
	- angular-*feature-y*
- But there is a pipeline setup for the main branch that is auto-triggered after a merge request has completed successfully
	- Which occurs as a result of a new commit on the main branch
- This main branch perform builds, testing and deployment to the development environment
- There are two other pipelines for UAT and Prod but both of these are manual and Prod requires elevated access.

# Tortoise SVN and Jenkins
- Medium [article](https://prajjwalanandeesh.medium.com/automate-your-devops-with-jenkins-and-version-control-a-step-by-step-guide-e82eb0904fbf) on integrating them

# Tortoise SVN Webhooks
- https://stackoverflow.com/questions/42930025/adding-webhook-capability-to-svn-server
- https://tortoisesvn.net/docs/release/TortoiseSVN_en/tsvn-repository-hooks.html

# Deployment Pipeline
- Deployment Environments
	- Dev
		- Separate Pipeline
		- Automatically run after merge on main branch
	- UAT
		- Separate Pipeline
		- Run manually
	- Prod
		- Separate Pipeline
		- Run manually
		- Requires privileged access to run
- Post build: Send Email to actuarial developers summarizing the changes made
- How was each separate pipeline implemented
	- Answer [here](https://community.jenkins.io/t/separating-dev-qa-deployments-from-production/694/2) seems extensive
		- Use a shared library to hold common stages (such as build, test, deploy)
			- How to create a shared library is explained [here](https://medium.com/@mesagarkulkarni/jenkins-shared-library-0f1c2974b833)
		- Create separate pipelines for dev and prod
		- These separate pipelines would call into the shared pipeline and pass a parameter in indicating DEV or PROD
		- Restrict prod job.

# Database Changes
-  Ideas on how it should work:
	- [ChatGPT answer](https://chatgpt.com/c/66e2b51d-1a48-8012-ba07-13e527f92e04)
	- [Jenkins Pipeline For Deploying Database Changes Using Sqitch](https://www.youtube.com/watch?v=wF4PEe8HD7k)
	- https://documentation.red-gate.com/sca4/deploying-database-changes/continuous-integration
	- https://documentation.red-gate.com/sca4/deploying-database-changes/add-ons/jenkins/example-jenkins-ci-cd-pipeline
- How ours worked:
	- We didn't have a separate pipeline for Database
	- Instead, each feature branch would hold it's own database changes
	- The database changes would be applied as part of the main branch pipeline to the `dev` environment.

# Multi-branch Pipeline
- Automatically creates a Jenkins pipeline for each feature branch.
- Without this, each new feature branch will take a long time to setup.
- A multi-branch job is a folder of pipeline jobs.
- Create a **Jenkinsfile** in your git repository and make sure it exists in every branch of that repository.
	- This is what Jenkins multi-branch pipeline will use to auto create our pipelines.
- Configure
	- Branch Sources
		- Discover branches ![[Pasted image 20240911181952.png]]

# Multi-branch Pipeline
- dotnet-*feature-x*
- dotnet-*feature-y*
- angular-*feature-x*
- angular-*feature-y*

# Workflow
1. Developer pushes to a feature branch.
2. Jenkins runs a build on the feature branch. The build includes automated tests.
3. Developer creates a PR from the feature branch to developer branch.
4. If build from step #2 was successful and another developer approves the PR, it may be merged into the developer branch.
5. Jenkins runs a build on the develop branch, which includes a dev server deployment.

# Agents and Master
- Due to security setup, we ran everything on agents with a different user account than that of the master.
- This was due to IT restricting our access to sensitive data like config files or certain Jenkins directories.
- Agents ran on the same machine as the master.
- More info [here](https://community.jenkins.io/t/clarification-about-what-can-run-on-agents-vs-controller/4191/2) and [here](https://stackoverflow.com/questions/54020776/how-do-i-make-jenkins-pipeline-run-in-any-agent-machine-but-never-master)

# Authentication/Credentials
- How did we manage deployment to Production ? Who signed off or triggered it ?
	- Solution [here](https://stackoverflow.com/questions/8323129/restricting-visibility-of-jenkins-jobs-to-specific-users) where we restrict that project to specific users
	- Explained further [here](https://www.jenkins.io/doc/book/security/build-authorization/)
	- Another solution [here](https://stackoverflow.com/questions/56081795/how-to-restrict-pipeline-deployment-by-user) that only shows it if the person is authenticated.

# Plugins
### Tortoise SVN
- **Subversion** plugin
### Angular
- **Node.js** and **npm**
### .NET 
- **MSTest** to process the result of NUnit tests.
- **MSBuild.exe** plugin that runs Visual Studio solution files and builds your .NET application. 
- **Nant** for builds `NUnit` tests (and both will produce nice charts), and even deploy from them.
### Python
- **ShiningPanda**: which provides a build environment for Python projects; 
- **jUnit**: which allows you to publish test results from various testing frameworks; 
- **Cobertura**: which allows you to publish code coverage reports from various tools.

# Testing Pipelines
[ChatGPT Answer](https://chatgpt.com/c/66e9d7dd-17dc-8012-a7ad-16966e194e97)
- Used the Replay functionality explained [here](https://www.jenkins.io/doc/book/pipeline/development/#replay)
- NOTE: When tutorials and answers talk about "before committing to source code repository", they are talking about the `Jenkinsfile` file. This is the file which holds our pipeline code we are testing. The goal of the test is to make sure the pipeline code inside the `Jenkinsfile` is working before we commit that `Jenkinsfile` to the repository.

# Pipelines
Actual names entries on the Dashboard
Pipeline exists for every feature plus the Dev, UAT and Prod branches
Feature pipelines where created automatically due to Multi-branch feature pipelines offered by Jenkins.
Feature branches where named based on *technology-feature-name* e.g. *python-some-feature*
#### Dev
- Automatically run when the main branch was committed
- Deployed to our `dev` environment
- Send email to actuarial dev team that new changes are available.
#### UAT
- Same as **Dev** pipeline but deployed to `UAT` and must be run manually.
- Sent email to reporting team that it's available for testing.
#### Prod
- Same as **Dev** pipeline but deployed to `prod` and must be run manually by privileged users.
- Sent email to reporting team that it was available.
#### python-*feature*
- An example pipeline including building, testing and deployment explained [here](https://www.linkedin.com/pulse/how-use-jenkins-run-automated-python-tests-antonio-quarta/)
- Remember the repository we deployed it to.
#### angular-*feature*
- Full [pipeline](https://stackoverflow.com/a/77790940/17385921) explained in this answer
#### dotnet-*feature*
[Running unit tests in Jenkins](https://octopus.com/blog/jenkins-running-unit-tests)
- [Pipeline](https://octopus.com/blog/jenkins-running-unit-tests#creating-the-pipeline-project-in-jenkins-1) consists of
	- Build
	- Test
	- Deploy