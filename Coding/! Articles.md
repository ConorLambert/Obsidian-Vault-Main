# Flag Argument
### Sources
- [Robert Fowler](https://martinfowler.com/bliki/FlagArgument.html)
- [Engineers Codex Email](https://mail.google.com/mail/u/0/?tab=rm&ogbl#inbox/FMfcgzQVzXWWpfCPrtzPkwfQxcLWWcpk)
- [Software Engineering StackExchangeThread](https://softwareengineering.stackexchange.com/questions/147977/is-it-wrong-to-use-a-boolean-parameter-to-determine-behavior/147983)

### Explained
- Avoid using boolean flags in method parameters
```python
def call_llm(prompt: str, output_plaintext: bool)
```
- Those True/False parameters that dictate control flow inside the method implementation.
- Must update the code in every place it's called.
- Not clear on what the intent is.
- Not extensible. What if we want to extend to output CSV, XML, etc
- There are some cases where it makes sense however (check section titled **Boolean Setting Method** in Robert Fowlers article)

### Alternative Solutions
###### Separate Methods
```python
call_llm_csv("message")
call_llm_json("message")
```
###### Enum
```python
output = call_llm("Subscribe!", LLM_OUTPUT.JSON)
```
- Even if it's only binary state
- The calling method is more expressive as it tells the reader what it's intent is.
