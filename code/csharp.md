C#
==

Data Types
----------

- `bool` - `true` or `false`
    - e.g. `bool canIVote = true;`
- `int` - 32-bit signed integers
    - `Console.WriteLine('Biggest int: {0}', int.MaxValue)`
    - `Console.WriteLine('Smallest int: {0}', int.MinValue)`
    - `int x = 1`
- `float` - 32-bit signed float point number
    - Accurate to 6 decimal places
    - `Console.WriteLine('Biggest float: {0}', float.MaxValue)`
    - `Console.WriteLine('Smallest float: {0}', float.MinValue)`
    - `float x = 2.2F`
- `double` - 64-bit signed float point number
    - `Console.WriteLine('Biggest double: {0}', double.MaxValue)`
    - `Console.WriteLine('Smallest double: {0}', double.MinValue)`
    - `double x = 2.2`
- `long` 
    - `Console.WriteLine('Biggest long: {0}', long.MaxValue)`
    - `Console.WriteLine('Smallest long: {0}', long.MinValue)`
    - `long x = 3L`
- `decimal` - 128 bit values
    - Accurate to 28 digits
    - `decimal pi = 3.14159265359M;`
    - `Console.WriteLine('Biggest decimal: {0}', decimal.MaxValue)`
    - `Console.WriteLine('Smallest decimal: {0}', decimal.MinValue)`
- `byte` - 8bit unsigned int: 0 ~ 255
- `sbyte` - 8bit signed int: -128 ~ 127
- `char` - 16bit unicode character
- `short` - 16bit signed: -32,768 ~ 32,767
- `ushort` - 16bit unsigned int: 0 ~ 65,535
- `uint` - 32bit unsigned int: 0 ~ 4,294,967,295
- `ulong` - 32bit unsigned int: 0 ~ 18446744073709551615

String Parsing
--------------
```c#
bool boomFromStr = bool.Parse("true");
int intFromStr = int.Parse("100");
double doubleFromStr = double.Parse("3.14159")
```

Date Time
--------
- Note the types that are built in are all lower case, whereas `DateTime` is capitalised like any other class
```c#
using System

DateTime firstProcessor = DateTime(1975, 12, 21);
firstProcessor.dayOfWeek;
firstProcessor.AddDays(4);
firstProcessor.AddMonths(2);
firstProcessor.AddYears(1);
Console.WriteLine("First processor date: {0}", firstProcessor.Date);
```

Time Span
---------

```c#
using System;

TimeSpan lunchTime = TimeSpan(12, 30, 0); // from midnight
lunchTime.Subtract(TimeSpan(0, 15, 0));
lunchTime.Subtract(TimeSpan(1, 15, 0));
Console.WriteLine("New duration: {0}", lunchTime.ToString());
```

Very Very Large Numbers
-----------------------
First have to check to use the `System.Numerics` is installed
```c#
System.Numerics;

BigInteger bigNum = BigInteger.parse("12345678901234567890");
Console.WriteLine("Big number x 2: {0}", bigNum * 2);
```

FORMATTING OUTPUT 
-----------------
 
```c#
// Format output for currency
Console.WriteLine("Currency : {0:c}", 23.455);

// Pad with zeroes 
Console.WriteLine("Pad with 0s : {0:d4}", 23);

// Define decimals 
Console.WriteLine("3 Decimals : {0:f3}", 23.4555);

// Add commas and decimals
Console.WriteLine("Commas : {0:n4}", 2300);
```

