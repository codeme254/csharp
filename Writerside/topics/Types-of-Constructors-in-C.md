# Types of Constructors in C#

There are 5 types of constructors available in C# and they are as follows:
- Default or parameter less constructor
- Parameterized constructor
- Copy constructor
- Static constructor
- Private constructor

Let's define each of these constructors with examples.

## Default or Parameterless Constructors
If a constructor method does not take any parameters, then we call that a Default or Parameter Less Constructor.

These constructors can be defined by a programmer explicitly or else will be defined implicitly provided there is 
no explicit constructor under the class.

Classified again into two:
- System-defined default constructor
- User-defined default constructor

### System Defined Default Constructor
If we don't define any constructor explicitly in our program, then by default the compiler will provide one constructor
at the time of compilation.

That constructor is called a default constructor and the default constructor is parameterless. The default constructor 
will assign default values to the data members (non-static variables).

As this constructor is created by the system this is also called a system-defined default constructor.

```C#
namespace Constructors
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Test t = new Test();
            // Default values assigned by default constructor
            Console.WriteLine($"i = {t.i}");
            Console.WriteLine($"j = {t.j}");
            Console.WriteLine($"k = {t.k}");
        }
    }

    class Test
    {
        public int i;
        public bool j;
        public string k;
    }
}
```

When you run the above code, you will see that default values based on the variable type are being printed 
on the console. In our example, we have not specified these default values. Then who provided these default values and 
when? These default values are provided by the default constructor based on the variable data type and the compiler
will provide the default constructor at the time of compilation.

### User-Defined Default Constructor
The constructor which is defined by the user without any parameter is called the user-defined default constructor.

This constructor does not accept any argument but as part of the constructor body, you can write your own logic.

```C#
namespace UserDefinedConstructor
{
    class Employee
    {
        public int Id, Age;
        public string Address, Name;
        public bool IsPermanent;

        // User-Defined Default/Parameterless Constructor
        public Employee()
        {
            Id = 100;
            Age = 30;
            Address = "Nairobi";
            Name = "John";
            if (Age > 25)
            {
                IsPermanent = true;
            } else
            {
                IsPermanent = false;
            }
        }

        public void DisplayDetails()
        {
            Console.WriteLine($"Id: {Id}");
            Console.WriteLine($"Age: {Age}");
            Console.WriteLine($"Address: {Address}");
            Console.WriteLine($"Name: {Name}");
            Console.WriteLine($"IsPermanent: {IsPermanent}");
        }
    }
    internal class UserDefinedConstructor
    {
        static void Main( string[] args )
        {
            Employee employee = new Employee();
            employee.DisplayDetails();
        }
    }
}
```

The drawback of default/parameterless constructor  is that each and every instance (i.e. object) of the class will be 
initialized (assigned) with the same set of values. That means it is not possible to initialize each instance of 
the class with different values.

## Parameterized Constructor

If a constructor method is defined with parameters, we call it a Parameterized Constructor in C#, and these 
constructors are defined by the programmers only.

If we want to initialize the objects dynamically with the user-given values or if we want to initialize each instance 
of a class with a different set of values then we need to use the Parameterized Constructor in C#.

```C#
namespace ParameterizedConstructor
{
    internal class ParameterizedConstructor
    {
        static void Main(string[] args)
        {
            Employee e1 = new Employee("John", "Doe", 24);
            e1.Display();

            Employee e2 = new Employee("Jack", "Smith", 38);
            e2.Display();

            Employee e3 = new Employee("Alison", "Krugger", 20);
            e3.Display();
        }
    }
    class Employee
    {
        string FirstName, LastName;
        int Age;
        // Parameterized constructor
        public Employee(string F_Name, string L_Name, int A_Age) 
        {
            FirstName = F_Name;
            LastName = L_Name;
            Age = A_Age;
        }

        public void Display()
        {
            Console.WriteLine($"FirstName: {FirstName}");
            Console.WriteLine($"LastName: {LastName}");
            Console.WriteLine($"Age: {Age}");
        }
    }
}
```

## Copy Constructor
If we want to create multiple instances with the same values then we need to use the copy constructor in C#, in 
a copy constructor the constructor takes the same class as a parameter to it.

