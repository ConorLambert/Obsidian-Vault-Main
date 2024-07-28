### Overview
- Locking is the process of ensuring that only one client can access a shared resource at a time.
- An example might be a shared counter (like inventory units) or an interface to a physical device (drawbridge up). 


### Performance
- Locks are important for enforcing the correctness of our system but can be disastrous for performance.


### Characteristics

##### Granularity of the lock
- Lock as little as possible to ensure that we're not blocking other clients from accessing the system. 
- For example, if we're updating a user's profile, we want to lock only that user's profile and not the entire user table.
##### Duration of the lock
- We want to lock only for the duration of the critical section. 
- For example, if we're updating a user's profile, we want to lock only for the duration of the update and not for the entire request.
##### Whether we can bypass the lock
- [[Optimistic concurrency control]] makes the assumption that most of the time we won't have contention (or multiple people trying to lock at the same time) in a system, which is a good assumption for many systems!

