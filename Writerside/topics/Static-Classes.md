# Static Classes

Static classes are classes created using the **static** modifier.

A static class can contain only static members.

It is not possible to create an instance of a static class. This is because it contains only static members. And we 
know we can access the static members of a class by using the class name.

Note: We cannot inherit from a static class.

We can access the members of a static class directly by using the class name.

## Example of a static class
```C#
using System;

namespace StaticClasses
{
    static class Math
    {
        public static void Add(int num1, int num2)
        {
            Console.WriteLine(num1 + num2);
        }

        public static void Multiply(int num1, int num2)
        {
            Console.WriteLine(num1 * num2);
        }
    }
    internal class StaticClasses
    {
        static void Main(string[] args)
        {
            Math.Add(10, 2);
            Math.Multiply(10, 2);
        }
    }
}
```

## Difference Between Static Classes and Non-Static Classes
1. In C#, the static class is created by using the static keyword, the rest of the others are non-static classes.
2. We cannot create an instance of a static class even if it is a reference. On the other hand, we can create both
instance and reference variables using a non-static class.
3. We can access the members of a static class directly by using the class name. To access the non-static members, 
we need an instance or object of that class.
4. In static class, we can only define static members. On the other hand, inside a non-static class, we can define 
both static and non-static members.
5. A static class contains only a static constructor whereas a non-static class contains can both static and 
instance constructors.
6. Static classes are sealed and hence cannot inherit from another class. On the other hand, the non-static 
class can be inherited by another class.