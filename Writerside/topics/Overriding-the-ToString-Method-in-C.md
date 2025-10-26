# Overriding the ToString Method in C#

To understand the `ToString` method in C#, let's start by understanding the Object class in C#.

## Understanding the Object Class in C#
The Object class is the Superclass of all dot net types.

That means, all the types in .NET Framework are inherited directly or indirectly from the Object class.

Because of this inheritance, every type in .NET inherits the ToString() method from the Object class.

If you go to the definition of Object class, then you will see that the ToString() method is defined as a 
Virtual Method which allows this method to be overridden in the child classes (more on this later).

![The object class](object-class.png)

Each and every class type (Reference Types) or struct type (Value Types) are directly or indirectly implicitly 
inherited from the Object class in C#.

Therefore, every object in C# gets the ToString method, which returns a string representation of that object.

**The `ToString()` method returns a string that represents the current object.**

For example, all variables of type int or float have the ToString method, which enables them to return their
contents as a string.

In the following example, the Number is an integer type variable and when we invoke the `ToString()` method on the
number object, it gives us the string representation of the integer 100:

```C#
namespace ToString
{
    internal class ToString
    {
        static void Main(string[] args)
        {
            int Number = 100;
            Console.WriteLine(Number.ToString());
        }
    }
}
```

When you create a custom class or struct in C#, then you can override the ToString method in order to provide 
information about your type to the client.

For example, if you have a complex type let’s say Employee class as shown in the below example and when you call the 
`ToString()` method on the Employee object, then you will not get the output as expected. Hence, we need to 
override the ToString() method, which is inherited from the Object class.

```C#
namespace ObjectClassMethods
{
    public class Employee
    {
        public string FirstName { get; set; }
        public string LastName { get; set; }
    }
    internal class ToString
    {
        static void Main(string[] args)
        {
            int Number = 100;
            Console.WriteLine(Number.ToString());

            Employee e = new Employee();
            e.FirstName = "John";
            e.LastName = "Doe";
            Console.WriteLine(e.ToString());
        }
    }
}
```
The output for the above program will be `ObjectClassMethods.Employee`.

Our requirement is when we call the ToString() method it should display the First Name and Last Name of the 
Employee object.

To achieve this we need to override the ToString() Virtual method which is provided by the Object class in C#.

## Overriding the `ToString()` method in C#
We can override the `ToString()` method using the `override` keyword as shown below.

```C#
namespace ObjectClassMethods
{
    public class Employee
    {
        public string FirstName { get; set; }
        public string LastName { get; set; }

        public override string ToString()
        {
            return $"Employee({FirstName} {LastName})";
        }
    }
    internal class ToString
    {
        static void Main(string[] args)
        {
            int Number = 100;
            Console.WriteLine(Number.ToString());

            Employee e = new Employee();
            e.FirstName = "John";
            e.LastName = "Doe";
            Console.WriteLine(e.ToString());
        }
    }
}
```

And now, when we run the program, we get `Employee(John Doe)` instead of the ugly and weird 
`ObjectClassMethods.Employee`.