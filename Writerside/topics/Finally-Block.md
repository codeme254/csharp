# Finally Block

The keyword finally establishes a block that definitely executes the statements placed in it irrespective of 
whether any exception has occurred or not.

This means that code inside the catch block will always be executed irrespective of whether an exception occurred or did
not occur.

Following is the syntax to use finally block in C#:

![Finally block syntax](exception-handling-finally-block-syntax.png)

As you can see, we can write the finally block in two ways:
- **try, catch, finally**: In this case, the exception will be handled, and stopping the abnormal termination along
with the statements that are placed within the “finally” block gets executed.
- **try, finally**: In this case, abnormal termination will not stop when a runtime error occurs because exceptions
are not handled but even if an abnormal termination occurs, the finally blocks get executed.

## Example to understand the finally block

```C#
using System;

namespace TryCatch
{
    internal class FinallyBlock
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
            catch (DivideByZeroException dbze)
            {
                Console.WriteLine("Second number should not be zero");
            }
            catch (FormatException fe)
            {
                Console.WriteLine("Only integer numbers allowed");
            }
            finally
            {
                Console.WriteLine("This is the finally block");
            }
        }
    }
}
```
Below are example to prove that the finally block is always guaranteed to be executed:

![Example 1](exception-handling-finally-block-example-1.png)

![Example 2](exception-handling-finally-block-example-2.png)

![Example 3](exception-handling-finally-block-example-3.png)