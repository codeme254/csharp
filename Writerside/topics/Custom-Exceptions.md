# Custom Exceptions

Before understanding how to create Custom Exceptions, let us first understand what are the different types of
Exceptions available.

In C#, exceptions are divided into two:
- **System exception**: caused by the CLR
- **Application exception**: caused by the programmer.

The Exception is the parent class of all Exception classes. From the Exception class, SystemException and 
ApplicationException classes are defined.

![Classification of exceptions](exception-handling-types-of-exceptions.png)

As you can see, for both SystemException and ApplicationException, the parent is the Exception class only.

By default, all the System Exception classes are inherited from the SystemException class which is inherited from 
the Exception class and if we are creating any Application Exception i.e. Custom Exception or user-defined exception, 
then that class should and must be inherited from the Exception class

## System Exceptions
An exception that is raised implicitly under a program at runtime by the Exception Manager (Component of CLR) because
of some logical mistakes (some predefined conditions) is known as System Exception.

For example, if you are diving an integer number by zero, then one system exception is raised called DivideByZero. 
Similarly, if you are taking an alphanumeric string value from the user and trying to store that value in an 
integer variable, then one system exception is raised called FormatException.

Some examples of system exception are: **DivideByZeroException**, **IndexOutOfRangeException**, **FormatException**,
**SQLException**, **NullReferenceException** e.t.c.

## Application Exceptions
An exception that is raised explicitly under a program based on our own condition (i.e. user-defined condition) 
is known as an application exception.

As programmers, we can raise application exceptions at any given point in time. 

For example, our requirement might be that while performing the division operation, we need to check that if the 
second number is an odd number, if it is, then we need to throw an exception. 

This cannot be handled automatically by the CLR. Then as programmers, we need to create our Custom Exception,
and we need to create an instance of our Custom Exception class, and we need to throw that Custom Exception 
instance using the **throw** keyword explicitly based on our business requirement.

To raise an Application Exception in C#, we need to adopt the following process. First, we need to create a custom 
Exception class by inheriting it from the Parent Exception class and then we need to create an instance of the Custom 
Exception class and then we need to throw that instance.

![Custom exception steps](exception-handling-custom-exception-steps.png)

## Creating Our Own Exceptions
Before creating your own exception have a look at the definition of the exception class shown below:

![Exception class definition](exception-handling-exception-class-definition-2.png)

As you can see, the Exception class has:
- Constructors
- Virtual and non-virtual properties
- Virtual and non-virtual methods

The virtual members you can override in the child of this Exception class and you can directly consume the 
non-virtual members using the child class instance.

Here, you can see that the OddNumberException class is inherited from the built-in Exception class and here we are 
re-implementing two virtual properties i.e. Message and HelpLink.

Now, we can create an instance of OddNumberException class and if we invoke Message and HelpLink properties, 
then these two properties are going to be executed from this class only.

But if you invoke the Source and StackTrace properties, then those properties are going to be executed from the 
Exception class only as we have not re-implemented these properties.

```C#
using System;

namespace TryCatch
{
    public class OddNumberException : Exception
    {
        public override string Message
        {
            get
            {
                return "Divisor cannot be an odd number";
            }
        }

        public override string HelpLink
        {
            get
            {
                return "Learn more about odd number: https://en.wikipedia.org/wiki/Parity_(mathematics)";
            }
        }
    }
    internal class CustomException
    {
        static void Main(string[] args)
        {
            int Number1, Number2, Result;
            try
            {
                Console.Write("Enter the first number: ");
                Number1 = Convert.ToInt32(Console.ReadLine());
                Console.Write("Enter the first number: ");
                Number2 = Convert.ToInt32(Console.ReadLine());

                if (Number2 % 2 != 0)
                {
                    throw new OddNumberException();
                }
                Result = Number1 / Number2;
                Console.WriteLine($"{Number1} / {Number2} = {Result}");
            } 
            catch(OddNumberException one)
            {
                Console.WriteLine(one.Message);
                Console.WriteLine(one.HelpLink);
            }
            // generic catch block - good practice to always have it
            catch(Exception ex)
            {
                Console.WriteLine("Something went wrong...");
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

![Output](exception-handling-custome-exception-output.png)

According to Microsoft, When creating your own exceptions, end the class name of the user-defined exception 
with the word **"Exception"** and implement the three common constructors.

To do so, let us modify the OddNumberException class as follows to include three constructors which call the 
Exception class’s respective constructors.

```C#
using System;

namespace TryCatch
{
    public class OddNumberException2 : Exception
    {
        // Overriding the first constructor
        public OddNumberException2() { }

        // Overriding the constructor that allows us to pass a message
        public OddNumberException2(string message): base(message) { }

        // Overriding the constructor that allows us to pass a message and an inner exception
        public OddNumberException2(string message, Exception innerException): base(message, innerException) { }

        public override string HelpLink
        {
            get
            {
                return "Learn more about odd number: https://en.wikipedia.org/wiki/Parity_(mathematics)";
            }
        }
    }
    internal class CustomExceptions
    {
        static void Main(string[] args)
        {
            int Number1, Number2, Result;
            try
            {
                Console.Write("Enter the first number: ");
                Number1 = Convert.ToInt32(Console.ReadLine());
                Console.Write("Enter the first number: ");
                Number2 = Convert.ToInt32(Console.ReadLine());

                if (Number2 % 2 != 0)
                {
                    throw new OddNumberException2("Divisor cannot be an odd number");
                }
                Result = Number1 / Number2;
                Console.WriteLine($"{Number1} / {Number2} = {Result}");
            }
            catch (OddNumberException one)
            {
                Console.WriteLine(one.Message);
                Console.WriteLine(one.HelpLink);
            }
            // generic catch block - good practice to always have it
            catch (Exception ex)
            {
                Console.WriteLine("Something went wrong...");
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

![Output](exception-handling-custom-exception-result-2.png)