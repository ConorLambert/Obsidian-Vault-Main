Medium [Article](https://saxenasanket.medium.com/database-part-three-b46568d282bb)

- Distributed locking is a method used to prevent multiple nodes from reading and writing to the same resource simultaneously. 
- Before a node starts to perform an operation, it attempts to acquire a lock. If the lock acquisition is successful, the node can safely perform the operation knowing no other node will interfere. Once it’s done, it releases the lock, allowing other nodes to acquire it.