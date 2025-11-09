# Exception Handling

**An exception is an event which occurs during the execution of a program, that disrupts the normal flow of
program's instructions**.

Exception Handling is a procedure for handling an exception that occurs during the execution of a program.

Exception handling allows developers to separate error-handling logic from the main program logic, ensuring that the
program can respond to unexpected situations without crashing.

## Types of Errors
When we write and execute our code, two types of errors might end up occuring:
- Compilation Errors
- Runtime Errors

### Compilation Errors
The error that occurs in a program during compilation is known as a compilation error (compile-time error).

These errors occur due to syntactical mistakes in the program, for example missing double quotes in a string value,
missing terminators in a statement (not ending a line with semicolon), missing parenthesis, trying to create an object
from an abstract class, wrong keyword spelling e.t.c.

So, whenever we compile the program, the compiler recognizes these errors and shows us the list of errors.

In simple words, this type of error occurs due to a poor understanding of the programming language. The compiler 
identifies these errors, which can be rectified before the program is executed. Thus, these errors do not
harm the program’s execution.

### Runtime Errors
The errors that occur at the time of program execution are called runtime errors.

These errors occur at runtime due to various reasons, such as when we are entering the wrong data into a variable, 
trying to open a file for which there is no permission, trying to connect to the database with the wrong user ID 
and password, the wrong implementation of logic, and missing required resources, etc.

So, in simple words, we can say that the errors that come while running the program are called runtime errors.

Runtime errors are dangerous because whenever they occur in the program, the program terminates abnormally on the
same line where the error occurred without executing the next line of code.

The compiler will never check the logic; it will only check the syntaxes. So, the compiler will identify the 
syntax error but not the logical error.

## What is an Exception
An Exception is a class in C# that is responsible for abnormal program termination when runtime errors occur while
running the program.

These errors (runtime) are very dangerous because whenever they occur, the program terminates abnormally on the same
line where the error occurs without executing the next line of code.

<note>
Most people say Runtime Errors are Exceptions, which is not true. Exceptions are classes that are responsible for 
the abnormal termination of the program when runtime errors occur.
</note>

Objects of Exception classes are responsible for abnormal termination of the program whenever runtime errors occur.

These exception classes are predefined under BCL (Base Class Libraries), where a separate class is provided for every 
different type of exception, like:
- IndexOutOfRangeException
- FormatException
- NullReferenceException
- DivideByZeroException
- FileNotFoundException
- SQLException,
- OverFlowException, etc.

Each exception class provides a specific exception error message. All the above exception classes are responsible for
abnormal program termination and will display an error message that specifies the reason for abnormal termination, 
i.e., they provide an error message specific to that error.

So, whenever a runtime error occurs in a program, first, the Exception Manager under the CLR (Common Language Runtime)
identifies the type of error that occurs in the program. Then, the Exception Manager creates an object of the 
Exception class related to that error and throws that object, which will immediately terminate the program abnormally 
on the line where the error occurred and display the error message related to that class.

## Example of a program execution with an exception
The following example shows program execution with an exception.

As you can see in the code below, we are dividing an integer number by 0, which is impossible in mathematics. So,
it will throw the Divide By Zero Exception in this case.

The statements present before the exception-causing statement, i.e., before c = a / b, are executed, and the 
statements present after the exception-causing statement will not be executed.

```C#
using System;

namespace ExceptionHandling
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int a = 20;
            int b = 0;
            int c;
            Console.WriteLine($"A = {a}");
            Console.WriteLine($"B = {b}");
            c = a / b;
            Console.WriteLine($"C = {c}");
        }
    }
}
```
The output of the program above will be as follows:

![Output](exception-handling-output.png)

## How to handle exceptions
There are two methods for handling exceptions:
- Logical implementation
- Try Catch Implementation

