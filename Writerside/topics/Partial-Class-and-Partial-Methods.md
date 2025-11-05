# Partial Class and Partial Methods

Partial class is a feature that allows us to define a class on multiple files, i.e we can split the content of the
class into different files.

A class in which code can be written in two or more files is known as a partial class.

To make any class partial we need to use the keyword **partial**.

## Example to understand partial classes and methods
File: `PartialEmployeeOne.cs`
```C#
namespace PartialClass
{
    public partial class PartialEmployee
    {
        public string FirstName { get; set; }
        public string LastName { get; set; }
        public string Gender { get; set; }
        public double Salary { get; set; }
    }
}
```

Here the file name is PartialEmployeeOne.cs but the class name is PartialEmployee and the class is marked with 
the partial keyword which makes it a partial class.

File: `PartialEmployeeTwo.cs`

```C#
using System;

namespace PartialClass
{
    public partial class PartialEmployee
    {
        public void DisplayFullName()
        {
            Console.WriteLine($"Full Name is {FirstName} {LastName}");
        }

        public void DisplayDetails()
        {
            Console.WriteLine("Employee Details:");
            Console.WriteLine($"First Name {FirstName}");
            Console.WriteLine($"Last Name {LastName}");
            Console.WriteLine($"Gender {Gender}");
            Console.WriteLine($"Salary {Salary}");
        }
    }
}
```

### Using the Partial Class
Now, we are going to use the Partial classes whose definition is split across two different class files.

Partial classes are used just like normal classes - nothing special.

```C#
namespace PartialClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            PartialEmployee employee = new PartialEmployee()
            {
                FirstName = "John",
                LastName = "Doe",
                Gender = "Male",
                Salary = 90000
            };
            employee.DisplayFullName();
            employee.DisplayDetails();
        }
    }
}
```

## Rules to follow when working with partial classes
### Rule 1
All the parts that contain the class definition must use the partial keyword.

All the parts must be available at compile time to form the final type. Otherwise, we will get a 
compilation error stating `Missing partial modifier. Another partial declaration of this type exists.`

![All the parts that contain the class definition must use the partial keyword.](partial-classes-rule-1.png)

### Rule 2
All the parts of the partial class must have the same access modifier.

If we try to use different access modifiers in different parts of the partial class, then we will get a compilation 
error saying that Partial declarations have conflicting accessibility modifiers.

Here, you can see that in the first definition of the PartialEmployee class we have used public access specifier, 
and in the second definition of the PartialEmployee class we have used internal access specifier and hence the 
compiler throws one compilation error.

![All the parts of the partial class must have the same access modifier.](partial-classes-rule-2.png)

### Rule 3
If any of the parts are declared as abstract, then the entire type is considered as abstract or if any of the 
parts are declared as sealed, then the entire type is considered as sealed or if any of the parts inherit a class, 
then the entire type inherits that class.

Here, you can see, one of the parts we declared as abstract, and hence the complete class becomes abstract and as
we know we cannot create an instance of an abstract class. And here when we are trying to create an instance of 
the PartialEmployee class which is an abstract class, the compiler throws one compilation error.

![Rule 3](partial-classes-rule-3.png)

### Rule 4
The different parts of the partial class must not specify different base classes. If we specify different bases 
class, then we will get a compilation error saying Partial declarations must not specify different base classes.

For a better understanding, please have a look at the below example code. Here, you can see that one part of the 
Partial Class inherits from the Employee base class and the other part of the Partial class inherits from the 
Customer base. That means now the Partial class has two base classes making this multiple inheritance with 
classes which is not possible in C# and hence the compiler throws one compilation error.

![Rule 4](partial-classes-rule-4.png)

### Rule 5
It is possible with Partial classes that the different parts of the partial class can specify different base 
interfaces and the final type should and must implement all the interface methods.

In the following example, the PartialClass needs to provide the implementation for both IEmployee and ICustomer 
interface methods. This is possible because a class can not have more than one base class, but a class can have 
more than one base interface and this is how we can implement multiple inheritances in C# with interfaces.

