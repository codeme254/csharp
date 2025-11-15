# Anonymous Methods

As the name suggests, an anonymous method in C# is a method without a name.

The Anonymous Methods in C# are defined using the delegate keyword and can be assigned to a variable of the 
delegate type.

Up until now, the approach we have been using with delegates is as follows:
1. Create a delegate
2. Create an instance of the delegate
3. Pass the method we want to execute as a parameter to the delegate constructor, and the delegate will point to this
function.
4. Invoke the delegate and the function the delegate is pointing to will be executed.

Here is an example

```c#
using System;

namespace ExampleDelegate
{
    internal class Program
    {
        public delegate string GreetingDelegate(string name);

        public static string Greetings(string name)
        {
            return $"Hello {name}, how do you do";
        }
        static void Main(string[] args)
        {
            GreetingDelegate gd = new GreetingDelegate(Greetings);
            string msg = gd.Invoke("Dennis");
            Console.WriteLine(msg);
        }
    }
}
```

In the example above:
1. We create one delegate (GreetingDelegate)
2. Then we instantiate the delegate, while we are instantiating the delegate, we are passing the Method name 
(Greetings) as a parameter to the constructor of the delegate
3. Finally, we invoke the delegate

As of now, this is the approach we are following to bind a method to a custom delegate and execute it.

An anonymous method in C# is also related to a delegate.

Without binding a named block (function or method) to a delegate, we can also bind a code block (unnamed code block) 
to a delegate which is nothing but an anonymous method in C#.

## Example to understand Delegates
The following example is the same as the previous example except here instead of binding the delegated with a named 
block (method or function), we are binding the delegate with an anonymous method

```C#
using System;

namespace AnonymouseMethods
{
    internal class Program
    {
        public delegate string GreetingDelegate(string name);

        static void Main(string[] args)
        {
            GreetingDelegate gd = delegate (string name)
            {
                return $"Hello {name}, how do you do";
            };
            string msg = gd.Invoke("Dennis");
            Console.WriteLine(msg);
        }
    }
}
```

## Limitations of Anonymous Methods
**An anonymous method in C# cannot contain any jump statement like goto, break or continue**

![No jump statements](delegates-anonymous-methods-limitation-1.png)

**Anonymous Method in C# cannot access the ref or out parameter of an outer method.**

![no ref or out parameter of an outer method](delegates-anonymous-methods-limitation-2.png)

## Points to remember when working with anonymous methods
1. The anonymous methods are defined using the delegate keyword
2. An anonymous method must be assigned to a delegate type.
3. This method can access outer variables or functions except for the outer function ref and out parameter.
4. An anonymous method can be passed as a parameter.
5. This method can be used as an event handler (more about this later).