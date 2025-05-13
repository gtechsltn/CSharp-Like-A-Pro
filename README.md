# Code C# Like a Pro (CSharp-Like-A-Pro)

## Using Primary Constructors
```
public class Employee(string firstName, string lastName, DateTime hireDate, decimal salary)
{
    public string FirstName { get; init; } = firstName;
    public string LastName { get; init; } = lastName;
    public DateTime HireDate { get; init; } = hireDate;
    public decimal Salary { get; init; } = salary;
}
```

## Default Interface Methods
```
public interface ILogger
{
  void Log(string message) => Console.WriteLine($"Log: {message}");
}
```

## Extension Methods
```
public static class StringExtensions
{
    public static string Quote(this string str)
    {
        return $"\"{str}\"";
    }
}

var myString = "Hello, world!";
Console.WriteLine(myString.Quote());
```

## Null-Conditional Operator
```
string[] array = null;
var length = array?.Length ?? 0;

// length is 0 without throwing an exception.
```

## Nullable Reference Types
```
string? name = GetName();
Console.WriteLine(name?.ToUpper()); // Secure Access
```

## Inline out variables
```
if (int.TryParse("123", out int number))
Console.WriteLine($"Parsed: {number}");
```

## Dynamic LINQ to SQL
```
using (var context = new DataContext())
{
    var query = context.People.Where("City == @0 and Age > @1", "Seattle", 25);
    foreach (var person in query)
    {
        Console.WriteLine(person.Name);
    }
}
```

## Master LINQ for cleaner, faster code
```
var evenNumbers = numbers.Where(n => n % 2 == 0).ToList();
Console.WriteLine(string.Join(", ", evenNumbers));
```

## Take Advantage of Immutable Collections
```
var immutableList = ImmutableList.Create(1, 2, 3);
var newList = immutableList.Add(4); // Returns a new list
```

## Async/Await
```
public async Task<string> FetchDataAsync(string url)
{
    using (var httpClient = new HttpClient())
    {
        var response = await httpClient.GetStringAsync(url);
        return response;
    }
}
```

## Asynchronous Streams: Process data asynchronously with **IAsyncEnumerable**.
```
async IAsyncEnumerable<int> GetNumbersAsync()
{
  for (int i = 0; i < 5; i++)
  {
    yield return i;
    await Task.Delay(100);
  }
}
```

## Use yield for custom iterators
```
IEnumerable<int> GetNumbers(int start, int count)
{
  for (int i = 0; i < count; i++)
  yield return start + i;
}
// Usage
foreach (var number in GetNumbers(10, 5))
Console.WriteLine(number); // Outputs 10, 11, 12, 13, 14
```

## Use Span<T> for high-performance memory access
```
Span<int> numbers = stackalloc int[5] { 1, 2, 3, 4, 5 };
Console.WriteLine(numbers[2]); // Output: 3
```

## Read-Only Collections
```
var originalList = new List<string> { "Alice", "Bob", "Charlie" };
var readOnlyCollection = originalList.AsReadOnly();

// readOnlyCollection is now immutable.
```

## Explore Global Uses
```
// GlobalUsings.cs
global using System;
global using System.Collections.Generic;
```

## Use string interpolation for readability
```
string name = "Alice";
int age = 25;
Console.WriteLine($"My name is {name} and I'm {age} years old.");
```

## Use pattern matching
```
object data = 42;
if (data is int number)
{
  Console.WriteLine($"It's an integer: {number}");
}
```

## String StartsWith and EndsWith
```
string fileName = "report.docx";

if (fileName.StartsWith("rep"))
{
  Console.WriteLine("This file starts with 'rep'.");
}

if (fileName.EndsWith(".docx"))
{
  Console.WriteLine("This is a Word document.");
}
```

## String To Char Array
```
string name = "Anish";
if (name[0] = 'A')
{
  Console.WriteLine("The name starts with 'A'.");
}

if (name[^1] = 'h') // Using ^ to access the last character
{
  Console.WriteLine("The name ends with 'h'.");
}
```

## Using the List Pattern (C# 11)
```
var myArray = new[] { "first", "middle", "last" };
if (myArray is ["first", ., "last"])
{
  Console.WriteLine("The array starts with 'first' and ends with 'last'.");
}
```
