# Strings in C#

In C#, the string is an object of the String class that represents a sequence of characters and is usually enclosed
within double quotes.

We can perform many operations on strings such as concatenation, comparison, getting substring, search, 
trim, replacement, etc.

## Strings are reference types in C#
Strings in C# are reference types, this means a variable of type `string` holds a reference to a `String` object 
on the managed heap, not the raw data itself.

## String (uppercase 'S') vs string (lowercase 's')
In C#, you can use the string in two ways i.e. you can use the string using capital S (i.e. String) or by using the
lowercase 's'  (i.e. string).
```C#
string str1 = "hello"; // using lowercase s
String str2 = "hello"; // using uppercase S
```
The small string is actually an alias of String (Capital string).

You can use any one of them i.e. either string or String.

As per convention, when creating a string variable, use the lowercase `string` but when invoking methods of the string
class use the uppercase one:

```C#
string str1 = "Hello World";
Console.WriteLine(String.Concat(" "));
```

## Strings are immutable in C#
Mutable means something can be changed while Immutable means something cannot be changed.

C# strings are immutable meaning C# strings cannot be changed.

This is to mean, each time we assign a new variable to the string variable, a new object is created and that object
will be referred to by the string variable and older objects will be garbage collected and this is the reason why
we say strings are immutable in C#.

```C#
string str = "Hello";
str = "World";
```
When the above two statements are executed, internally two memory locations are created.

When the first statement is executed, one object will be created which holds the value "Hello" and that object will be
referred to by the str variable.

When the second statement is executed, another object is created which holds the value "World" and now str will point
to this newly created object.

The first object will be garbage collected.

With value data types, such as int, double, boolean e.t.c., you can override the value of the same memory location and
hence they are said to be **mutable**, with string data type (reference types), you cannot modify the value of a
memory location and hence they are said to be **immutable**.

## String Intern in C#
The String Intern in C# is a process that uses the same memory location if the value is the same.

String interning is a memory optimization technique used by .NET runtime, it ensures that identical string literals
are only stored once in the memory.

```C#
string str1 = "hello";
string str2 = "hello";
```

Instead of doing this:

![not string interning](string-interning-1.png)

String interning does this:

![string interning](string-interning-2.png)