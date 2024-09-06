[Source](https://www.youtube.com/watch?v=g_7pYAfx0kQ)
## Overview
- *"A large fraction of the flaws in software development are due to programmers not fully understanding all the possible states their code can execute in"* - John Carmack.
- Immutability is *not only* when you request a new object upon every change. 
- Immutable design is a separate strategy.

## Purpose
##### Expressiveness
- Think if you where in a team environment.
- If we define a setter on some class then we are telling the users of that class that they can change the value of that data.
- Likewise, passing mutable data to methods is giving that method permission to change the data when it suits that method.

## C# API Examples
- Anonymous Types
- String

## Implementation
##### Collections
- Be careful when attempting to declare collections as immutable.
	- This [article](https://www.developmentsimplyput.com/post/why-immutability-is-important-in-net-c#) has some pitfalls to avoid (highlighted).

## Performance
#####

