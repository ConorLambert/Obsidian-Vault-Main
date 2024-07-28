### Background
- Locking can be an expensive task
- Systems with low data contention may suffer in performance by unnecessary locking.
- It's worth noting however, if contention is frequent, the cost of repeatedly restarting transactions hurts performance significantly. 

### Explained:
- Before committing, each transaction verifies that no other transaction has modified the data it has read. 
- If the check reveals conflicting modifications, the committing transaction rolls back and can be restarted:
	![[Pasted image 20240703101548.png|600]]

### Use Cases
- Applicable to systems with low data contention
