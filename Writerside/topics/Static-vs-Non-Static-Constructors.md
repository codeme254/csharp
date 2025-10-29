# Static vs Non-Static Constructors

The following are the differences between static and non-static constructors
## Declaration
If a constructor is explicitly declared by using the static modifier, we call that constructor a static constructor
whereas the rest of the others are called non-static constructors.

```C#
namespace ConstructorsDemo
{
    internal class ConstructorsDemo
    {
        static ConstructorsDemo()
        {
            Console.WriteLine("This is a static constructor");
        }

        public ConstructorsDemo()
        {
            Console.WriteLine("This is a non-static constructor");
        }
        static void Main(string[] args)
        {
            Console.WriteLine("Constructors");
        }
    }
}
```

## Fields
Static Fields/Variables are initialized by static constructors and non-static fields/variables are initialized
by non-static or instance constructors.

```C#
namespace ConstructorsDemo
{
    internal class ConstructorsDemo
    {
        static int x;
        int y;
        static ConstructorsDemo()
        {
            Console.WriteLine("This is a static constructor");
            x = 55;
        }

        public ConstructorsDemo()
        {
            Console.WriteLine("This is a non-static constructor");
            y = 99;
        }
        static void Main(string[] args)
        {
            Console.WriteLine("Constructors");
        }
    }
}
```

## Invoking
Static constructors are implicitly called whereas non-static constructors are explicitly called.

```C#
namespace ConstructorsDemo
{
    internal class ConstructorsDemo
    {
        static int x;
        int y;
        static ConstructorsDemo()
        {
            Console.WriteLine("This is a static constructor");
            x = 55;
        }

        public ConstructorsDemo()
        {
            Console.WriteLine("This is a non-static constructor");
            y = 99;
        }
        static void Main(string[] args)
        {
            ConstructorsDemo d = new ConstructorsDemo();
        }
    }
}
```

Even though we are only calling the non-static constructor, the output of the program above will be:

![output](constructors-static-vs-non-static-output.png)

This is because static constructors are called implicitly.

## Number of Times of Execution
Static Constructors execute immediately once the execution of a class start and moreover, it is the first block of
code to run under a class whereas non-static constructors execute only after creating the instance of the class as 
well as each and every time the instance of the class is created.

```C#
namespace ConstructorsDemo
{
    internal class ConstructorsDemo
    {
        static int x;
        int y;
        static ConstructorsDemo()
        {
            Console.WriteLine("This is a static constructor");
            x = 55;
        }

        public ConstructorsDemo()
        {
            Console.WriteLine("This is a non-static constructor");
            y = 99;
        }
        static void Main(string[] args)
        {
            ConstructorsDemo d1 = new ConstructorsDemo();
            ConstructorsDemo d2 = new ConstructorsDemo();
            ConstructorsDemo d3 = new ConstructorsDemo();
            ConstructorsDemo d4 = new ConstructorsDemo();
            ConstructorsDemo d5 = new ConstructorsDemo();
        }
    }
}
```

![output](constructors-number-of-times-of-execution.png)

## Parameters
Non-Static Constructors can be parameterized whereas the static constructors cannot have any parameter.

This is because we explicitly call the non-static constructors, so we can have a chance to pass parameters. On the 
other hand, static constructors are implicitly called and it is the first block of code to run under a class, and 
hence we don’t have any chance to pass parameters.

```C#
namespace ConstructorsDemo
{
    internal class ConstructorsDemo
    {
        static int x;
        int y;
        static ConstructorsDemo()
        {
            Console.WriteLine("This is a static constructor");
            x = 55;
        }

        public ConstructorsDemo(int value)
        {
            Console.WriteLine("This is a non-static constructor");
            y = value;
        }
        static void Main(string[] args)
        {
            ConstructorsDemo d1 = new ConstructorsDemo(99);
        }
    }
}
```

## Overloading
Non-Static Constructors can be overloaded whereas static constructors cannot be overloaded.

Overloading is something that comes into the picture based on the parameters. As we have a chance to pass parameters 
in the case of non-static constructors, overloading is possible. On the other hand, we cannot pass parameters to 
static constructors i.e. static constructors are parameterless, and hence overloading is not possible.

```C#
namespace ConstructorsDemo
{
    internal class ConstructorsDemo
    {
        static int x;
        int y;
        static ConstructorsDemo()
        {
            Console.WriteLine("This is a static constructor");
            x = 55;
        }

        public ConstructorsDemo(int value)
        {
            Console.WriteLine("This is a non-static constructor");
            y = value;
        }

        public ConstructorsDemo(int x, int y)
        {
            Console.WriteLine("Overload 1");
        }

        public ConstructorsDemo(double x, int y)
        {
            Console.WriteLine("Overload 2");
        }

        public ConstructorsDemo(double x, double y)
        {
            Console.WriteLine("Overload 3");
        }
        static void Main(string[] args)
        {
            ConstructorsDemo d1 = new ConstructorsDemo(99);
        }
    }
}
```

**N/B**:
Every class contains an implicit constructor if not defined explicitly and those implicit constructors are defined 
based on the following criteria:
- Every class except a static class contains an implicit non-static constructor if not defined with an explicit 
constructor.
- Static constructors are implicitly defined only if that class contains any static fields or else that constructor
will not be present provided that the class does not have an explicit static constructor.