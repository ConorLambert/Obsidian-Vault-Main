https://leetcode.com/problems/happy-number/description/
#### Getting the square of each digit
- Performing a modulo calculation in conjunction with dividing by 10 each iteration, will give you access to each digit of a number

```csharp
int squaresum(int n)
{ 
    int fast=0;
    while (n > 0) 
    {
        int digit = n% 10;
        fast += digit * digit;
        n/= 10;
    }
    return fast;
}
```