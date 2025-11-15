# Lambda Expressions

The Lambda Expression in C# is the shorthand for writing the Anonymous Functions.

## How to Create Lambda Expression in C#
We use the lambda operator **=>**.

To create a lambda expression in C#, we need to specify the input parameters (if any) on the left side 
of the lambda operator, and we need to put the expression or statement block within the open and close curly braces.

In the example below, we have replaced the delegate keyword with the lambda operator (**=>**), and we have also
removed the data type of the parameter as the delegate knows the data type of the parameter:

```C#
using System;

namespace LambdaExpressions
{
    internal class Program
    {
        public delegate string GreetingDelegate(string name);

        static void Main(string[] args)
        {
            GreetingDelegate gd =  (name) =>
            {
                return $"Hello {name}, how do you do";
            };
            string msg = gd.Invoke("Dennis");
            Console.WriteLine(msg);
        }
    }
}
```

If your lambda expression is only taking one parameter, you can drop the parenthesis:

```C#
using System;

namespace LambdaExpressions
{
    internal class Program
    {
        public delegate string GreetingDelegate(string name);

        static void Main(string[] args)
        {
            GreetingDelegate gd =  name =>
            {
                return $"Hello {name}, how do you do";
            };
            string msg = gd.Invoke("Dennis");
            Console.WriteLine(msg);
        }
    }
}
```