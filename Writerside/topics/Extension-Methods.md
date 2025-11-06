# Extension Methods

Extension methods is a feature that allows us to add new methods into a class without editing the source code of the
class.

If a class consists of a set of members in it and in the future if you want to add new methods into the class,
you can add those methods without making any changes to the source code of the class.

Extension methods can be used as an approach to extending the functionality of a class in the future if the 
source code of the class is not available, or we don’t have any permission in making changes to the class.

Before extension methods, inheritance is an approach that is used for extending the functionality of a class i.e. 
if we want to add any new members to an existing class without making a modification to the class, we will define 
a child class to that existing class, and then we add new members in the child class.

In the case of an extension method, we will extend the functionality of an existing class. In this case, we will 
create a new class and by using that new class we will extend the functionality of an existing class.

Both these approaches can be used for extending the functionalities of an existing class whereas, in the case of 
inheritance, we call the methods defined in the old and new classes by using the object of the new class whereas, 
in the case of extension methods, we call the old and new methods by using the object of the old class.

## Things to keep in mind when working with C# extension methods
- Extension methods must be defined only under the static class.
- We already discussed that Static Class in C# contains only Static Members. As an extension method is defined 
under a static class, it means the extension method should be created as a static method.
- The first parameter of an extension method is known as the **binding parameter** which should be the name of the
class to which the method has to be bound and the binding parameter should be prefixed with the **this**.
- An extension method can have only one binding parameter and that should be defined in the first 
place on the parameter list.
- If required, an extension method can be defined with normal parameters also starting from the second place of 
the parameter list.

## Example to understand extension methods
Consider the example below:

```C#
using System;

namespace ExtensionMethods
{
    public class MyMath
    {
        public int Number1 { get; set; }
        public int Number2 { get; set; }

        public void Add()
        {
            int sum = Number1 + Number2;
            Console.WriteLine($"Sum of {Number1} and {Number2} is {sum}");
        }
    }
    internal class ExtensionMethods
    {
        static void Main( string[] args )
        {
            MyMath m = new MyMath()
            {
                Number1 = 15,
                Number2 = 3,
            };
            m.Add();
        }
    }
}
```

Assume we wanted to add three more methods, i.e `Multiply`, `Divide` and `Difference`, for some reason, let's assume
the source code is not available to us, or we don't have access to the source code to edit, this means we cannot change
`MyMath` class, how do we extend its functionality to include these three new methods?

We can do this with the help of extension methods as shown:

```C#
using System;

namespace ExtensionMethods
{
    public class MyMath
    {
        public int Number1 { get; set; }
        public int Number2 { get; set; }

        public void Add()
        {
            int sum = Number1 + Number2;
            Console.WriteLine($"Sum of {Number1} and {Number2} is {sum}");
        }
    }

    public static class NewMyMath
    {
        public static void Multiply(this MyMath m)
        {
            int product = m.Number1 * m.Number2;
            Console.WriteLine($"Product of {m.Number1} and {m.Number2} is {product}");
        }

        public static void Divide(this MyMath m)
        {
            int division = m.Number1 / m.Number2;
            Console.WriteLine($"Division between {m.Number1} and {m.Number2} is {division}");
        }

        public static void Difference(this MyMath m)
        {
            int difference = m.Number1 - m.Number2;
            Console.WriteLine($"Difference in {m.Number1} and {m.Number2} is {difference}");
        }
    }
    internal class ExtensionMethods
    {
        static void Main( string[] args )
        {
            MyMath m = new MyMath()
            {
                Number1 = 15,
                Number2 = 3,
            };
            m.Add();
            m.Multiply();
            m.Divide();
            m.Difference();
        }
    }
}
```

Notice how we are calling these new methods as if they belong to the original MyMath class.