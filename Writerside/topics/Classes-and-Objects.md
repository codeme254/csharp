# Classes and Objects

Everything that you can 'see' and 'touch' in the world is an object and there is a class for it.

Classes come from classification. If you take anything in the world you can say that this belongs to so-and-so class.

For example, BMW is a Car, Toyota is a Car, these are objects of class Car, so class is a definition and objects are
instances.

## Classes and Objects From Programming Languages Point of View
### Class
A class is simply a user-defined data type that represents both state and behavior.

The state represents the properties and behavior is the action that objects can perform.

In other words, we can say that a class is the blueprint/plan/template that describes the details of an object.

A class is a blueprint from which the individual objects are created.

### Object
It is an instance of a class. A class is brought to life by creating objects.

Members of a class can be accessed through an object.

To access the class members, we need to use the dot (.) operator. The dot operator links the name of an object with 
the name of a member of a class.

## How we Create a Class and Object in C#
A class definition starts with the keyword class followed by the class name and the class body is enclosed by a pair
of curly braces.

In order to use a class, we must create an object of that class using the new keyword. Once you create the object
then you can access the class members using the object.

```C#
namespace OOP
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // Creating an object (instance of the calculator class)
            Calculator c = new Calculator();
            // Accessing Calculator class member using an object
            Console.WriteLine(c.Sum(5, 6));
        }
    }

    // Defininig a class
    class Calculator
    {
        public int Sum(int a, int b)
        {
            return a + b;
        }
    }
}
```

## Types of Classes in C#
In C#, we have the following types of classes:
- Abstract Class
- Concrete Class
- Sealed Class
- Partial Class
- Static Class

We will discuss these classes in details later.