### Overview
- Event Sourcing ensures that all changes to application state are stored as a sequence of events. 
- Whenever the state of a business entity changes, a new event is appended to the list of events. 
- The application reconstructs an entity’s current state by replaying the events.
- We can also use the event log to reconstruct past states.

### Implementation
- ???

### Use Cases
- Makes it an effective strategy for systems that require a detailed **audit trail** or the ability to reverse or **replay transactions**.