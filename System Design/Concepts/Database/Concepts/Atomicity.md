### Overview
- An atomic transaction is an indivisible and irreducible series of database operations such that either all occur, or none occur.
- A guarantee of atomicity prevents partial database updates from occurring, because they can cause greater problems than rejecting the whole series outright. 
- The transaction cannot be observed to be in progress by another database client. At one moment in time, it has not yet happened, and at the next it has already occurred in whole (or nothing happened if the transaction was cancelled in progress).

### Example
- Monetary transfer from bank account A to account B. 
- It consists of two operations: 
	- Withdrawing the money from account A 
	- Saving it to account B. 
- Performing these operations in an atomic transaction ensures that the database remains in a consistent state, that is, money is neither lost nor created if either of those two operations fails.