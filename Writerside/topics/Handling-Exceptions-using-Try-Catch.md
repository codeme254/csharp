# Handling Exceptions using Try-Catch

The .NET framework provides three keywords to implement the try-catch implementation. 

They are as follows:
- try
- catch
- finally

## try
The try keyword establishes a block in which we need to write the exception causing and its related statements.

That means exception-causing statements and the related statements, which we should not execute when an exception 
occurs, must be placed in the try block.

When the exception occurs, the CLR will create an instance of the Exception class based on the logical error and then 
throw that Exception object, which the corresponding catch block will handle.

## catch
The catch block is used to catch the exception that is thrown from its corresponding try block.

It has the logic to take necessary actions on that caught exception.

The Catch block syntax in C# looks like a constructor. It does not take accessibility modifiers, normal modifiers, 
or return types. It takes only a single parameter of type Exception or any child class of the parent Exception class.

Inside the catch block, we can write any statement that is legal in .NET, including raising an exception. In this 
case, we can stop the abnormal termination of the program, and we can also give the user an understandable error
message so that the user can take necessary action to resolve the error.

## finally
The keyword finally establishes a block that definitely executes the statements placed in it irrespective of 
whether any exception has occurred or not.

That means the statements that are placed in finally block are always going to be executed irrespective of whether
any exception is thrown or not.

**This block is optional**

## Syntax to use Exception handling
The following image shows the syntax for using exception handling in C#. It starts with the try block, followed 
by the catch block, and writing the finally block is optional. You can write any number of catch blocks for a 
given try block in C#. This will handle different types of exceptions thrown by the try block.

![try catch syntax](exception-handling-try-catch-syntax.png)

## Example to handle exception using try-catch block with a generic catch block
The catch block without exception class is called a generic catch, and the generic catch block in C# can handle any 
exception raised in the corresponding try block.

```C#
using System;

namespace TryCatch
{
    internal class TryCatch
    {
        static void Main(string[] args)
        {
            int Number1, Number2, Result;
            try
            {
                Console.Write("Enter the first number: ");
                Number1 = Convert.ToInt16(Console.ReadLine());
                Console.Write("Enter the second number: ");
                Number2 = Convert.ToInt16(Console.ReadLine());
                Result = Number1 / Number2;
                Console.WriteLine($"Result = {Result}");
            } catch
            {
                Console.WriteLine("Some error occurred...");
            }
        }
    }
}
```

Sample execution and output:

![Sample execution output](exception-handling-output-2.png)

In the above example, no exception class is used in the try block, which is known as the generic catch block.

The problem with the generic catch block is that if any kind of exception occurs, the same message will be 
displayed to the end user, and the end user cannot understand why the error has occurred; to overcome this,
specific catch blocks are used.

Using specific catch blocks, it is possible to learn more about the exception.

## Properties of the Exception Class in C#
The Exception Class is the superclass of all Exception classes, providing some virtual properties and methods 
which are re-implemented by the child classes.

If you go to the definition of the Exception class, then you will see the following.

![Exception class definition](exception-handling-exception-class-definition.png)

The most important properties are as follows:
- **Message**: This property will store the reason why an exception has occurred.
- **Source**: This property will store the application’s name from which the exception has been raised.
- **HelpLink**: This is used to provide a link to any file /URL to give helpful information to the user
about why this exception is raised.
- **StackTrace**: This is used to provide more information about the Exception, such as the reason for the 
exception, what method and class the exception occurred in, and what line number the exception occurred at, 
which helps us resolve the issue.

A full example is as shown below:

```C#
using System;

namespace TryCatch
{
    internal class TryCatch2
    {
        static void Main(string[] args)
        {
            int Number1, Number2, Result;
            try
            {
                Console.Write("Enter the first number: ");
                Number1 = Convert.ToInt16(Console.ReadLine());
                Console.Write("Enter the second number: ");
                Number2 = Convert.ToInt16(Console.ReadLine());
                Result = Number1 / Number2;
                Console.WriteLine($"Result = {Result}");
            }
            catch (Exception e)
            {
                Console.WriteLine($"Message: {e.Message}");
                Console.WriteLine($"Source: {e.Source}");
                Console.WriteLine($"HelpLink: {e.HelpLink}");
                Console.WriteLine($"StackTrace: {e.StackTrace}");
            }
        }
    }
}
```

Example execution and output:

![example execution and output](exception-handling-catch-block-outputs.png)