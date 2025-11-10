# Delegates and Lambda Expressions

Delegates in C# are type-safe function pointers.

They hold the reference of a method or function and then call that method for execution.

Think of a delegate as a *variable that can hold a function*.

In simple terms:
> A delegate lets you store methods in variables, pass methods as parameters, and call them dynamically.

Delegates in C# allow us to treat functions as first class citizens in a way:
- You can assign a function to a variable (a delegate variable).
- You can pass a function as an argument to another function.
- You can store a function in a collection (e.g a list of delegates).
- You can return a function from another function.
- You can invoke a function directly through a variable.

## How to create a delegate in C#
A delegate can be defined using the **delegate** keyword.

The syntax for defining a delegate in C# is as follows:

`<access modifier> delegate <return type> <delegate name> (parameter list);`

For example:
```C#
public delegate void GreetDelegate(string name);
```
This defines a delegate type that:
- Returns void
- Takes one parameter of type string

Now create methods that match that signature:
```C#
void SayHello(string name)
{
    Console.WriteLine($"Hello, {name}!");
}

void SayGoodbye(string name)
{
    Console.WriteLine($"Goodbye, {name}!");
}
```
Next, create a delegate instance:
```C#
GreetDelegate greet;

greet = SayHello; // assign method
greet("Dennis");  // calls SayHello("Dennis")

greet = SayGoodbye; // reassign
greet("Dennis");    // calls SayGoodbye("Dennis")
```

## Full Example
Below is a full example which we will discuss later in details:
```C#
using System;
using System.Security.Cryptography.X509Certificates;

namespace Delegates
{
    internal class Program
    {
        // Delegate
        public delegate void GreetDelegate(string name);

        // SayHello method that matches the signature of GreetDelegate delegate
        static void SayHello(string name)
        {
            Console.WriteLine($"Hello {name}");
            Console.WriteLine($"How do you do {name}");
        }

        // SayGoodbye method that matches the signature of GreetDelegate delegate
        static void SayGoodbye(string name)
        {
            Console.WriteLine($"Goodbye {name}");
        }
        static void Main(string[] args)
        {
            GreetDelegate greet;
            greet = SayHello;
            greet("Dennis");

            greet = SayGoodbye;
            greet("Dennis");
        }
    }
}
```
In the example above, **SayHello** and **SayGoodbye** are referred to as **Handlers**.

A handler is simply a method that matches the delegate’s signature, so it can be attached and invoked 
through that delegate.

The delegate signature and handler method signature must be matched.

In our case, as we have defined the delegate with one parameter, the handler must also have the same number, type
and order of parameters as the delegate.

Note: the parameter names do not matter, what matters is the number, type and order of the parameters in the delegate
and the handler.

## Delegate Base Class in C#
One of the really core classes in the .NET Framework is Delegate which provides some base functionalities.

If you go to the definition of the Delegate class, then you will see that it is an abstract class as shown in 
the below image.

![Delegate base class](delegates-delegate-base-class.png)

## MulticastDelegate Base Class in C#
If you go to the definition of MulticastDelegate class, you will see that this class is also an abstract class and is
inherited from the Delegate abstract class as shown in the image below:

![Multicast delegate base class](delegates-multicastdelegate-base-class.png)

Every delegate that we create, once compiled will inherit from Multicast delegate.

Multicast Delegate is a way to hold multiple delegates.

In your code while declaring the delegate, you cannot directly inherit from the Delegate or Multicast Delegate 
classes. The way you need to do this is to use the delegate keyword and the rest of the things are done by the compiler.

These are the special base classes that the compiler restricts us from directly inheriting. Once the compiler sees 
the delegate keyword in the signature, then it will automatically generate the class that inherits from the 
Multicast Delegate.

## How to use a delegate
Upto this point, we know how to create a delegate, let's talk about the handler methods.
- If the handler method is a static method, you can access that method directly or using the class name.
- If the handler method is non-static, then you need to access the handler method  using the object name.


_if the handler method is a static method, you can access that method directly, or using the class name_
```C#
using System;

namespace Delegates
{
    internal class Program
    {
        // Delegate
        public delegate void GreetDelegate(string name);

        // SayHello method that matches the signature of GreetDelegate delegate
        static void SayHello(string name)
        {
            Console.WriteLine($"Hello {name}");
            Console.WriteLine($"How do you do {name}");
        }

        // SayGoodbye method that matches the signature of GreetDelegate delegate
        static void SayGoodbye(string name)
        {
            Console.WriteLine($"Goodbye {name}");
        }
        static void Main(string[] args)
        {
            GreetDelegate greet;
            greet = SayHello;
            greet("Dennis");

            greet = SayGoodbye;
            greet("Dennis");
        }
    }
}
```
_if the handler method is non-static, then you need to access the handler method using the object name_
```C#
using System;

namespace Delegates
{
    internal class Delegates
    {
        // Delegate
        public delegate void GreetDelegate(string name);

        // SayHello method that matches the signature of GreetDelegate delegate
        void SayHello(string name)
        {
            Console.WriteLine($"Hello {name}");
            Console.WriteLine($"How do you do {name}");
        }

        // SayGoodbye method that matches the signature of GreetDelegate delegate
        void SayGoodbye(string name)
        {
            Console.WriteLine($"Goodbye {name}");
        }
        static void Main(string[] args)
        {
            Delegates d = new Delegates();
            GreetDelegate greet;
            greet = d.SayHello;
            greet("Dennis");

            greet = d.SayGoodbye;
            greet("Dennis");
        }
    }
}
```

Delegates can also be used as shown:

```C#
using System;

namespace Delegates
{
    internal class Delegates
    {
        // Delegate
        public delegate void GreetDelegate(string name);

        // SayHello method that matches the signature of GreetDelegate delegate
        void SayHello(string name)
        {
            Console.WriteLine($"Hello {name}");
            Console.WriteLine($"How do you do {name}");
        }

        // SayGoodbye method that matches the signature of GreetDelegate delegate
        void SayGoodbye(string name)
        {
            Console.WriteLine($"Goodbye {name}");
        }
        static void Main(string[] args)
        {
            Delegates d = new Delegates();
            GreetDelegate gd = new GreetDelegate(d.SayHello);
            gd("Dennis");
            gd = new GreetDelegate(d.SayGoodbye);
            gd("Dennis");
        }
    }
}
```