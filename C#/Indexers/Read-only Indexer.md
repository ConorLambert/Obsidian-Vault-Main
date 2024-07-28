A read-only indexer can be implemented as an [[Expression-Bodied]] member, as the following example shows:

```csharp
public T this[int i] => arr[i];
```

Note that we dont require the keyword `get` 