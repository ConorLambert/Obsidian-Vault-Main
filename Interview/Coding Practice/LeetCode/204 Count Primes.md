https://leetcode.com/problems/count-primes/description/
## Terminology
##### Prime Number
- A prime number is a whole number greater than 1 that cannot be exactly divided by any whole number other than itself and 1 (e.g. 2, 3, 5, 7, 11)
- NOTE that 1 is not a prime number
##### Square Root
- The square root of a number is the factor that we can multiply by itself to get that number. For example, the square root of 16 is 4 (i.e. 4 * 4 = 16).

## Solution
- [Here](https://leetcode.com/problems/count-primes/solutions/5379921/understand-sieve-of-erasthonese-c-java-python/) is a solution on LeetCode with an explanation
- Uses **Sieve of Erasthonese** algorithm

## Sieve of Erasthonese Explained
##### Formal Description
- The Sieve of Eratosthenes works by iteratively marking multiples of prime numbers as composite.
- By starting with 2 (the smallest prime), the algorithm ensures that all smaller multiples are already marked as composite.
- As the outer loop progresses, it considers each prime number and eliminates its multiples from the potential prime list.
- Finally, the code counts the remaining elements marked as 1 (prime) in the prime array to determine the total number of primes.
##### Layman's Terms
1. Initialize every element in the array as 1 to indicate that it's prime.
	- The prime array acts as a flag system, effectively keeping track of which numbers are still considered prime candidates.
2. Create two loops, an outer loop and an inner loop 
3. The outer loop starts at 2 and ends with the square root of `n` 
4. The inner loop will mark any multiple of the outer loops value as composite i.e. not prime.
	- Any multiple of the outer loop will naturally not be considered a prime number.
	- The inner loop starts at *i$^2$* and increments by *i* each iteration (while `j < n`)
5. In the end, the array state is left in such a way that all remaining numbers that where not a multiple of 2 through the square root of `n` are prime.