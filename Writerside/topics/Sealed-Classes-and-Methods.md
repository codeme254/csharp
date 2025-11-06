# Sealed Classes and Methods

A sealed class is a class that cannot be inherited from by other classes.

To make any class a sealed class, we use the **sealed** keyword.

![Sealed classes](sealed-classes.png)

Always keep the following points in mind when working with sealed classes:
- A sealed class is completely the opposite of an abstract class.
- The sealed class cannot contain any abstract methods.
- It should be the bottom-most class within the inheritance hierarchy.
- A sealed class can never be used as a base class.
- The sealed class is specially used to avoid further inheritance.
- The keyword sealed can be used with classes, instance methods, and properties.
- **Even if a sealed class cannot be inherited, we can still consume the class members from any 
other class by creating the object of the class.**

## Example of a Sealed Class

The `Manager` class in the example below is a sealed class since we have used the **sealed** modifier on it.

We cannot inherit from this class but we can create instances of this class.

```C#
using System;

namespace SealedClasses
{
    partial class Employee
    {
        public string FirstName { get; set; }
        public string LastName { get; set; }
        public int Salary { get; set; }

        public virtual void DisplayEmployeeDetails()
        {
            Console.WriteLine($"First name: {FirstName}");
            Console.WriteLine($"Last name: {LastName}");
            Console.WriteLine($"Salary: {Salary}");
        }
    }

    sealed class Manager : Employee
    {
        public int Bonus { get; set; }
        public override void DisplayEmployeeDetails()
        {
            base.DisplayEmployeeDetails();
            Console.WriteLine($"Bonus: {Bonus}");
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Manager m = new Manager()
            {
                FirstName = "John",
                LastName = "Doe",
                Salary = 200000,
                Bonus = 60000
            };
            m.DisplayEmployeeDetails();
        }
    }
}
```

## Sealed Methods
A sealed method is a method defined in the parent class but cannot be overridden in the child class.

By default, all methods in C# are **sealed** because overriding methods in C# is not possible unless the method is
declared as virtual in the parent class.

```C#
using System;

namespace SealedMethods
{
    class Parent
    {
        public virtual void Show()
        {
            Console.WriteLine("Show method in the parent class");
        }
    }

    class Child : Parent
    {
        // This method cannot be overriden any further
        // because we are marking it as sealed
        public override sealed void Show()
        {
            Console.WriteLine("Show method in the child class");
        }
    }

    class GrandChild : Child
    {
        // This will give us an error
        public override void Show()
        {
            Console.WriteLine("Show method in grandchild");
        }
    }
}
```