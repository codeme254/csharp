# Handling exceptions Logically

In a logical implementation, we need to handle exceptions using logical statements.

We should always try to handle exceptions logically, if it is impossible to handle an exception logically, then we
go for try-catch implementation.

## Example
In the following example, we are logically checking if the second number is zero, if it is, we are printing a simple
message saying that the second number should not be zero. If the second number is not zero, then we are performing our
division operation and showing the results.

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
            if (b == 0)
            {
                Console.WriteLine("Cannot divide by zero");
            } else
            {
                Console.WriteLine($"A = {a}");
                Console.WriteLine($"B = {b}");
                c = a / b;
                Console.WriteLine($"C = {c}");
            }
        }
    }
}
```
If we are unable to handle exceptions logically, we need to go for try-catch implementation