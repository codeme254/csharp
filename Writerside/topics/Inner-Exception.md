# Inner Exception

The Inner Exception in C# is a property of the Exception class. If you go to the definition of the Exception
class, then you will see that it is a read-only property i.e. having only get accessor as shown in the below image.

![Inner Exception is Read Only](exception-handling-inner-exception-is-read-only.png)

As this property is defined in the parent Exception class, so this property is available to all the Child classes
including the Custom Exception classes.

**public Exception InnerException {get;}**: This InnerException property gets the Exception instance that caused the 
current exception. It returns an object that describes the error that caused the current exception. The InnerException
property returns the same value that passed into the constructor, or null if the inner exception value was not 
supplied to the constructor.

To simplify the above definition, we can say that, when there is a series of exceptions, then the Most Current 
Exception Obtains the Previous Exception Details in the InnerException Property. Suppose, in our application, 
from Method1, we are calling Method2. In Method2, we are getting one exception let’s say divide by zero exception, 
and then from Method1 we are getting another exception, let’s say Format exception. Then, in this case, 
the current exception or the latest exception is Format Exception and in the Format Exception InnerException property, 
you will get the previous exception details i.e. Divide By Zero Exception.


## Inner Exception Examples in C#


```C#
using System;

namespace TryCatch
{
    internal class InnerException
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
                    throw new Exception("Divisor cannot be an odd number");
                }
                Result = Number1 / Number2;
                Console.WriteLine($"{Number1} / {Number2} = {Result}");
            }
            catch (Exception ex)
            {

                Console.WriteLine("Something went wrong...");
                Console.WriteLine(ex.Message);

                try
                {
                    throw new Exception("Some exception", ex);
                }
                catch (Exception e)
                {
                    Console.WriteLine(e.InnerException);
                }
            }
        }
    }
}
```
This program takes two numbers from the user, checks if the second number (the divisor) is odd, and divides the 
two numbers if it isn’t. If the divisor is odd, it throws an exception with the message “Divisor cannot be an 
odd number.” The catch block then catches that exception, displays an error message, and throws a 
new exception while passing the original one (ex) as its inner exception. The inner exception helps preserve the 
original error that caused the new one, making it easier to trace the actual problem when debugging.