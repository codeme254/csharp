# Interface

The Interface in C# is a Fully Unimplemented Class used for declaring a set of operations/methods of an object.

So, we can define an interface as a pure abstract class, which allows us to define only abstract methods.

Interfaces are used to achieve multiple inheritance which is not possible using classes in C#.

Interfaces are also used to achieve abstraction because the methods cannot have a method body.

Interfaces allow you to define a common set of functionality that multiple classes can share, promoting code 
reusability and ensuring a consistent structure for related classes.

## Difference Between Concrete Class, Abstract Class and Interface in C# { caps="title" }
1. **Concrete class/class**:  Contains only the Non-Abstract Methods (Methods with Method Body).
2. **Abstract class**: Contains both Non-Abstract Methods (Methods with Method Body) and Abstract Methods 
(Methods without Method Body).
3. **Interface**: Contain only Abstract Methods (Methods without Method Body).

Generally, a class inherits from another class to consume members of its Parent. On the other hand, if a class 
inherits from an interface, it is to implement the members of its Parent (Interface), not for consumption.

## How to define an interface in C# { caps="title" }

The way we define a class in the same way we need to define an interface in C#. In a class declaration, we 
need to use the class keyword, whereas in an interface declaration, we need to use the interface keyword. 
Moreover, in an interface, we can only declare abstract members. For a better understanding, please 
have a look at the below diagram.

![How to define an interface](interface-defining-an-interface.png)

**NOTE: The convention for naming an interface is to start it with an uppercase 'I'**

```C#
interface ITestInterface {
    // Abstract Members Declaration
}
```

## how to define abstract methods in an interface in C# { caps="title" }

In a class (i.e., Abstract Class), we generally use the abstract keyword to define abstract methods as follows.

```C#
public abstract void Add(int num1, int num2);
```

If you want to write the above abstract method in an interface, then you don’t require public and abstract 
keywords in the method signature as follows:

```C#
void Add(int num1, int num2);
```

While working with interfaces, you need to remember the following rules:
- The default scope for an interface’s members is public, whereas it is private in the case of a class.
- By default, every member of an interface is abstract, so we aren’t required to use the abstract modifier on 
it again, just like we do in the case of an abstract class.
- We cannot declare fields/variables, constructors, and destructors in an interface in C#.
- An interface can inherit from another interface the same way a class inherits from another class.
- Every member of an interface should be implemented under the child class without fail (mandatory), however, while
implementing, we aren't required to use the **override** modifier just like the case of an abstract class.

## Example to understand interfaces in C# { caps="title" }

```C#
using System;

namespace Interfaces
{
    interface IMath
    {
        void Add(int x, int y);
        void Sub(int x, int y);
        void Mul(int x, int y);
        void Div(int x, int y);
    }

    class Math : IMath
    {
        public void Add(int x, int y)
        {
            Console.WriteLine(x * y);
        }

        public void Sub(int x, int y)
        {
            Console.WriteLine(x - y);
        }

        public void Mul(int x, int y)
        {
            Console.WriteLine(x * y);
        }

        public void Div(int x, int y)
        {
            Console.WriteLine(x / y);
        }
    }
    internal class Interfaces
    {
        static void Main(string[] args)
        {
            Math m = new Math();
            m.Mul(5, 3);
            m.Sub(5, 3);
            m.Add(5, 3);
            m.Div(5, 3);
        }
    }
}
```

We cannot create an instance of an interface, but we can create a reference of an interface. The interface reference 
is going to hold the child class instance. We can only invoke the methods declared in the interface using the 
interface reference.

```C#
using System;

namespace Interfaces
{
    interface IMath
    {
        void Add(int x, int y);
        void Sub(int x, int y);
        void Mul(int x, int y);
        void Div(int x, int y);
    }

    class Math : IMath
    {
        public void Add(int x, int y)
        {
            Console.WriteLine(x * y);
        }

        public void Sub(int x, int y)
        {
            Console.WriteLine(x - y);
        }

        public void Mul(int x, int y)
        {
            Console.WriteLine(x * y);
        }

        public void Div(int x, int y)
        {
            Console.WriteLine(x / y);
        }

        public void Mod(int x, int y)
        {
            Console.WriteLine(x % y);
        }
    }
    internal class Interfaces
    {
        static void Main(string[] args)
        {
            IMath m = new Math();
            m.Mul(5, 3);
            m.Sub(5, 3);
            m.Add(5, 3);
            m.Div(5, 3);
            //m.mod(5, 3); // Error
        }
    }
}
```