STRINGS
-------
```c#
// Strings store a series of characters
string randString = "This is a string";

// Get number of characters in string
Console.WriteLine("String Length : {0}", randString.Length);

// Check if string contains other string
Console.WriteLine("String Contains is : {0}", 
    randString.Contains("is"));

// Index of string match
Console.WriteLine("Index of is : {0}", 
    randString.IndexOf("is"));

// Remove number of characters starting at an index
Console.WriteLine("Remove string : {0}",
    randString.Remove(10, 6));

// Add a string starting at an index
Console.WriteLine("Insert String : {0}",
    randString.Insert(10, "short "));

// Replace a string with another
Console.WriteLine("Replace String : {0}",
    randString.Replace("string", "sentence"));

// Compare strings and ignore case
// < 0 : str1 preceeds str2
// = : Zero
// > 0 : str2 preceeds str1
Console.WriteLine("Compare A to B : {0}",
    String.Compare("A", "B", StringComparison.OrdinalIgnoreCase));

// Check if strings are equal
Console.WriteLine("A = a : {0}",
    String.Equals("A", "a", StringComparison.OrdinalIgnoreCase));

// Add padding left
Console.WriteLine("Pad Left : {0}",
    randString.PadLeft(20, '.'));

// Add padding right
Console.WriteLine("Pad Right : {0} Stuff",
    randString.PadRight(20, '.'));

// Trim whitespace
Console.WriteLine("Trim : {0}",
    randString.Trim());

// Make uppercase
Console.WriteLine("Uppercase : {0}",
    randString.ToUpper());

// Make lowercase
Console.WriteLine("Lowercase : {0}",
    randString.ToLower());

// Use Format to create strings
string newString = String.Format("{0} saw a {1} {2} in the {3}",
    "Paul", "rabbit", "eating", "field");

// You can add newlines with \n and join strings with +
Console.Write(newString + "\n");

// Other escape characters
// \' \" \\ \t \a

// Verbatim strings ignore escape characters
Console.Write(@"Exactly What I Typed");

// Excepts input up until a newline, but it is here to 
// keep the console open after output
// Read() excepts a single character
Console.ReadLine();
```

## LISTS

Created like this:

```cs
new List<string> myList = {"foo", "bar"};
myList.add("baz")
myList[2] = "caz"

// Printing the list
foreach (string s in myList)
{
    Console.WriteLine(s);
}
```

## DICTIONARIES

```cs
// Declare a dictionary with keys of type string and values of type int
Dictionary<string, int> myDictionary = new Dictionary<string, int>();

// Set an item in the dictionary
myDictionary["apple"] = 5;
myDictionary["banana"] = 3;
myDictionary["orange"] = 7;

// Get an item from the dictionary
int numberOfApples = myDictionary["apple"];
Console.WriteLine($"Number of apples: {numberOfApples}"); // Output: Number of apples: 5

// Get an item or a default value if not present
int numberOfGrapes;
int numberOfGrapes = myDictionary.TryGetValue("grape", out int grapeValue) ? grapeValue : 0;
Console.WriteLine($"Number of grapes: {numberOfGrapes}");
``` 

## LINQ

- `Language Integrated Query`
- LINQ is a set of features that allow you to write queries against various data sources in a unified and consistent manner, whether it's collections, databases, XML, or other data sources.
- JavaScript - C#
- `.map()`    - `.select()`
- `.filter()` - `.where()`

```cs
// Example: Filtering even numbers
List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6 };
IEnumerable<int> evenNumbers = numbers.Where(num => num % 2 == 0);

// Example: Sorting strings alphabetically (Use `OrderByDescending` for desc)
List<string> names = new List<string> { "Alice", "Bob", "Charlie", "David" };
IEnumerable<string> sortedNames = names.OrderBy(name => name);

// Example: Grouping strings by their length
List<string> words = new List<string> { "apple", "banana", "grape", "orange" };
var groupedByLength = words.GroupBy(word => word.Length);

// Example: Flattening a list of lists
List<List<int>> nestedNumbers = new List<List<int>>
{
new List<int> { 1, 2, 3 },
new List<int> { 4, 5 },
new List<int> { 6, 7, 8 }
};
IEnumerable<int> flattenedNumbers = nestedNumbers.SelectMany(innerList => innerList);
```


## Visibility Modifiers for Methods

- `internal`: An internal member (class, method, property, etc.) is accessible only within the same assembly. It's not visible to code outside that assembly. It's used for hiding implementation details from external assemblies while allowing other types within the same assembly to access it.

- `private`: A private member is accessible only within the containing type (class, struct, etc.). It's the most restrictive access modifier and is used to encapsulate implementation details.

- `protected`: A protected member is accessible within the containing type and derived types (classes that inherit from the containing class).

- `public`: A public member is accessible from any code, whether it's within the same assembly or in a different one.
