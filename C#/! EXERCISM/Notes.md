#### String.Split() - Consecutive Delimiters
- The **Split** method does not treat consecutive delimiters as one.
- For example, if your delimiter consisted of a single space and the string to be split contained a number of consecutive spaces, then the output array would only remove a single space per group meaning the result would still contain multiple empty spaces.
- The way around this is to use the **StringSplitOptions.RemoveEmptyEntries** as the second parameter to the **Split** method:

```csharp
lineOfText.Split(new [] {' '}, StringSplitOptions.RemoveEmptyEntries);
```

#### Repeated Operations Inside LINQ
- In a LINQ operation, if you are repeating an operation such as calling **ToLower()** on a string multiple times then see if you can encapsulate the logic that requires the string to be lowercase behind a method.
- Then pass the string in lowercase format as argument. That way, we only need to declare **ToLower()** once on the string in question:

```csharp
	public string[] FindAnagrams(string[] potentialMatches)
    {
        return potentialMatches
            .Where(x => isAnagram(baseWord.ToLower(), x.ToLower()))
            .ToArray();
    }

    private bool isAnagram(string baseWord, string potentialMatch)
    {
        return baseWord != potentialMatch
            && baseWord.Length == potentialMatch.Length 
            && string.Join("", baseWord.Order()) == string.Join("", potentialMatch.Order());
    }
```
