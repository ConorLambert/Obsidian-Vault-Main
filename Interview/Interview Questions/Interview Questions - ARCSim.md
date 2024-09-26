# Personal
### Introduction
{{Show enthusiasm}}
- Thank you for taking time out today to interview me

### Tell me about yourself ?
- From Sandyford, south Dublin
- Born and raised here
- Graduated from DIT Kevin street with Honours degree in computer science.
- Work as full stack developer in my last job at Athora Ireland for 6 years
- Was made redundant at the end of 2023
- Went travelling for the year and *got to meet people from different backgrounds*
	- Went to China for a month
	- I returned home for a short time
	- Then went back and toured most of Asia
	- Returned home to the grey clouds and the rain back in June.

### Interests & Hobbies
- Workout.
- Travel
- Meditate.
- Foodie (like trying new restaurants)

# Role
### Tell me about your time in Athora ?
- I worked on a team with 3-4 developers
- I worked *with* the Actuarial Reporting team
- *We* developed an actuarial modelling solution called **ARCSim** (Athora Risk and Capital Simulator).
- The purpose of this solution was to allow the reporting team to calculate a non-unit reserve.\
	- A [[! Terminology#Non-unit Reserve|non-unit reserve]] is the amount of money the company needs to hold in order to ensure we can meet all future policyholder liabilities.
- This calculation was needed to comply with [[! Terminology#regulatory|regulatory]] Solvency II reporting and [[! Terminology#Statutory|statutory]] IFRS returns set out by the EU.
- The calculation itself is a 60 year [[! Terminology#Stochastic Cash Flow|stochastic cash flow]] projection of all policies, taking account of all future fees/charges and claims. This projection uses policyholder and market data and takes account of future assumptions relating to lapses, mortality, expenses etc, as well as future economic assumptions.

### What was your role in Athora ?
- At the start I was a junior dev
- I worked on basic front-end features and then progressed to back-end and then onto Calculation Engine
- Later became mid-level and began mentoring junior devs.
- Conducted interviews
- Took on more senior roles near end of tenure to build UX Upgrade.
- Throughout that, I would continuously research new and existing technologies to enhance business processes within a company.
	- ARCSim
	- Angular
	- Mediator
	- VBA to streamline IFRS 17 process

### What was your typical day like in Athora ?
- Daily standup in the morning with Actuarial Development team
- Check JIRA or email for any reported bugs.
- Continue working with task or take a new one from JIRA list

### Why where you made redundant ?
- Project was outsourced

### Tell me about the UX Upgrade
- Front-end deteriorating
- Patch up features
- Assigned the project to manage
- Prototyping
- Interacted with person based in Spain.
- Result was huge customer satisfaction
- Happier using a tool they use daily

### Why was project outsourced ?
- ==Conflict between the actuaries on both sides==
- *There was a clash between our processes and their processes and what information they wanted out of it, we didn't provide or couldn't provide.*
- We took on many business units which was totally unforeseen.
- ==Whole company was moving their internal processes to Power BI and similar solutions.==

### Who was it outsourced to ?
- Willis Towers Watson

# Behaviour
### How do you handle tight deadlines ?
- Cut scope
	- Prioritize remaining tasks
- Implement the most important part of a feature
	- Okay if color is a little off or something not laid out properly
- Document everything and make sure there is an audit trail

### What are your weaknesses and how do you overcome them ?
- Software Estimates
	- [[! Reddit Discussion|How to give software estimates]]
- Not properly prioritizing tasks.
	- Spent more time on prioritizing what actually mattered
	- Getting advice from senior engineer.
-  Architect Elevator
	- Know how to talk to tech and non-tech people

### What big lessons did you learn from working in Athora ?
- Really understand the problem domain
	- Was difficult with actuarial science as it is such a complex field

### What innovation have you brought to the team in your old job ?
{{Makes everyones life easier which is something I like to do}}
- Implement CI/CD pipeline. Manual process before that.
- UXUpgrade.
- RunGroup Compare

### How do you handle ambiguous tasks ?
- Why is it ambiguous ?
	- Was the requirement not recorded properly ?
		- Get further clarification from stakeholders
	- Or maybe the possible solution needs more research.
		- Break down problem into smaller pieces.
		- Conduct research
- Continuously verify with stakeholders to ensure the right path is being taken.

# Scenarios
### Describe a situation where successfully worked as part of a team to achieve a goal and explain what your role was in achieving that ?
{{Make sure to give answer in context of a team}}
{{Make sure to show how you contributed to that goal}}
###### Migrating on-prem to cloud
- Worked with IT and other team members
- Migrated the WebApp, Version Control and Jenkins, and part of the database
- Takeaways
	- The importance of documenting things
	- The power of working in teams
		- Way ahead of the deadline
		- Worked with external teams like IT.
		- Everyone focused on one specific task.
		- Felt like when everyone is aware of what to do, then it has the best chance of getting done and done properly.

### Describe a time where you worked on a project and you faced a setback and how did you overcome it ?
{{Show how you provided leadership here}}
##### Investigating failed runs
- Situation
	- A single package can take 30 mins to run.
	- During testing and development, runs would regularly fail inside the calculation engine due to incorrect inputs and model errors.
	- Extremely difficult to debug
	- Second guess what input was incorrect or was it a model error
	- Causing the regression tests to be delayed
- Task
	- Run the package in debug mode in the server
	- Stop at the point of execution to allow developer to analyze call stack.
- Action
	- Setup automated via a windows batch file
		- Transmitted with the run package
	- Batch file which opened python package in PyCharm with certain configuration settings
		- NumberOfSims=1
		- NumberOfProcessors=1
		- OutputType=CSV
	- Run PyCharm and it would automatically pause at the point of failure
- Result
	- Issues resolved in minutes rather than hours.
	- White box view of the run.

### Tell me about a recent failure and what did you learn from the experience ?
##### Attribution runs with Sean Begley
- (S) Bug that made runs fall over 
- (S) Actuarial dev team really needed the results the next morning
- (S) But runs take a couple of hours to complete
- (T) I realized I caused the bug and came forward to fix it.
- (A) Solution
	- Rollbacked changes and deployed
	- Checked logs and analysed the problem
	- Fixed bug and deployed after runs where complete
	- Decided on which runs where the most important and ran those on fasted server.
- (R)
	- Important results where available in time.
- Lessons learned
	- Don't deploy enhancements before certain runs are needed
	- Perform mini regression test based when changing certain code.
	- Often tell other devs what happened.
- What if they needed all results
	- I would go to the person who the report is for and tell them what happened. I would take responsibility.
	- I would also ask them if there was something they really needed from the results.
##### AWS Servers Left On
- The AWS cloud servers where left on, costing the company 30,000
	- 30 grand is a junior devs wage.
- I'm not so much annoyed on us getting blamed but it did cost the company money
- Share with rest of the team so that this doesn't happen.
- Lessons Learned
	- Make responsibilities with IT more clearer 
	- Implement a manual check going forward

### Give an examples where simplified a complex idea ?
- Explaining the concept of a Config Set. Related it to how Excel and MsWord files have a version history.
- Put yourself in their shoes

### Give examples of where you wrote clear documentation ?
- Done video tutorials that users could playback

### Examples of when you solved a problem ?
##### Large Data Output from Model
- Converting output of model to HEX data and storing it on database
- Improvement numbers
	- 1 GB to around 500 MB
##### Base Runs 
- Actuarial reporting team needed the base runs of each product
	- Split by SubRunName and SimRange instead of per product
##### SIMD
- SIMD using vectorization in Python
- Reduced execution time for single product with single sim by 90%
##### UXUpgrade
- Front-end was becoming unusable

### Tell me about a time when you had to resolve a challenging bug in a software project under a tight deadline ?
##### SharePoint
- Situation
	- One day before release
	- Request limit with SharePoint
	- Only surfaced just before release
- Task
	- I was tasked to find the issue
- Action
	- Analysed logs
	- Refactored business logic to set a timeout.
- Result
	- No more request limit errors
	- Release was deployed successfully.

### Show how something could have gone better and how you would do if if you where starting over
- ??? Some of the database structure

### Give an example where customer feedback shaped your work or how you ensured the final product met customer expectations ?
- UXUpgrade project using prototypes

### Give an example where customer feedback did not meet expectations  and what you done to remedy it ?
- Coding out a front-end screen which took a number of weeks
- Apologised to the stakeholders and took responsibility.
- How I solved it
	- Organized another meeting and clarified using third-party prototypes from Dribbble
	- Learned UI prototyping to avoid in the future.

# Leadership
### What is your leadership style ?
- Servant leadership ([ChatGPT answer](https://chatgpt.com/c/66f1a08f-2368-8012-98b1-efe28afb1124))
	- Server others 
	- Prioritize the needs, development, and well-being of their team members or organization
	- Highlighted some great answers on this Reddit [thread](https://www.reddit.com/r/careerguidance/comments/1alu738/how_do_you_answer_the_question_what_is_your/)
- I strive to make other peoples lives easier in the company
- I want to help the team excel and not just myself (remember that 10x developer reddit [discussion](https://www.reddit.com/r/ExperiencedDevs/comments/1ep1sa9/what_makes_a_10x_or_whatever_your_term_is/))
- I want to understand the business and align my role with the business goals
- If the best solution requires using an existing tool like Excel or some third party library, then use that instead of spending needless hours coding up an application.

### What you value in leadership and why you hold those values
- Look the qualities of servant leadership
	- Being a servant leader will prevent a high staff turnover
- I have seen people leave my old job because there leader was difficult to deal with.
- Set high technical standards
	- Broken window fallacy.
- I like to see people develop new skills and be more productive.

### How do you handle difficult stakeholders ?
- Build relationship on personal and professional level
- Have a personal chat
- Make them see you understand their view.
- Trying to get the stakeholders to trust you

### Tell me about a time when you had a conflict with a coworker ?
- Showing up late, not interested in the work.
- I felt I was the problem because it was my first junior dev position
	- Knocked my confidence a little bit.
	- Reassured myself that
- I will talk to him first and see.
	- He's a junior dev, maybe he is adjusting himself.
- Eventually came around and we started collaborating together.
- Be compassionate. Maybe something else is going on in their lives

### How do you deal with developers spending precious time on low priority tasks 
- "That aspect of the solution is important, but it's not important at this moment in time in the project lifecycle"
- CSS styling.
- Page load speed (provided the slow speed is not making the project unusable).

### Give an example of situation where a team member had a bad solution and how you talked them out of that ?
{{Didn't just say "No, bad idea"}}
{{Show how you empowered them}}
- Notice and comment on good things in their solution and try and bring that over
- Shows links to resources
	- Backup what your saying so it doesn't seem like it's coming from just you

### Can you think of a time when a developer might not have liked the opportunity you gave them and how you dealt with it ?
- FERGAL and Angular
- He didn't understand it and thought it was a steep learning curve
- I gave him time to learn up using courses I had handpicked and that I had learned from

### How did you mentor other developers ?
 - Try and give them opportunities and responsibilities
	 - Don't want them thinking there just doing boring tasks
- Developers where nervous doing presenting and demoing
	- Reassured them
	- "*I will be in the room with you if a question arises*"

### How did you delegate tasks to other engineers ?
- Evenly distribute workload and show this
	- Put number beside task related to complexity.
- Discuss on call with all engineers present
- Go through each task to make sure the engineer understands
- Follow up if deadline not met
- Make sure the team can approach you for whatever reason or if they are struggling.
- Document standards
- Give constructive feedback

### How would your colleagues describe you ?
- Helpful and easily approachable.
- I was point of contact for reporting team who would ask me questions
- Devs would come to me if there was a tech problem as senior manager was in lot's of meetings.
	- I would always try and make them understand the solution. I would provide references to articles that  dug further into it.

### Give an example where you took initiative, mentored others or led projects ?
- UXUpgrade

### How to deal with people trying to push you over.
- Tell them your already doing something
- "*I am doing A, B and C right now. I can prioritize D, if it is more urgent. Which of the other tasks should I pass to coworker or put on hold until I finish with D?*".

# Communication
### How did you communicate problems or solutions to other people ?
- Emails with TLDR and highlight important parts.

### How did you teach others how to use the platform ?
- "*Call me and Il share my screen and we can discuss*"
- Record meetings
- Provide video tutorials.
- ARCSim Bytes
	- Manually wrote email with a portion of the documentation
	- Sent out every Wednesday

### How do you provide feedback to a colleague ?
- Be gentle
- Watch tone
- Present an alternative rather than say it's wrong and show how the alternatives is better through the lens of less work and/or increased efficiency.
- Don't give too much feedback in a short time (day after day)
	- Better to give it all in one go through lesser interactions
- Try and find positives rather then just finding everything wrong.

### How well do you receive feedback from a colleague ? 
- Reframe what might be perceived as criticism into an opportunity to improve. The criticism isn’t directed toward you, it being presented FOR you. Welcome failure as a fast cycle of learning.
- Make sure you understand the feedback and maybe practice is there and then.

### How did you conduct code reviews ?
- ???
- Me to Junior
	- I would always try and make them understand the solution. 
	- I would provide references to articles that dug further into it.

# Technical

### How you approach solving a problem ?
- Clearly defining the problem at hand
	- Talk to necessary people
- "*20 days to solve a problem...*"
- Prototyping
- Break big problems down into smaller problems
	- Describe it in simpler terms
- Sleep on it
	- If well defined, then your brain can come up with the solution.
- Pomodoro timer

### Explain your philosophy around how you make decisions
- Cost
- Choosing one from two similar libraries
	- Which is better maintained.
- Big Decision steps
	1. Problem - what is the problem we are trying to solve?
	2. Solution - what is your proposed solution?
	3. Alternatives - what other ways could we solve the problem?
	4. Negative Consequences- what bad things will happen as a result of doing this?
	5. Actions - if we do this, what are the first steps, and who should we talk to?
- Document your decision using [[! NOTES (Dometrain Solutions Architect)#Architecture Decision Records (ADR)|ADR]]

### What steps did you take when implementing a new feature or bug fix ?
1. Create new branch
2. Try and replicate for a unit test.
3. Implement solution
4. Create pull request
5. Merge onto main branch
6. Deployed into dev environment for testing

### What was your most challenging project ?
- Jenkins
	- Difficult to setup and test
- Excel streamlining IFRS17
	- Lots of VBA code
	- Difficult to debug
- UX Upgrade (Deadlines)

### What is your troubleshooting process ?
- [[Interview/ARCSim/Architecture/Troubleshooting|Troubleshooting]]

### How important do you feel unit testing your code is ?
- Spend time (money) on developing unit tests rather then losing money because of a loss of customers because a bug showed up in production that caused downtime and lost trust.

# Architecture
### What Architectural patterns where used in your application ?
- Onion architecture
	- ???
### What Design Patterns where used in your application ?
- Mediator
- CQRS
- Facade
	- State Management
- Redux
	- State Management

# Technology
### Describe the technology stack ?
- When I first joined
	- Blazor
	- jQuery
	- .NET Framework
	- SQL Server
	- Python
	- Tortoise SVN
- Update
	- .NET Core
	- Angular
- UXUpgrade
	- Angular Material
	- Mediator
	- SharePoint interaction

# UX Upgrade
### How did this project come about ?
- Initial GUI from when I started was sufficient
	- Only Aegon Ireland policies
- As the years progressed, more and more functionality was required along with adding a new business unit Germany.
- Front-end became difficult to use in parts.
- I had been pushing for an upgrade for some time but got sidelined with other tasks
- Spoke to a member of Reporting team who agreed and we both proposed to upper management who gave the go ahead.
- Proof-of-concepts

### What where some of the main features of this new platform ?
- ProductionSpecification
	- The goal of the new UI was hide away the things they don't *generally* need but make them accessible if they *do* need them
- InputsGrid
- SharePoint interaction

### How did you conduct the Requirements gathering ?
- Observe how they currently used the system
- Prototyping
- Regular meetings
- Getting

### How did you plan it out ?
- Requirements phase
	- Massive use of prototyping
	- Finding what do they actually want at the root level (check this [[! YouTube#Every Developer Needs To Know How To Do This|note]])
- Write mock front-end where button clicks where simulated.
- Customer is happy and signed off
- Finding out what has to change from the current system
	- New tables need to be added
	- Whole rewrite of GUI layer
	- Application layer required moderate re-write.
- Created tasks using Trello and assigned a priority to the tasks.
- Prioritised the tasks
- Assigned tasks to contractor and myself.
- Periodic demos

### How did you delegate responsibilities to the team ?
- Other engineer was working on migrating Belgium over to our current platform.
- Hired a contractor
- Showed him prototypes, etc
- He was quite experienced

### What challenges did you face when implementing and how did you overcome it ?
- Deadlines/Estimates
	- How did I overcome
		- [[! Reddit Discussion|How to give software estimates]]
- Not enough coding skills
	- Certain features where very difficult to implement
	- How did I overcome
		- Practiced coding exercises every morning before work
		- Reversed engineered existing solutions from the web
- Dealing with a contractor
	- Was hired early whilst I was still doing requirements phase
		- Felt rushed
	- Communication barrier
		- Different country
		- Difficult explaining the prototypes remotely
	- How did I overcome
		- Talk slower and clearer.
		- Gave tasks on requirements that where clear at that stage.
- Had applied new skills and understandings from previous failings
	- Prototyped
	- Fail early

### What important lessons where learned ?
- How important the requirements phase is
	- Failing early in the lifecycle
	- I enjoyed the coding a lot more because I felt confident in what I was implementing.
- How valuable prototyping is.
- The importance of really understanding the domain

### What went well ?
- Separation of concerns
	- Contract focus on front-end, I focused on back-end
- Prototyping
	- Prototyping was invaluable
	- Saved weeks of coding.

### Are there any things you could have done better ?
- Hiring the contractor too early
- Not giving the stakeholders more interaction with UX sessions.
	- Example of Calum.

### What features are you most proud of ?
- RunGroup comparer
- Turning on and off AWS cloud servers to save money
	- Remember charged by the hour

# Calculation Engine
### How did the calculation engine come about ?
- ???

### Explain the SIMD feature ?
- SIMD stands for *Single Instruction, Multiple Data*.
- Initial solution used three nested loops
- ???

### What type of improvements did ARCSim provide over previous solutions ?
- Previous solution was called ModelRP and used Prophet to perform it's calculations
- ModelRp took weekend to run.
- ARCSim took 7-8 hours.

# Deployments
### What type of CI/CD pipeline did you have ?
- ???

# AWS Migration
### How was the AWS migration handled ?
- Multiple meetings with IT department to explain what our current infrastructure looked like.
- Our team got together and planned the migration over
- We split the responsibilities based on the technology stack. This worked well because each technology would run in it's own server when transferred. Allowed each person to work in an isolated way.
	- WebApp (GUI and .NET)
	- Data (SQL Server)
	- Calculation Engine (Python)
	- Version Control (Tortoise SVN)
- IT created the necessary servers for us
	- WebApp
		- Installing .NET hosting bundle
		- Adding Console trigger to Task Scheduler under certain credentials
		- Setting up and testing deployment
	- Data
		- Exported each database into it's own file
		- Sent file to AWS bucket
		- Restored from AWS bucket onto new Server.
	- Worker Servers
		- *Done at the end when data and WebApp migrated*
		- Turn on worker server
		- Installed python on each worker server
		- Ran small package
		- Ensured it connected to the database okay.
		- Turn back off
	- Version Control
		- More info on setting up [here](https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/)

### What corresponding technology was used in AWS ?
[[AWS Setup]]
- WebApp
	- Elastic Beanstalk 
	- `m5.4xlarge`
- Database
	- RDS
	- Came pre-installed with SQL Server
- Worker Servers
	- EC2
	- `C5`

### What challenges happened did you encounter when migrating and how did you deal with it ?
- GUI
	- Firewall settings
	- Azure app settings (Manu and Nikita)
- Database
	- Large volume of data to transfer.
	- Broke it down into constituent databases
	- Send an individual database file to an S3 bucket.
- Worker Servers
	- Installing python on each worker server
	- Turning on each worker server individually from WebApp testing  from WebApp 
- Console
	- Update worker server logic to turn on and off machines based on hourly charge rate.
- Jenkins on Version control server
	- Issues related to security (create a Key pair and Security Group)
	- IT managed this
		- More info on setting up [here](https://www.jenkins.io/doc/tutorials/tutorial-for-installing-jenkins-on-AWS/)

### What important lessons where learned ?
- The importance of documenting things

### What went well ?
- ???

### Are there any things you could have done better ?
- ???