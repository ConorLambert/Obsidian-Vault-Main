[Source](https://exercism.org/tracks/csharp/exercises/largest-series-product)
[VSCode Project](vscode://file/Users/conorlambert/Exercism/csharp/largest-series-product)

# Reflection
#### Aggregate
- Need to understand the `Aggregate` method better (good explainer [here](https://dev.to/ayodejii/understanding-the-enumerableaggregate-method-in-linq-5dpl))
#### Char Comparison
- Can compare integer values in their `char` representation without having to convert them to integers. The variable `digits` in the following example is a string:
	`digits.Any(c => c > '9' || c < '0')`
- Notice how it reads the similarly if they where integers.
#### Convert Char to Int
`var someInt = someChar - '0'`

# Solutions
[BlueD solution](https://exercism.org/tracks/csharp/exercises/largest-series-product/solutions/BlueD)
- [Chat GPT explanation](https://chatgpt.com/c/66f44841-a3a8-8012-a7d8-d5d8621d8e57)
- In the solution, there is no need for the value 1 to be used as the seed in the call to `Aggregate`. I have removed it and the tests still pass.
- Check comments in VsCode solution.