# Const and Read-Only in C#

The Constants variables are the immutable values that are known at the time of program compilation and do not 
change their values for the lifetime of the program.

The Read-only variables are also immutable values but these values are known at runtime and also do not change their 
values for the life of the program.

## Constant variables in C#
In C#, if we declare a variable by using the const keyword, then it is a constant variable and the value of the
constant variable can’t be modified once after its declaration.

This means that it is mandatory to initialize the value of a constant variable at the time of declaration.

Syntax: `const float PI = 3.14f;`

<note>
The behavior of constant variable is similar to the behavior of static variables i.e. initialized once and only 
one time in the life cycle of a class and <strong>does not require an instance of a class either for initialization
or execution.</strong>
</note>

Let us understand the Const variable in C# with an example. Please have a look at the following example. As you 
can see in the below code, we declare a const variable i.e. `const float PI = 3.14f;` and within the Main method, 
we access the const variable by using the class name and can access it directly also.

This is because const are static by default and as static it does not require an object instead it can be accessed by 
using the class name or directly within the same class.

It is also possible to declare local variables as const i.e. we can declare const variable within a method also. In
our example, within the Main method, we declare a const variable i.e. `const int number = 25;`. In this case, there is
no need to use the class name to access the variable.

```C#
namespace ConstAndReadonly
{
    internal class Program
    {
        const float PI = 3.14f;
        static void Main(string[] args)
        {
            Console.WriteLine($"The value of PI is {Program.PI}");

            const int number = 25;
            Console.WriteLine(number);
        }
    }
}
```

### Key points to remember when working with const variables in C#
1. The keyword const is used to create a “constant” variable. It means it will create a variable whose value is 
never going to be changed. In simple words, we can say that the variable whose value cannot be changed or
modified once after its declaration is known as a constant variable.
2. Constants are static by default.
3. It is mandatory to initialize a constant variable at the time of its declaration.
4. The behavior of a constant variable is the same as the behavior of a static variable i.e. maintains only one 
copy in the life cycle of the class and initializes immediately once the execution of the class start
(object not required)
5. The only difference between a static and constant variable is that the static variables can be modified whereas 
the constant variables in C# can’t be modified once it is declared.

## Read-Only Variables in C#
When we declare a variable by using the `readonly` keyword, then it is known as a read-only variable and these 
variables can’t be modified like constants but after initialization.

That means it is not mandatory to initialize a read-only variable at the time of its declaration but once initialized,
they cannot be changed.

The behavior of read-only variables will be similar to the behavior of non-static variables in C#, i.e. initialized 
only after creating the instance of the class and once for each instance of the class is created.

In C#, a readonly value can be assigned a value only in two places:
- At the point of declaration.
- Inside a constructor.

We will learn more about constructors later, but for now look at the example below to understand this:

```C#
namespace ConstAndReadonly
{
    internal class Program
    {
        // Initializing a readonly variable at the place of creation
        readonly int number = 99;
        readonly int age;

        public Program() 
        {
            // Initializing a readonly variable inside of a constructor
            age = 55;
        }
        static void Main(string[] args)
        {
            // you need an instance of the class to work with a readonly variable.
            Program p = new Program();
            Console.WriteLine($"Number is {p.number}");
            Console.WriteLine($"Age is {p.age}");
        }
    }
}
```

### Points to remember when working with Read-Only Variables in C#
1. The variable which is created by using the readonly keyword is known as a read-only variable in C#. The read-only 
variable’s value cannot be modified once after its initialization.
2. It is not mandatory or required to initialize the read-only variable at the time of its declaration like a 
constant. You can initialize the read-only variables under a constructor but the most important point is that 
after initialization, you cannot modify the value of the readonly variable outside the constructor.