**Before using copy constructors, it is important to know that constructors can be overloaded, i.e, we can have
multiple constructors in a class. However, each of these constructors must have a different signature. A different 
signature means the number, type, and parameter order should be different.**

Consider the example below to understand copy constructors:

```C#
namespace CopyConstructor
{
    internal class CopyConstructor
    {
        static void Main(string[] args)
        {
            TestClass t1 = new TestClass(10, 20, 30, 40);
            t1.Display();
        }
    }

    class TestClass
    {
        int I, J, K, L;
        public TestClass(int i, int j, int k, int l)
        {
            I = i;
            J = j;
            K = k;
            L = l;
        }

        public void Display()
        {
            Console.WriteLine($"I = {I}");
            Console.WriteLine($"J = {J}");
            Console.WriteLine($"K = {K}");
            Console.WriteLine($"L = {L}");
        }
    }
}
```

In the above example, if we wanted three identical copies of object t1, we could create the three new objects and use
the values manually but this process would be tedious and error prone especially when have a lot of parameters needed.

The solution to this is a copy constructor as shown:

```C#
namespace CopyConstructor
{
    internal class CopyConstructor
    {
        static void Main(string[] args)
        {
            TestClass t1 = new TestClass(10, 20, 30, 40);
            t1.Display();
            TestClass t2 = new TestClass(t1);
            t2.Display();
            TestClass t3 = new TestClass(t1);
            t3.Display();
            TestClass t4 = new TestClass(t1);
            t4.Display();
        }
    }

    class TestClass
    {
        int I, J, K, L;
        public TestClass(int i, int j, int k, int l)
        {
            I = i;
            J = j;
            K = k;
            L = l;
        }

        public TestClass(TestClass t) 
        {
            I = t.I; 
            J = t.J;
            K = t.K;
            L = t.L;
        }

        public void Display()
        {
            Console.WriteLine($"I = {I}");
            Console.WriteLine($"J = {J}");
            Console.WriteLine($"K = {K}");
            Console.WriteLine($"L = {L}");
        }
    }
}
```

## Static Constructor
In C#, it is also possible to create a constructor as static and when we do so, it is called a Static Constructor.

If a constructor is declared explicitly by using the static modifier, then it is called a static constructor.

Static constructors are responsible for initializing static variables.

The following are some key points to understand about static constructors:

### Point 1
When a class has static variables, C# automatically provides a static constructor if you don’t write one.

### Point 2
Static Constructors are responsible for initializing static variables and these constructors are never called 
explicitly. They are called Implicitly and moreover, these constructors are the first to execute in any class.

When we run the following code, the static constructor is executed despite the fact that we didn't call it:

```C#
namespace StaticConstructor
{
    internal class StaticConstructor
    {
        static StaticConstructor()
        {
            Console.WriteLine("Static Constructor Executed");
        }

        static void Main()
        {
            Console.WriteLine("Main method executed");
        }
    }
}
```
![Output](constructors-static-constructor-output.png)

The non-static constructors are never called implicitly, they are always called explicitly whereas the static 
constructor never called explicitly, they are always going to be called implicitly.

### Point 3
Static Constructors cannot be parameterized, so overloading of the static constructors is not possible in C#.

The static constructors are executed implicitly and hence we never get a chance to pass a value.


### Static Constructor Summary
1. There can be only one static constructor in a class.
2. It can’t be called explicitly, it is always called implicitly.
3. The static constructor should be without any parameters.
4. It can only access the static members of the class.
5. There should not be any access specifiers in the static constructor definition.
6. If a class is static then we cannot create the object for the static class.
7. It is called automatically to initialize the static members.
8. Static constructor will be invoked only once
<note>
We cannot initialize non-static members inside a static constructor.

We can initialize static members inside a non-static constructor.
</note>

## Private Constructor
The constructor whose accessibility is private is known as a private constructor.

When a class contains a private constructor then we cannot create an object for the class outside of the class. So, 
private constructors are used to create an object for the class within the same class.

```C#
namespace PrivateConstructor
{
    internal class PrivateConstructor
    {
        private PrivateConstructor()
        {
            Console.WriteLine("Private Constructor");
        }

        static void Main(string[] args)
        {
           PrivateConstructor p = new PrivateConstructor();
        }
    }
}
```