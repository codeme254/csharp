# Generic Constraints

Generic constraints are used to restrict the types that can be substituted for type parameters.

It will give you a compile-time error if you try to substitute a generic type using a type that is not 
allowed by the specified constraints.

## Why We Need Generic Constraints
Let us first understand why we need constraints, and then we will see the different types of generic constraints 
in C# with examples. 

As we already discussed generics are used to define a class or structure or method with placeholders 
(type parameters) to indicate that they can use any of the types.

```C#
using System;
namespace GenericsConstraints
{
    public class GenericClass<T>
    {
        public T Message;
        public void GenericMethod(T Param1, T Param2)
        {
            Console.WriteLine($"Message: {Message}");
            Console.WriteLine($"Param1: {Param1}");
            Console.WriteLine($"Param2: {Param2}");
        }
    }
}
```

As you can see in the above code, here we have created a class i.e. GenericClass with one variable i.e. Message 
and one method i.e. GenericMethod using type parameter T and we have defined this type parameter with the 
class name using the angle (<>) brackets.

If you want to restrict a generic class to accept only a particular type of placeholder, then we need to use 
the Generic Constraints. So, by using Generic Constraints in C#, we can specify what type of placeholder the 
generic class can accept. If we try to instantiate a generic class with the placeholder type, that is not 
allowed by a constraint, then the compiler will throw a compile-time error. For example, if we specify the 
generic type to accept on class type, then later if we try to send int, bool, or any value type, then we will 
get a compile-time error.

Syntax: `GenericTypeName<T> where T : contraint1, constraint2`

## Types of Generic Constraints
In C#, generic constraints are specified by using the **where** keyword.

The following are the list of different type of generic constraints available in C#.

1. **where T: struct** => T must be a value type. No classes, no strings, no nullables.
2. **where T: class** => T must be a reference type; classes, interface, delegates or arrays. If it needs new to be
created or behaves like an object, it fits.
3. **where T: new()** => T must have a public empty constructor. This excludes; abstract classes, classes without a
default constructor, classes with only private constructors.
4. **where T: <base class name>** => T must be the specified class or a subclass of the specified class.
5. **where T: <interface name>** => T must be the specified interface or implement the specified interface.
6. **where T: U** => The type T must be the same type as U or a subtype of U.

## `where T: class` Generic Constraint in C#
The type argument must be a reference type. We know a class is a reference type in C#. So **where T: class**
is a reference type constraint.

That means this constraint can be applied to any class (non-nullable), interface, delegate, or array type in C#.

Consider the example below:

```C#
using System;

namespace WhereTClass
{
    class GenericClass<T> where T : class
    {
        public T Message;
        public void GenericMethod(T Param1,  T Param2)
        {
            Console.WriteLine($"Message: {Message}");
            Console.WriteLine($"Param1: {Param1}");
            Console.WriteLine($"Param2: {Param2}");
        }
    }
}
```

GenericClass will only accept reference-type arguments.

`GenericClass<string> stringClass = new GenericClass<string>();` - will work because string is a reference type.

`GenericClass<int> intClass = new GenericClass<int>();` - will not work because `int` is not a reference type.

```C#
using System;

namespace WhereTClass
{
    class GenericClass<T> where T : class
    {
        public T Message;
        public void GenericMethod(T Param1,  T Param2)
        {
            Console.WriteLine($"Message: {Message}");
            Console.WriteLine($"Param1: {Param1}");
            Console.WriteLine($"Param2: {Param2}");
        }
    }

    class Employee
    {
        public string Name {  get; set; }
        public string Location { get; set; }
    }

    class Program
    {
        static void Main(string[] args)
        {
            GenericClass<Employee> emp = new GenericClass<Employee>(); // works fine
            //GenericClass<int> gc = new GenericClass<int>(); // Error 
        }
    }
}
```

## `where T: struct` Generic Constraint in C#
If you want the type argument to accept only the value type then you need to use `where T: struct` constraints in C#.

In this case, the type argument must be non-nullable value types such as int, double, char, bool, float, etc.

```C#
using System;

namespace WhereTClass
{
    class GenericClass<T> where T : struct
    {
        public T Message;
        public void GenericMethod(T Param1,  T Param2)
        {
            Console.WriteLine($"Message: {Message}");
            Console.WriteLine($"Param1: {Param1}");
            Console.WriteLine($"Param2: {Param2}");
        }
    }
}
```

GenericClass will only accept value-type arguments.

`GenericClass<int> intClass = new GenericClass<int>();` - will work since int is a value type.

`GenericClass<string> stringClass = new GenericClass<string>();` - will not work since string is a reference type.

```C#
using System;

namespace WhereTStruct
{
    class GenericClass<T> where T : struct
    {
        public T Message;
        public void GenericMethod(T Param1, T Param2)
        {
            Console.WriteLine($"Message: {Message}");
            Console.WriteLine($"Param1: {Param1}");
            Console.WriteLine($"Param2: {Param2}");
        }
    }

    class Employee
    {
        public string Name { get; set; }
        public string Location { get; set; }
    }

    class Program
    {
        static void Main(string[] args)
        {
            //GenericClass<Employee> emp = new GenericClass<Employee>(); // Error
            GenericClass<int> gc = new GenericClass<int>(); // works fine
        }
    }
}
```

