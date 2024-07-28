## Requirements
- If the interviewee asks you to design a system that is well known that this part can become easier.
	- However, if they ask you to design an unknown system then there will be a back and forth period to dig deeper into what is required.
- You can always come back to the requirements throughout the interview if you think of new ones.
- Keep things short and concise (at least in writing)
	- Drop Example:
		- Instead of
			- Users should be able to add files to the cloud from your desktop, mobile, iPad, etc
		- Say
			- Users should be able to upload a file from any device
		- Even Better (on whiteboard)
			- Upload File
#### Functional Requirements 
- For an existing system, think about what steps you would perform on this system:
	- A good way to garner what functional requirements exist.
#### Non-Functional Requirements 
- Don't rush through the non-functional requirements.
- Go through the `-ilities` in a context specific to the problem at hand.
	- Not enough to just say scalability, availability, reliability
	- How do those things relate to the system at hand
- Steps
	- You want to make sure that you can:
		1. Identify the qualities that are unique and relevant to this system, what makes this system challenging, what makes it different or difficult.
		2. Be able to put them in the context of this system
		3. Quantify them (if possible)
		- Uber example:
			- low latency matching < one minute to match or failure
				- "low latency" refers to point 1
				- "matching" refers to point 2 (Uber relates to matching)
				- "< one minute to match or failure" refers to point 3 (it's quantifiable)
			- consistency of matching. Ride to driver is 1:1
				- "consistency" refers to point 1
				- "matching" refers to point 2
				- "Ride to driver is 1:1" refers to point 3
			- Highly available matching
				- No point 3 here
			- Handle high throughout
	1. CAP Theorem 
		- What two of the three does my system need the most
		- Mid Level
			- Consistency over availability to avoid double booking
			- Can tolerate a delay in viewing events
		- Senior Level
			- Strong consistency for booking tickets, high availability for searching and viewing events.
			- Here we are being more nuanced in that we can apply different 
	2. Our ratio of read/writes
		- read >> write
		- There are people who are going to be searching and viewing events a lot more then buying them
	3. Need to think about how our site will be used. Stuff like [[Access Pattern]]s, etc
		- Whats the frequency of requests 
		- Is it irregular, will there be a burst of access at certain times?
			- Ticketmaster:
				- People aren't booking tickets all that often
				- Maybe large scale access for particular events but relatively smooth otherwise e.g. Taylor Swift tour is about to go live, or the World Cup has been scheduled.
			- Uber:
				- Massive burst of access after a concert for example
				- 1000s of requests for Uber drivers.
		- This is where scalability is important
			- "We need scalability to handle surges in popular events"
	4. Note other less important requirements below a dotted line and make clear these are "Out of scope" or below the line requirements
		- GDPR Compliance
		- Fault tolerance
	5. Proceed with "These are what I'm going to prioritise (pointing at core requirements) and these are what I see out of scope (pointing at below the line requirements), would you like me to re-prioritise any of this".