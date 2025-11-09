# Multiple Catch Blocks

It is possible in C#, to write multiple catch blocks for a given try block.

When we implement multiple catch blocks in C# for a given try block, then at any given point of time only one
catch block is going to be executed and other catch blocks will be ignored.

## Example
As you can see, here, we created two catch blocks for the given try block. The first catch block takes the 
DivideByZeroException class as the input parameter and the second catch block takes the FormatException 
class as the input parameter.

```C#
using System;

namespace TryCatch
{
    internal class MutlipleCatchBlocks
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
            catch(DivideByZeroException dbze)
            {
                Console.WriteLine("Second number should not be zero");
            }
            catch(FormatException fe)
            {
                Console.WriteLine("Only integer numbers allowed");
            }
        }
    }
}
```
If we enter zero as the second number, the DivideByZeroException catch block is what gets executed:

![DivideByZeroException](exception-handling-multiple-catch-blocks-dbze.png)

If we enter an input with bad number format, the FormatException catch block is what gets executed:

![Format Exception](exception-handling-multiple-catch-blocks-fe.png)

Whenever we implement Multiple Catch Blocks in C#, then it is not possible to write the catch blocks in the following 
manner, it raises to compilation error because the first catch block Exception can handle all the exceptions as it 
is the parent class of the child exception classes and it does not make any sense to write the further catch blocks 
as they are never going to be executed. 

![Bad format](exception-handling-bad-format.png)
_Bad format for exception handling_

## Catching all exceptions with a single catch block
We can catch all exceptions with a single catch block with the parameter Exception.

The Exception class is the superclass of all Child Exception classes and hence it can handle all types of exceptions 
thrown in the try block.

We need to use this catch block only for stopping the abnormal termination irrespective of the exceptions thrown 
from its corresponding try block.

This is what we refer to as a **generic Catch block**.

```C#
using System;

namespace TryCatch
{
    internal class GenericCatchBlock
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
            catch(Exception ex )
            {
                Console.WriteLine("Something went wrong");
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

Now, in the above example, for any type of exception, the generic catch block is going to be executed.

<note>
It is always recommended to write a catch block with the Exception parameter as the last catch block even though we 
are writing multiple catch blocks. It acts as a backup catch block.

Below is the syntax to do the same
</note>

![Exception handling multiple catch block recommendation](exception-handling-multiple-catch-block-recommendation.png)

Here is an example:

```C#
using System;
namespace ExceptionHandlingDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            int Number1, Number2, Result;
            try
            {
                Console.WriteLine("Enter First Number");
                Number1 = int.Parse(Console.ReadLine());
                Console.WriteLine("Enter Second Number");
                Number2 = int.Parse(Console.ReadLine());
                Result = Number1 / Number2;
                Console.WriteLine($"Result: {Result}");
            }
            
            catch (DivideByZeroException DBZE)
            {
                Console.WriteLine("Second Number Should Not Be Zero");
            }
            catch (FormatException FE)
            {
                Console.WriteLine("Enter Only Integer Numbers");
            }
            catch (Exception ex)
            {
                Console.WriteLine("Generic Catch Block...");
            }
            Console.ReadKey();
        }
    }
}
```