## `where T: new()` Generic Constraint in C#
Here, the type argument must be a reference type that has a public parameterless (default) constructor.

That means with the help of the new() constraint, we can only specify types which has a parameterless constructor.

```C#
using System;

namespace WhereTnew
{
    class GenericClass<T> where T : new()
    {
        public T Message;
        public void GenericMethod(T Param1, T Param2)
        {
            Console.WriteLine($"Message: {Message}");
            Console.WriteLine($"Param1: {Param1}");
            Console.WriteLine($"Param2: {Param2}");
        }
    }

    class Employee
    {
        public string Name { get; set; }
        public string Location { get; set; }
    }

    class Customer
    {
        public string Name { get; set; }
        public string Location { get; set; }
        public Customer(string cName, string cLocation)
        {
            Name = cName;
            Location = cLocation;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Works fine because Employee has a public parameterless contructor
            // REM: if we don't specify a constructor, there's always a default
            // public parameterless constructor
            GenericClass<Employee> e = new GenericClass<Employee>();

            // Will not work because Customer has no public parameterless contructor
            //GenericClass<Customer> c = new GenericClass<Customer>();
        }
    }
}
```

As you can see in the above code, we have not defined any constructor explicitly in the Employee class, so the 
compiler will provide a parameter-less default constructor. On the other hand, in the Customer class, we have 
defined one parameterized constructor explicitly.

If we use the Employee class as T in GenericClass, it will work fine but the Customer class will not.

## `where T: BaseClass` Generic Constraint in C#
Here, the type of argument must be derived from the specified base class.

That means in the `<base class>` constraint, we can only specify types that are inherited from `<base class>`.

The following example shows the base class constraint that restricts the type argument to be a derived 
class of the specified class.

```C#
using System;

namespace WhereTBaseClass
{
    class GenericClass<T> where T : BaseEmployee
    {
        public T Message;
        public void GenericMethod(T Param1, T Param2)
        {
            Console.WriteLine($"Message: {Message}");
            Console.WriteLine($"Param1: {Param1}");
            Console.WriteLine($"Param2: {Param2}");
        }
    }

    class BaseEmployee { }

    class Employee : BaseEmployee
    {
        public string Name { get; set; }
        public string Location { get; set; }
    }

    class Customer
    {
        public string Name { get; set; }
        public string Location { get; set; }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Works fine
            GenericClass<Employee> e = new GenericClass<Employee>();

            // Error
            //GenericClass<Customer> c = new GenericClass<Customer>();
        }
    }
}
```

When we create an instance of GenericClass using the Employee type argument, it works fine because Employee 
is the derived class of the BaseEmployee class. But, when we try to create an instance with Customer type, we 
will get a compile-time error because Customer is not a derived class of the BaseEmployee class.

## `where T: Interface` Generic Constraint in C#

Here, the type argument must be or implement the specified interface. Also, multiple interface constraints 
can be specified.

That means in the <interface> constraint, we can only specify types that implement the <interface> or the <interface>
itself.

```C#
using System;

namespace WhereTInterface
{
    interface IEmployee { };
    class GenericClass<T> where T : IEmployee
    {
        public T Message;
        public void GenericMethod(T Param1, T Param2)
        {
            Console.WriteLine($"Message: {Message}");
            Console.WriteLine($"Param1: {Param1}");
            Console.WriteLine($"Param2: {Param2}");
        }
    }

    class Employee : IEmployee
    {
        public string Name { get; set; }
        public string Location { get; set; }
    }

    class Customer
    {
        public string Name { get; set; }
        public string Location { get; set; }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Works fine
            GenericClass<Employee> e = new GenericClass<Employee>();
            GenericClass<IEmployee> e2 = new GenericClass<IEmployee>();

            // Error
            //GenericClass<Customer> c = new GenericClass<Customer>();
        }
    }
}
```

When we create an instance of GenericClass using the Employee type argument, it works fine because the Employee
class implements the IEmployee interface. But, when we try to create an instance with Customer type, we will get
a compile-time error because the Customer class does not implement the IEmployee interface.

## Multiple Generic Constraints
In C# generics, it is also possible to apply multiple constraints on generic classes based on our requirements.

In the below example, we are creating the generic class with two constraints. The first constraint specifies
that the T parameter must be a reference type whereas the second constraint specifies that the X parameter 
must be a value type.

```C#
using System;
namespace GenericsDemo
{
    public class GenericClass<T, X> where T: class where X: struct
    {
        public T Message;
        public void GenericMethod(T Param1, X Param2)
        {
            Console.WriteLine($"Message: {Message}");
            Console.WriteLine($"Param1: {Param1}");
            Console.WriteLine($"Param2: {Param2}");
        }
    }
   
    class Program
    {
        static void Main()
        {
            GenericClass<string, int> multipleGenericConstraints = new GenericClass<string, int>();
            multipleGenericConstraints.Message = "Good Morning";
            multipleGenericConstraints.GenericMethod("Anurag", 100);
            Console.ReadKey();
        }
    }
}
```