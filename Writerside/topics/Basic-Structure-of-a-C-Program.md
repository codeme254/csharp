# Basic Structure of a C# Program

C#.NET is a Case-Sensitive Language and Every Statement in C# should end with a Semicolon.

```C#
// Importing namespace
using System;

// Namespace declaration section
namespace HelloWorld
{
    // Class Declaration section
    internal class Program
    {
        // Main method
        static void Main()
        {
            Console.WriteLine("Hello, World!");
        }

        // Functions/methods/blocks
        static void MyFunction()
        {
            // Statements
            Console.WriteLine("Hello, World!");
        }
        
    }
}
```

## Importing namespace section
This section contains importing statements that are used to import the BCL (Base Class Libraries) as well 
as user-defined namespaces if required.

This is similar to the included statements in the C programming language or the import and require
statements in JavaScript.

Suppose you want to use some classes and interfaces in your code, then you have to include the namespace(s)
from where these classes and interfaces are defined.

For example, if you are going to use the Console class in your code, then you have to include the System namespace
as the Console class belongs to the System namespace.

**Syntax**: `using NameSpaceName;`  
**Example**: `using System;`

If the required namespace is a member of another namespace, we have to specify the parent and child namespaces 
separated by a dot as follows:  
`using System.Data;`  
`using System.IO;`  

<note>
A namespace is a container that contains a group of related classes and interfaces.

A namespace can also contain other namespaces.
</note>

## Namespace Declaration Section
This is where we can define our own custom namespaces.

In .NET applications, all classes and interfaces or any type related to the project should be declared inside 
some namespace.

Generally, we put all the related classes under one namespace and in a project, we can create multiple namespaces.

**Syntax**: `namespace NameSpaceName {}`  
**Example**: `namespace HelloWorld {}`

## Class Declaration Section
For every Desktop Application in .NET, we need a start-up class file.

**A start-up class is a class that contains the `Main()` method, program execution usually starts from the `Main()`
method**

For example, for every .NET Desktop Application like Console and Windows, there should be a Start-Up class that 
should have the Main method from where the program execution is going to start.

When we create a Console Application using Visual Studio, by default, Visual Studio will Create the Start-Up class 
file with the name Program.cs which will have a class with the name Program that contains the Main method.

You can change this default behavior. You can create your own class and you can also make that class as the 
Start-Up Class by including the Main method. In our upcoming articles, we will discuss this in detail.

**Syntax:**
```C#
class ClassName
{
}
```
**Example:**
```C#
class Program
{
}
```

## Main() Method
The main() method is the entry point or starting point of the application to start its execution.

When the application starts executing, the main method will be the first block of the application to be executed. 