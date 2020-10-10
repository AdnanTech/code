# Files

Reading a CSV

```csharp
//Read CSV
using (var reader = new StreamReader(@"csvFile.csv"))
{
    List<string> listA = new List<string>();
    while (!reader.EndOfStream)
    {
        var line = reader.ReadLine();
        var values = line.Split(';');

        Console.WriteLine(values[0]);
    }
}
```

