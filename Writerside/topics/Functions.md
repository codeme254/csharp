# Functions

A function is a group of related instructions that performs a specific task.

Functions take some input as parameters and return the result as a return value.

If we write a function, then we can reuse the function multiple times in the program. That means functions allow us
to reuse the code without retyping the code.

## Types of functions in C#
There are two types of functions and they are as follows:
- Built-in functions
- User-defined functions

The function that is already defined in the framework and available to be used by developers is called a **built in**
function whereas if the function is defined by the developer it is called a user-defined function.

## Built-in functions
In the below example, we are using the built-in WriteLIne function to print the output on the console window and
the built-in Sqrt function to get the square root of a given number.

```C#
namespace Functions
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int number = 25;
            double squareRoot = Math.Sqrt(number);
            Console.WriteLine($"Square root of {number} is {squareRoot}");
        }
    }
}
```

Whenever the built-in functions don't support our requirements, we write our own functions.

## User-defined functions
These are functions that we create ourselves.

The function whose body is implemented by the developer or user is called a user-defined function.

As programmers, we have full control of these functions.

### How to create a function
First of all, the function should have a **name** that is **mandatory**. 

Then it should have a **parameter list** (the parameters it is taking) which is **optional**. 

Then the function should have a **return type** which is **mandatory**. 

A function can have an **access specifier**, which is **optional**.

A function can have a **modifier** which is also **optional**.

![function](function-structure.png)

- **Function name**:  It is mandatory, and it defines the name of the method or function. The rules for giving 
function names are the same as the rules for giving variable names.
- **Parameter list**: It is Optional and defines the list of parameters. A function that can take 0 or more parameters.
- **Return type**: It is Mandatory and defines the method’s return type value. A function may or may not return a 
value, but it can return at most one value. It cannot return multiple values but can take multiple values as 
parameters. If the function is not returning any value, then the return type should be **void**.
- **Access specifier**: It is Optional and defines the method’s scope. That means it defines the accessibility of 
the method, such as private, protected, public, etc.
- **Modifier**: It is optional and defines the method’s access type. For example, static, virtual, partial, sealed, etc.
If you declare the method with a static modifier, then you can access the method directly without creating an 
instance. If you declare the method with the sealed modifier, then this method is not going to be overridden under 
a child class. And if you declare the method with the partial modifier, then you can split the method definition 
into two parts (more on this later).
- **Function body**: The function’s body defines the code or list of statements you need to execute the function 
call. It is enclosed within curly braces.

### What is a function signature?
In C#, a function signature is made up of two parts, the **function name** and the **parameter list**.

In C#, the return type is not considered to be part of the method signature.

![function signature](function-signature.png)

```C#
namespace Functions
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int x = 10, y = 20;
            int sum = Add(x, y);
            int product = Product(x, y);
            Console.WriteLine($"Sum of {x} and {y} is {sum}");
            Console.WriteLine($"Product of {x} and {y} is {product}");
        }

        static int Add(int x, int y)
        {
            return x + y;
        }

        static int Product(int x, int y)
        {
            return x * y;
        }
    }
}
```

### What are parameters of a function
For a better understanding, have a look at the image below:

![Parameters](function-parameters.png)

As you can see in the above image, we are passing two values, x, and y, to the Add function, which takes two 
parameters (a and b). The parameters (x and y) that we are passing to the Add function are called Actual Parameters. 
The parameters (a and b) which are taken by the Add method are called Formal Parameters. When we call the Add method,
the values of actual parameters are copied to the formal parameters. So, the x value, i.e., 10, is copied to a, and 
the y value, i.e., 15, is copied to b.

## Function/Method Overloading
In C#, we can write more than one function with the same name, but with a different argument or parameter list,
and when we do so, it is called function overloading.

Consider the add function/method below:

```C#
namespace Functions
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Add(10, 10));
            Console.WriteLine(Add(10.5, 8));
            Console.WriteLine(Add(10, 10, 15));
            Console.WriteLine(Add(1.5, 2.7, 3.3));
        }

        static int Add(int x, int y)
        {
            return x + y;
        }

        static double Add(double x, double y)
        {
            return x + y;
        }

        static int Add(int x, int y, int z)
        {
            return x + y + z;
        }

        static double Add(double x, double y, double z)
        {
            return x + y + z;
        }
    }
}
```