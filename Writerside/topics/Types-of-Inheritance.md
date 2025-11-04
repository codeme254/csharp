# Types of Inheritance

Generally, there are 5 types of inheritance:
- Single inheritance
- Multi-level inheritance
- Hierarchical inheritance
- Hybrid inheritance
- Multiple inheritance

## Single Inheritance
When a class is inherited from a single base class then the inheritance is called single inheritance.

![Single inheritance](inheritance-single-inheritance.png)

### Example of Single Inheritance
```C#
using System;

namespace SingleInheritance
{
    class A
    {
        public void Method1()
        {
            Console.WriteLine("This is method 1");
        }
    }

    class B : A
    {
        public void Method2()
        {
            Console.WriteLine("This is method 2");
        }
    }
    internal class SingleInheritance
    {
        static void Main(string[] args)
        {
            B b = new B();
            b.Method1();
            b.Method2();
        }
    }
}
```

## Multilevel Inheritance
When a derived class is created from another derived class, then such a type of inheritance is called 
Multilevel Inheritance.

![Multilevel inheritance](inheritance-multilevel-inheritance.png)

### Example of Multilevel inheritance
```C#
using System;


namespace MultilevelInheritance
{
    class A
    {
        public void Method1()
        {
            Console.WriteLine("This is method 1");
        }
    }

    class B : A
    {
        public void Method2()
        {
            Console.WriteLine("This is method 2");
        }
    }

    class C : B
    {
        public void Method3()
        {
            Console.WriteLine("This is method 3");
        }
    }
    internal class MultilevelInheritance
    {
        static void Main(string[] args)
        {
            C c = new C();
            c.Method1();
            c.Method2();
            c.Method3();
        }
    }
}

```

## Hierarchical inheritance
When more than one derived class is created from a single base class, then it is called Hierarchical inheritance.

![Hierarchical inheritance](inheritance-hierarchical.png)

### Example of Hierarchical inheritance
```C#
using System;

namespace HierarchicalInheritance
{
    class A
    {
        public void Method1()
        {
            Console.WriteLine("This is the first method");
        }
    }

    class B : A
    {
        public void Method2()
        {
            Console.WriteLine("This is Method 2");
        }
    }

    class C : A
    {
        public void Method3()
        {
            Console.WriteLine("This is Method 3");
        }
    }

    class D : A
    {
        public void Method4()
        {
            Console.WriteLine("This is Method 4");
        }
    }
    internal class HierarchicalInheritance
    {
        static void Main(string[] args)
        {
            B b = new B();
            b.Method1();
            b.Method2();

            C c = new C();
            c.Method1();
            c.Method3();

            D d = new D();
            d.Method1();
            d.Method4();
        }
    }
}
```

## Multiple inheritance
When a derived class is created from more than one base class then such type of inheritance is called multiple 
inheritance.

![Multiple inheritance](inheritance-multiple-inheritance.png)

C# does not support multiple inheritance through classes.

We can achieve multiple inheritance in C# through interfaces; [Learn more about interfaces here](Interface.md).

A class can have one and only one immediate parent class, whereas the same class can have any number of interfaces
as its parent.

### Example of Multiple Inheritance
```C#
using System;

namespace MultipleInheritance
{
    interface IAnimal
    {
        void Eat();
    }

    interface IPet
    {
        void Play();
    }

    class Dog: IAnimal , IPet
    {
        public void Eat()
        {
            Console.WriteLine("Animal eating");
        }

        public void Play()
        {
            Console.WriteLine("Pet playing");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Dog d = new Dog();
            d.Eat();
            d.Play();
        }
    }
}
```

## Hybrid inheritance
Hybrid Inheritance is the inheritance that is the combination of any Single, Hierarchical, and Multilevel inheritances.

![Hybrid inheritance](inheritance-hybrid-inheritance.png)

There are two subclasses i.e. B and C which are inheriting from class A (this is Hierarchical inheritance). Then 
from B and C, there is one more class that is D inherits from B and C. Now, this is a combination of hierarchical 
inheritance from the top and multiple inheritances (D is inheriting from B and C) from the bottom. Further, from 
A to B and from B to C i.e. Multi-level Inheritance. So, if you have this type of inheritance then the features of 
base class A will be appearing in class D via class B and class C. This type of Inheritance is called Hybrid 
Inheritance.

C# does not support hybrid inheritance