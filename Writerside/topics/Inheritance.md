# Inheritance

Inheritance is a mechanism of consuming members that are defined in one class from another class.

It is a mechanism of consuming the members of one class in another class by establishing a parent/child relationship
between the classes, which provides re-usability.

## How to Implement Inheritance in C# { caps="title" }

Suppose we have a class called A with a set of members. And we have another class B, and we want this class B to be
inherited from class A. The following code shows how to establish the Parent-Child relationship between
Class A and Class B.

![Inheritance](inheritance.png)

- A => Parent class/Base class/Super class
- B => Child class/Derived class/Sub class

Note: In Inheritance, the Child class can consume members of its Parent class as if it is the owner of those 
members (except private members of the parent).

## Rules of Inheritance in C#
These 6 rules must be followed for inheritance to be possible in C#.
### Rule 1
In C#, Note: In Inheritance, the Child class can consume members of its Parent class as if it is the owner of those 
members (except private members of the parent).

The code below will not work:
```C#
using System;

namespace Inheritance
{
    class A
    {
        private A()
        {
            Console.WriteLine("Constructor of A");
        }
        public void Method1()
        {
            Console.WriteLine("This is Method1");
        }
    }

    class B: A
    {
        public void Method2()
        {
            Console.WriteLine("This is Method 2");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
        }
    }
}
```
When we try to execute the code above we will get the following error.
![Rule 1 Error](inheritance-rule-1-error.png)

We are getting the above error because when we create an instance of the child class, the child class constructor 
will implicitly call its parent class constructors. Right now, the Class B constructor trying to call the Class 
A constructor, which is not accessible because that constructor is private.

### Rule 2
In inheritance, the child class can access the parent class members, but the parent classes can never access any 
members that are purely defined in the child class.

The program below will not work:
```C#
using System;

namespace Inheritance
{
    class A
    {
        public A()
        {
            Console.WriteLine("Constructor of A");
        }
        public void Method1()
        {
            Console.WriteLine("This is Method1");
        }
    }

    class B: A
    {
        public void Method2()
        {
            Console.WriteLine("This is Method 2");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            A a = new A();
            a.Method3();
        }
    }
}
```
![Rule 2 Error](inheritance-rule-2-error.png)

### Rule 3
Every class that is defined by us or predefined in the libraries of the language has a default parent class, 
i.e., the Object class of the System namespace, so the members (`Equals`, `GetHashCode`, `GetType`, and 
`ToString`) of the Object class are accessible from anywhere.

Generally, when we define a class, we think that we did not inherit it from any class. But by default, our class 
is Inherited from the Object class. So, Object is the parent class for all the classes defined in our Base Class 
Library as well as all the classes that we defined in our application.

Because Object is the parent class, four important methods (Equals, GetHashCode, GetType, and ToString) of the 
Object class can be called or accessed from anywhere.

Remember the above four methods can be accessed from everywhere. Every class can contain the Equals, GetHashCode, 
GetType, and ToString methods, and this is possible because every class in the .NET framework is inherited
from the Object class.

Now, let us create an object of class A, and when you type obj., then the intelligence shows 6 methods, i.e., 
2 methods (Method1 and Method2) from class A and four methods (Equals, GetHashCode, GetType, and ToString) 
from Object class shown in the below image.

![The 4 Object methods](inheritance-4-object-methods.png)

Every class in the .NET Framework is either directly or indirectly inherited from the Object class.

### Rule 4
In C#, we don’t have support for multiple inheritances through classes.

What we are provided is only a Single Inheritance through classes. That means with classes, only one immediate 
parent class is allowed (i.e., Single, Multilevel, and Hierarchical supported), and more than one immediate parent 
class is not allowed in C# with classes (i.e., Multiple and Hybrid are not supported) - _more about this later_.

### Rule 5
In Rule1, we learned whenever the child class instance is created, the child class constructor will implicitly call 
its parent classes constructor, but this only happens if the parent classes constructor is parameterless.

If the constructor of the Parent class is parameterized, then the Child class constructor cannot implicitly call 
its Parent’s constructor.

So, to overcome this problem, it is the responsibility of the programmer to explicitly call the Parent classes 
constructor from the child class constructor and pass values to those parameters.

To call the Parent’s constructor from the child class, we need to use the `base` keyword.

```C#
using System;

namespace Inheritance
{
    class A
    {
        public A(int number)
        {
            Console.WriteLine($"Number is {number}");
        }
        public void Method1()
        {
            Console.WriteLine("This is Method1");
        }

        public void Method2()
        {
            Console.WriteLine("This is Method2");
        }
    }

    class B: A
    {
        public void Method3()
        {
            Console.WriteLine("This is Method 2");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            
        }
    }
}
```

If we try to execute the code above we will get the following error:
![Rule 5 Error](inheritance-rule-5-error.png)

It is complaining that **"There is no argument given that corresponds to the required formal parameter 'number'
of 'A.A(int)'** and this makes sense. This is because the class B constructor implicitly calls the class 
A constructor. But, if you want to call the class A constructor, it requires an integer parameter now. 
Without passing the parameter, we cannot call the class A constructor. So, now, the class B constructor 
is unable to call the class A constructor.

Implicit calling of the parent constructor is not working in this case, to resolve this issue, we go for explicit 
calling of the parent constructor, the syntax is as shown:

![explicitly calling the parent constructor](inheritance-explicit-calling-of-parent-constructor.png)

```C#
using System;

namespace Inheritance
{
    class A
    {
        public A(int number)
        {
            Console.WriteLine("Constructor of A executed");
            Console.WriteLine($"Number is {number}");
        }
        public void Method1()
        {
            Console.WriteLine("This is Method1");
        }

        public void Method2()
        {
            Console.WriteLine("This is Method2");
        }
    }

    class B: A
    {
        public B(): base(10)
        {
            Console.WriteLine("Constructor of B executed");
        }
        public void Method2()
        {
            Console.WriteLine("This is Method 2");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            A a = new A(5);
        }
    }
}
```

We can also pass dynamic values:

```C#
using System;

namespace Inheritance
{
    class A
    {
        public A(int number)
        {
            Console.WriteLine("Constructor of A executed");
            Console.WriteLine($"Number is {number}");
        }
        public void Method1()
        {
            Console.WriteLine("This is Method1");
        }

        public void Method2()
        {
            Console.WriteLine("This is Method2");
        }
    }

    class B : A
    {
        public B(int num) : base(num)
        {
            Console.WriteLine("Constructor of B executed");
        }
        public void Method2()
        {
            Console.WriteLine("This is Method 2");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            A a = new A(5);
        }
    }
}
```