```C#
namespace PartialClassDemo
{
    public interface IEmployee
    {
        void EmployeeMethod();
    }
    public interface ICustomer
    {
        void CustomerMethod();
    }
    public partial class PartialClass : IEmployee
    {
        public void EmployeeMethod()
        {
            //Method Implementation
        }
    }
    public partial class PartialClass : ICustomer
    {
        public void CustomerMethod()
        {
            //Method Implementation
        }
    }
}
```

## Partial Methods
A partial class may contain a partial method. 

One part of the class contains the signature of the method. An implementation of the Partial Method can 
be defined in the same part or other parts of the Partial Class. 

If the implementation is not supplied, then the method and all calls to the partial method are removed
by the compiler at the time of compilation.

```C#
using System;
namespace PartialClassDemo
{
    partial class PartialClass
    {
        // Declaration of the partial method.
        partial void PartialMethod();

        // A public method calling the partial method
        public void PublicMethod()
        {
            Console.WriteLine("Public Method Invoked");
            PartialMethod();
        }
    }
}
```

As you can see in the above code, we have created the PartialMethod() using the partial keyword which makes it a 
partial method, and further notice this partial method does not have its body, it contains only the method signature.

The implementation of this Partial you can provide in this class definition or you can also provide the 
implementation in other parts of this partial class. But the most important point that you need to remember 
is that the implementation of a partial method is optional. If we don’t provide the implementation, then the
method and all calls to the partial method are simply removed by the compiler at the time of compilation.

The implementation of the Partial Methods as discussed can be provided in the same part or in other parts of 
the partial class.

In a different file:
```C#
using System;
namespace PartialClassDemo
{
    partial class PartialClass
    {
        // Partial method implemented
        partial void PartialMethod()
        {
            Console.WriteLine("Partial PartialMethod  Invoked");
        }
    }
}
```

## Rules to follow when working with partial methods
### Rule 1
Partial methods in C# are private by default, and we cannot use any access specifier explicitly, and 
if we try to use any access specifier explicitly like public, private, protected, etc, then we will get a 
compiler error stating `A partial method cannot have access modifiers or the virtual, abstract, override, 
new, sealed, or extern modifiers.`

For a better understanding, please have a look at the below example code. Here, we are explicitly trying to use a
private access modifier with the partial method, and hence the compiler throws an error.

![Rule 1](partial-methods-rule-1.png)


### Rule 2
Partial method declaration and implementation should not be at the same time.

Its declaration should be at one place and its implementation must be at a different place either in the same part
or in other parts of the partial class.

For a better understanding, please have a look at the below example code. Here, we are declaring and implementing 
the partial method at the same time and hence we are getting a compiler error.

![Rule 2](partial-methods-rule-2.png)

### Rule 3
A partial method return type must be void. If we try to use any other return type like int, string, bool, etc. 
then we will get a compiler error.

For a better understanding, please have a look at the below example code. Here, we are trying to make the return 
type as int and hence the compiler throws an error.

![Rule 3](partial-methods-rule-3.png)

### Rule 4
A partial method must and should be declared within a partial class or partial struct.

A non-partial class or struct cannot include partial methods.

For a better understanding, please have a look at the below code. Here, we are trying to define a partial method 
under a non-partial class and hence the compiler throws an error.

![Rule 4](partial-methods-rule-4.png)

### Rule 5
The signature of the partial method declaration must match the signature of the implementation else we will 
get a compilation error.

For a better understanding, please have a look at the following code. Here, in the first part of the partial class, 
we have defined the partial method with one integer parameter and in the second part of the partial class where we 
are providing the implementation, we are not including the integer parameter and hence the compiler throws an error.

![Rule 5](partial-methods-rule-5.png)

### Rule 6
A partial method can be implemented only once either in the same part or in other parts of the partial class. If we 
try to implement a partial method more than once, then we will get a compilation error.

For a better understanding, please have a look at the below example code. Here, in the first part, we have 
declared the partial method and in the second part and in the part we are providing implementation to the 
partial method, and as we are providing two implementations we are getting the compilation error. This is 
because, in a class, we cannot define two methods with the same name and same parameters i.e. method overriding 
is not possible in a single class.

![Rule 6](partial-methods-rule-6.png)