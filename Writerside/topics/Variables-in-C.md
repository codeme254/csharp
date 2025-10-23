# Variables in C#

We execute programs to process information and data.

Whenever we are processing the data or information, the data or information must be at some location in out computer
and we call that location **memory location**.

Every computer has memory locations, and every memory location is identified by an address.

![Memory locations example](memory-locations.png)

If we want to store a value like 10 in a memory location, the value will be stored randomly at a particular memory
location.

![Memory locations](memory-locations-2.png)

Let's say we want to access our data, we will face problems in that the data is stored at a random memory location
which we cannot identify. So here, accessing the memory location becomes very difficult after storing the
information.

We need to set the identity of the memory location where our data is going to be stored.

This is where **variables** also known as **identifiers** come in.

We use variables to set the identity of memory location where our data is going to live for easier retrieval in our
program.

The syntax for creating a variable in C# is `data_type variableName;`  
For example: `int a;`  
Here int is the data type and the identifier can be any name and here we set it as `a`.

![Memory locations](memory-locations-3.png)

Here “a” is a named memory location to location 10344. Later we can store an element in that memory location
that is identified by the identifier “a” as follows:  
`a = 10;`

![Memory locations](memory-locations-4.png)

## What is a variable
A variable refers to a name given to a particular memory location.

The purpose of a variable is to provide a name to a memory location where we store some data.

We will then access the data by the variable name and the computer will access the data by the memory address.

## Rules for variable declaration in C#
1. A variable name must begin with a letter or underscore and nothing else.
2. Variables in C# are case sensitive
3. They can be constructed with digits and letters and the underscore symbol.
4. No special symbols are allowed other than underscores.

The syntax for declaring a variable is `data_type variable_name;`

## Types of variables in C#
There are 4 types of variables in C# and they are:
1. Non-static/Instance variables
2. Static variables
3. Constant variables
4. Readonly variables

## Static vs Non-Static Variables in C#
If we declare a variable explicitly by using the `static` keyword, we call that type of variable a **static variable**,
all the rest **non-static variables**.

If we declare a variable inside a `static` block, then that variable becomes a static variable even if we don't use
the **static keyword**.

```C#
namespace Variables
{
    internal class Variables
    {
        static int x = 100;
        int y = 200;
        static void Main()
        {
            int z = 300;
        }
    }
}
```
In the example above:
- Variable x is a static variable as it is declared using the `static` keyword.
- Variable y is non-static by default.
- Variable z is static as it is declared inside a static block (as the main method is static, so the variables declared
inside the main method are going to be static as well).

Let's try to print the value of x inside the main method:

```C#
namespace Variables
{
    internal class Variables
    {
        static int x = 100;
        int y = 200;
        static void Main()
        {
            int z = 300;
            Console.WriteLine($"The value of x is: {x}");
        }
    }
}
```
This works perfect.

Let's also try to print the value of y inside the main method:

```C#
namespace Variables
{
    internal class Variables
    {
        static int x = 100;
        int y = 200;
        static void Main()
        {
            int z = 300;
            Console.WriteLine($"The value of y is: {y}");
        }
    }
}
```

If we try to print the value of y inside the main method, we get an error saying: `an object reference is required for
non-static field, method, or property 'Variables.y'`


The reason for this is the memory for the variable y is going to be created only when we create an instance of the 
class `Variables` and for each instance.

Unless we create an instance of the `Variables` class, the memory will not be allocated for the variable y, and as long
as the memory is not allocated for variable y, then we cannot access it.

In the example below, we are creating an instance of the `Variables` class and using this instance, we are able to 
access the variable y.

```C#
namespace Variables
{
    internal class Variables
    {
        static int x = 100;
        int y = 200;
        static void Main()
        {
            int z = 300;
            Variables obj = new Variables();
            Console.WriteLine($"The value of y is: {obj.y}");
        }
    }
}
```

<note>
Non-static variables require an instance to be used but static variables don't require an instance of the class.
</note>

The point we start the execution of a class to the point we end the execution of a class is called a 
Life Cycle of a class. In the life cycle of a class, static variables are initialized once and only one time 
whereas non-static or instance variables are initialized 0 times if no instance is created and n times if 
n instances are created.

### Differences between Static and Non-Static Variables in C#
1. In the case of a non-static variable, each object will have its own copy whereas We can only have one copy of 
a static variable irrespective of how many objects we create.
2. Changes made to a non-static variable using one object will not be reflected in other objects as each object has 
its own copy of the non-static variable. In the case of static variables, changes made in one object will be reflected 
in other objects as static variables are common to all objects of a class.
3. We can access non-static variables through object references whereas the Static Variables can be accessed
directly by using the class name in C#.
4. In the life cycle of a class, a static variable is initialized only once, whereas non-static variables are 
initialized for 0 times if no instance is created and n times if n number of instances are created.

## Constant Variables in C#
In C#, if we declare a variable by using the const keyword, then it is a constant variable and the value of the 
constant variable can’t be modified once after its declaration.

It is mandatory to initialize the constant variable at the time of its declaration.

Below is how we declare a constant variable in C#:
```C#
namespace Variables
{
    internal class Variables
    {
        static void Main()
        {
            const float PI = 3.142F;
            Console.WriteLine(PI);
        }
    }
}
```

The behavior of a constant variable is similar to the behavior of static variables i.e. initialized once and only 
one time in the life cycle of the class and does not require an instance of a class either for initialization
or execution.

```C#
namespace Variables
{
    internal class Variables
    {
        const float PI = 3.142f;
        static void Main()
        {
            Console.WriteLine(PI);
        }
    }
}
```

The only difference between a static and constant variable is that the static variables can be modified whereas 
the constant variables in C# can’t be modified once declared.

## Read-only variables
When we declare a variable by using the `readonly` keyword, then it is known as a read-only variable and 
these variables can’t be modified like constants but after initialization.

This means that it is not mandatory to initialize a read-only variable at the time of its declaration but once we
initialize them, we cannot change them.

The behavior of read-only variables will be similar to the behavior of non-static variables in C#, i.e. initialized 
only after creating the instance of the class and once for each instance of the class is created. That means we can 
consider it as a non-static variable and to access readonly variables we need an instance.

```C#
namespace Variables
{
    internal class Variables
    {
        readonly float PI = 3.142f;

        static void Main()
        {
            Variables v = new Variables();
            Console.WriteLine(v.PI);
        }
    }
}
```

The only difference between a non-static and readonly variable is that after initialization, you can modify the 
non-static variable value but you cannot modify the readonly variable value.

The difference between a constant and readonly variable in C# is that a constant is a fixed value for the whole
class whereas readonly is a fixed value specific to an instance of a class and for each instance.