If you only use the get accessor like so:

```csharp
public string Info
{
	get { return "Some useful information"; }  
}
```

You can reduce it down to this instead:

```csharp
public string Info => "Some useful information";
```