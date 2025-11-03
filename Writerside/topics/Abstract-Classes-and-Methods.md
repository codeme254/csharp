# Abstract Classes and Methods

In C#, an abstract class is a class that serves as a blueprint for other classes.

Abstract classes cannot be instantiated directly, but they can be used as base classes for other classes 
that derive from them.

Abstract classes are declared using the abstract keyword. They often define a common set of characteristics or 
behaviors that should be shared among multiple derived classes.

Abstract methods are methods that have been declared inside an abstract class or interface and these methods do not have
a method body or implementation in the declaring class or interface. Instead, the responsibility for implementing
the method is delegated to any concrete (non-abstract) class that derives from the abstract class or implements
the interface.

A method without the body is known as the Abstract Method. What the method contains is only the declaration of the 
method. That means the abstract method contains only the declaration, no implementation.

<note>
Note: Every abstract method declared within an abstract class must and should be implemented by the Child classes 
without fail; otherwise, we will get a compile-time error.

<strong>Abstract classes can also contain non-abstract methods. If a class is non-abstract, it contains only
non-abstract methods, but if a class is abstract, it contains both abstract and non-abstract methods</strong>
</note>

## Example to understand abstract class and abstract methods in C# { caps="title" }
In this class, we have defined two non-abstract methods, i.e., Add and Sum, and two abstract methods, i.e., Mul and Div.

```C#
using System;

namespace AbstractClassesAndMethods
{
    abstract class AbstractClass
    {
        public void Add(int x, int y)
        {
            Console.WriteLine(x + y);
        }

        public void Sub(int x, int y)
        {
            Console.WriteLine(x - y);
        }
        public abstract void Mul(int x, int y);
        public abstract void Div(int x, int y);
    }
}
```

Suppose there is a child class for the above AbsParent class. Then, the child class has to implement the 
Mul and Div abstract methods.

## Why abstract classes cannot be instantiated { caps="title" }
Abstract classes can contain abstract methods which are not fully implemented.

If the compiler allows us to create the object for an abstract class, we can invoke the abstract method using 
that object, which CLR cannot execute at runtime.

To restrict calling abstract methods which might not have been fully implemented, the compiler does not allow us to
instantiate an abstract class.

## Implementing abstract methods in child class { caps="title" }
Use the **override** keyword to implement abstract methods inside a child class.

```C#
using System;

namespace AbstractClassesAndMethods
{
    abstract class AbstractClass
    {
        public void Add(int x, int y)
        {
            Console.WriteLine(x + y);
        }

        public void Sub(int x, int y)
        {
            Console.WriteLine(x - y);
        }
        public abstract void Mul(int x, int y);
        public abstract void Div(int x, int y);
    }

    class AbstractChild : AbstractClass
    {
        public override void Mul(int x, int y)
        {
            Console.WriteLine(x * y);
        }

        public override void Div(int x, int y)
        {
            Console.WriteLine(x / y);
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            AbstractChild c = new AbstractChild();
            c.Mul(5, 3);
            c.Div(5, 3);
            c.Add(5, 3);
            c.Sub(5, 3);
        }
    }
}
```

## Summary of abstract classes and methods in C# { caps="title" }
1. A method that does not have a body is called an abstract method, and the class that is declared using the 
keyword abstract is called an abstract class. If a class contains an abstract method, it must be declared abstract.
2. An abstract class can contain both abstract and non-abstract methods. If a child class of an abstract class
wants to consume any non-abstract methods of its parent, it should implement all abstract methods.
3. An abstract class is never usable in itself because we cannot create the object of an abstract class. The 
members of an abstract class can be consumed only by the child class of the abstract class.