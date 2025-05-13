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

## Using Local Functions for Encapsulation
```
public IEnumerable<int> Fibonacci(int n)
{
    int Fib(int term) => term <= 2 ? 1 : Fib(term - 1) + Fib(term - 2);
    return Enumerable.Range(1, n).Select(Fib);
}
```

## Expression-bodied Members for Succinct Code
```
public class Person
{
    public string Name { get; set; }
    public override string ToString() => $"Name: {Name}";
}
```

## Readonly Structs for Immutable Data Types
```
public readonly struct Point
{
    public double X { get; }
    public double Y { get; }
    
    public Point(double x, double y) => (X, Y) = (x, y);
}
```

## Ref Returns and Locals for Performance Optimization
```
public ref int Find(int[] numbers, int target)
{
    for (int i = 0; i < numbers.Length; i++)
    {
        if (numbers[i] == target)
            return ref numbers[i];
    }
    throw new IndexOutOfRangeException("Not found");
}
```

## Using Discards to Ignore Unwanted Returns
```
var (_, product) = Calculate(3, 4); // Only interested in the product
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

## Null Coalescing Assignment for Streamlined Null Checks
```
List<int> numbers = null;
numbers ??= new List<int>();
numbers.Add(1);
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

## Asynchronous Streams with IAsyncEnumerable

```
public async IAsyncEnumerable<int> GetNumbersAsync()
{
    for (int i = 0; i < 10; i++)
    {
        await Task.Delay(100); // Simulate asynchronous work
        yield return i;
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

# References
+ [C# Tips: Time Series Analysis Like a Pro](https://medium.com/@WC_/c-tips-time-series-analysis-like-a-pro-5d44db178842);
+ [10 Advanced C# Tricks for Experienced Developers](https://medium.com/@kmorpex/10-advanced-c-tricks-for-experienced-developers-26a48c6a8c9c);
+ [10 Useful C# .NET Snippets To Code Like a Pro](https://medium.com/@kmorpex/10-useful-c-net-snippets-to-code-like-a-pro-cb196dbc86d4);
+ [7 Clever Async Tips for C#/.NET Ninjas](https://medium.com/@kmorpex/7-clever-async-tips-for-c-net-ninjas-223b8cefd120);

## Build a Command Line Interface(CLI) Program with .NET Core
+ [Build a Command Line Interface(CLI) Program with .NET Core](https://medium.com/swlh/build-a-command-line-interface-cli-program-with-net-core-428c4c85221)
```
Install-Package Microsoft.Extensions.Hosting

Install-Package Serilog.Extensions.Logging
Install-Package Serilog.Settings.Configuration
Install-Package Serilog.Sinks.Console
Install-Package Serilog.Sinks.File

Install-Package McMaster.Extensions.CommandLineUtils
Install-Package McMaster.Extensions.Hosting.CommandLine
```

## Crafting a Powerful API Performance CLI: Approach with .NET Core and System.CommandLine
+ [Crafting a Powerful API Performance CLI: Approach with .NET Core and System.CommandLine](https://dev.to/alisson_podgurski/crafting-a-powerful-api-performance-cli-approach-with-net-core-and-systemcommandline-3i9k)
```
dotnet new console -n ApiPerformanceTool
cd ApiPerformanceTool

dotnet add package System.CommandLine
dotnet add package System.Net.Http
dotnet add package System.CommandLine.NamingConventionBinder

dotnet run -- test https://api.example.com/endpoint --concurrent 100 --output report1.txt

dotnet run -- compare report1.txt report2.txt
```

## How to Create Command Line Console Applications in .NET with Cocona
+ [How to Create Command Line Console Applications in .NET](https://antondevtips.com/blog/how-to-create-command-line-console-applications-in-dotnet)
+ [Building a Command Line Interface (CLI) program using System.CommandLine library in C#](https://medium.com/@devedium/building-a-command-line-interface-cli-program-using-system-commandline-library-in-c-ec0e8fbbd88d)
+ [Micro-framework for .NET console application. Cocona makes it easy and fast to build console applications on .NET.](https://github.com/mayuki/Cocona)
```
dotnet add package HtmlAgilityPack
dotnet add package AngleSharp

# Cocona
dotnet add package Cocona

# A lightweight version is also available if you prefer less dependency.
dotnet add package Cocona.Lite
```

## Building Command Line Applications with .NET: A Comprehensive Guide with ReadLine
+ [Building Command Line Applications with .NET: A Comprehensive Guide](https://blog.stackademic.com/building-command-line-applications-with-net-a-comprehensive-guide-69836f8186d0)
+ [Guidelines for creating your own CLI tool](https://medium.com/jit-team/guidelines-for-creating-your-own-cli-tool-c95d4af62919)
+ [A Pure C# GNU-Readline like library for .NET/.NET Core](https://github.com/tonerdo/readline)
```
dotnet add package System.CommandLine --version <latest_version>
dotnet add package ReadLine --version <latest_version>
dotnet publish -c Release -r win10-x64 --self-contained
dotnet publish -c Release -r win10-x64 --self-contained -p:PublishTrimmed=true
dotnet pack -c Release
dotnet nuget push ./nupkg/YourToolName.<version>.nupkg --api-key Your_NuGet_Api_Key
dotnet tool install --global YourToolName
```

## Building a Secure Authentication System in .NET Core

## The Complete Guide to OAuth Integration with C#
+ [The Complete Guide to OAuth Integration with C#](https://medium.com/@WC_/the-complete-guide-to-oauth-integration-with-c-from-beginner-to-pro-c7c31ceecf32)
```
dotnet add package Microsoft.IdentityModel.Protocols.OpenIdConnect
```

## OxyPlot is a cross-platform plotting library for .NET Core
+ [OxyPlot](https://github.com/oxyplot/oxyplot)

## dotnet cli
+ [Important .NET CLI Commands: Essential Tools for .NET Developers](https://hardyian.medium.com/important-net-cli-commands-essential-tools-for-net-developers-b180d1dc10af)
+ [.NET Core Architecture and .NET CLI](https://medium.com/mr-plan-publication/net-core-architecture-and-net-cli-290cc44d8097)
