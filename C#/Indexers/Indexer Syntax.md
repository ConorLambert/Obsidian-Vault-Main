Suppose you have a class `TempRecord` that represents the temperature in Fahrenheit as recorded at 10 different times during a 24-hour period. 
The class contains a `temps` array of type `float[]` to store the temperature values.

```csharp
public class TempRecord
{
    // Array of temperature values
    float[] temps = new float[10]
    {
        56.2F, 56.7F, 56.5F, 56.9F, 58.8F,
        61.3F, 65.9F, 62.1F, 59.2F, 57.5F
    };
    
    public float this[int index]
    {
        get => temps[index];
        set => temps[index] = value;
    }
}
```

By implementing an indexer in this class, clients can access the temperatures in a `TempRecord` instance as
	`float temp = tempRecord[4]`
instead of
	`float temp = tempRecord.temps[4]`

```csharp
class Program
{
    static void Main()
    {
        var tempRecord = new TempRecord();

        // Use the indexer's set accessor
        tempRecord[3] = 58.3F;
        tempRecord[5] = 60.1F;

        // Use the indexer's get accessor
        for (int i = 0; i < 10; i++)
        {
            Console.WriteLine($"Element #{i} = {tempRecord[i]}");
        }
    }
}
```
