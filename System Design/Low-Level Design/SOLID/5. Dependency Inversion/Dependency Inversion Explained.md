# Definitions
- High level modules shouldn't depend on low level modules. They should both depend on abstractions.

# Purpose
- Worth noting that in most cases, only one class will ever implement the interface.
- Mostly useful for mocking in Unit Tests.

# Implementation
```C#
public IRepository
{	
	// DECLARE METHODS
}

public Database : IRepository
{
	// IMPLEMENT METHODS
}

public Service
{
	public Service(IRepository repository)
	{
	}
}
```
==Both the high level module (`Service`) and the low level module (`Database`) depend on an abstraction (`IRepository`).==
