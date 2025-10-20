# Methods and Properties of the Console Class

In order to implement the user interface in console applications, Microsoft provided us with a class called Console.

The Console class is available in the System namespace.

This Console class provides some methods and properties using which we can implement the user interface in a 
console application.

In order words, if we want to work with the console window either for taking user input or to show the output, we 
are provided with the Console in C#.

According to Microsoft documentation the Console class represents the standard input, output, and error streams for 
console applications and this class cannot be inherited because it is a static class i.e. declared as static.

Since the Console class is a static class, all the properties and methods available in the Console class are static as
well, this means we can access these members by using the Console class name without creating an instance.

## Properties of the Console Class in C#
### Title
It gets or sets the title to display in the console title bar.

It returns the string to be displayed in the title bar of the console. The maximum length of the title string is
24500 characters.

```C#
using System;

namespace ConsoleClass
{
    internal class Program
    {
        static void Main()
        {
            Console.Title = "C# is Awesome";
            Console.WriteLine(Console.Title); // C# is Awesome
        }
        
    }
}
```

### BackgroundColor
It gets or sets the background color of the console.

Background color in this case refers to the color that appears behind each character.

It returns a value that specifies the background color of the console; that is, the color that appears behind 
each character. The default is black.

```C#
using System;

namespace ConsoleClass
{
    internal class Program
    {
        static void Main()
        {
            Console.BackgroundColor = ConsoleColor.Green;
            Console.WriteLine(Console.BackgroundColor);
        }
        
    }
}
```

### Foreground Color
It gets or sets the foreground color of the console.

Foreground color in this case means the color of each character that is displayed.

It returns a ConsoleColor that specifies the foreground color of the console; that is, the color of each character 
that is displayed. The default is gray.

```C#
using System;

namespace ConsoleClass
{
    internal class Program
    {
        static void Main()
        {
            Console.ForegroundColor = ConsoleColor.Yellow;
            Console.WriteLine(Console.ForegroundColor);
        }
        
    }
}
```

[You can get more of these properties here](https://learn.microsoft.com/en-us/dotnet/api/system.console)

![console properties](console-properties.png)


## Methods of the Console Class
### Write("string")
This method is used to write the specified string value to the standard output stream.

```C#
using System;

namespace ConsoleClass
{
    internal class Program
    {
        static void Main()
        {
            Console.Write("Hello, World");
        }
        
    }
}

```

### WriteLine("string")
This method is used to write the specified string value, followed by the current line terminator, to the standard 
output stream.

That means this method same as the write method but automatically moves the cursor to the next line after 
printing the message.

```C#
using System;

namespace ConsoleClass
{
    internal class Program
    {
        static void Main()
        {
            Console.WriteLine("Hello, World");
        }
        
    }
}

```

### Read()
This method read a single character from the keyboard and returns its ASCII value.

The Datatype should be int as it returns the ASCII value.

```C#
using System;

namespace ConsoleClass
{
    internal class Program
    {
        static void Main()
        {
            Console.Write("Type a character: ");
            int value = Console.Read();
            Console.WriteLine("Ascii is "+ value);
        }
        
    }
}
```

### ReadLine()
This method reads a string value from the keyboard and returns the entered value only.

As it returns the entered string value so the DataType is going to be a string.

```C#
using System;

namespace ConsoleClass
{
    internal class Program
    {
        static void Main()
        {
            Console.Write("What is your full name: ");
            string name = Console.ReadLine();
            Console.WriteLine(name);
        }
        
    }
}

```
### Clear()
It is used to clear the console buffer and corresponding console window of display information.

In simple words, it is used to clear the screen.

```C#
using System;

namespace ConsoleClass
{
    internal class Program
    {
        static void Main()
        {
            Console.WriteLine("Hello, World");
            Console.Clear();
        }
        
    }
}
```

[you can get more methods here](https://learn.microsoft.com/en-us/dotnet/api/system.console)
