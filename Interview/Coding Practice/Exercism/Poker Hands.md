[Source](https://exercism.org/tracks/csharp/exercises/poker)

# Terminology
- `Hand`:
	- Set of cards for one person
- `Rank`:
	- Number on the card
- `Suit`:
	- Spades, Hearts, etc
- `Card`:
	- Rank and Suit
- `Flush`:
	- Hand with all the same suit
- `Straight`:
	- Hand where each card is in sequential order

# Design
- Classes, properties and methods are created to match the terminology

# Questions
#### ToArray()
- Why is there lot's of `ToArray()` calls?
	- Removing most of them causes no issues.
	- I don't think the `ToArray()` calls incur any performance issues though because it will be converted to an array anyway when needed e.g. inside the `IsStraight` and `IsFlush` methods and even in the calling test method.

# Lessons Learned
#### Use ChatGPT
- Use ChatGPT to explain the problem
- Use ChatGPT to explain someones else's solution
#### Thoroughly understanding the problem
- Take your time to read up on the problem at hand. 
- Thoroughly read up on poker hands and their rules.
#### Write requirements
- After understanding the problem, write down the requirements.
#### Create Constructs from Requirements
- Create classes, properties and methods related to Card, Hands, Rank, etc

# Useful Functionality
#### Call Constructor Implicitly
```c#
hands.Select(card => new { Card=card, Rank=HandRank(card) }).ToArray();
```
- `Card=card` will call the constructor of the `Card` class and pass `card` as a parameter.

#### IEnumerable.SequenceEquals
- Compare two sets of collections
```c#
ranks.SequenceEqual(new []{14,5,4,3,2})
```
- Works on any type that implements the `IEnumerable` interface.
