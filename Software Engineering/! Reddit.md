https://www.reddit.com/r/ExperiencedDevs/

### What makes a 10x (or whatever your term is) developer and how to learn that?
[Source](https://www.reddit.com/r/ExperiencedDevs/comments/1ep1sa9/what_makes_a_10x_or_whatever_your_term_is/)

### What process do you use to plan/design new applications?
[Source](https://www.reddit.com/r/dotnet/comments/18an826/what_process_do_you_use_to_plandesign_new/)
- Goal is for early feedback/early failure
- General Process:
	1. Requirements gathering on what is actually needed (use case diagrams, flowcharts, event storming)
	2. Get early feedback with UI prototypes (no code).
	3. Get feedback again from a coded UI with mocked data and processes.
		- For example, clicking a button might simulate some process kicking off but nothing is actually happening in the background.
	4. If all clear, then begin implementing the API than the database tables and business logic.
- Other tips
	- Let users/stakeholders draw on whiteboard or using programs like excel to explain what they want.
	- Use Domain Driven Design.
	- Rubber duck designing to flesh out designs.
	- Be ready to erase things if it doesn't look right i.e. avoid the [[sunk cost fallacy]].
	- Look for existing projects on GitHub that are similar and use their template
- Tooling
	- https://flowsage.co/
		- Flowcharts that are AI powered
	- Lucid Chart
	- Miro
		- Project management
	- Draw.io
	- https://www.justinmind.com/
		- UI prototyping tool
	- https://www.syncfusion.com/downloads/metrostudio
		- UI Icons