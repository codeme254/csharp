# Generics

Generic means not specific to a particular data type, that type will be decided by the compiler at the time 
of compilation.

Generic is a concept that allows us to define classes and methods with placeholder types.

C# Compiler replaces these placeholders with the specified type at compile time. The concept of generics 
is used to create general-purpose classes and methods.

Let us understand the need for Generics in C# with one example. Let us create a simple program to check whether 
two integer numbers are equal or not. The following code implementation is very straightforward. Here we created 
two classes with the name **ClsCalculator** and **ClsMain**. Within the **ClsCalculator** class, we 
have **AreEqual()** method which takes two integer values as the input parameter, and then it checks whether 
the two input values are equal or not. If both are equal then it returns true else it will return false. 
And from the ClsMain class, we are calling the static **AreEqual()** method and showing the output 
based on the return value.

```C#
using System;

namespace Generics
{
    internal class ClsMain
    {
        static void Main(string[] args)
        {
            bool IsEqual = ClsCalculator.AreEqual(10, 20);
            if (IsEqual)
            {
                Console.WriteLine("Both are equal");
            }
            else
            {
                Console.WriteLine("Both are not equal");
            }
        }
    }

    class ClsCalculator
    {
        public static bool AreEqual(int value1, int value2)
        {
            return value1 == value2;
        }
    }
}
```

The above **AreEqual()** method works as expected as it is and more importantly it will only work with the integer
values as this is our initial requirement. 

Suppose our requirement changes, now we also need to check whether two string values are equal or not.

In the above example, if we try to pass values other than the integer values, then we will get a compile-time error. 
This is because the **AreEqual()** method of the **ClsCalculator** class is tightly bounded with the integer 
data type and hence it is not possible to invoke the **AreEqual** method other than with integer data type values. 
So, when we try to invoke the **AreEqual()** method by passing string or any other data type, we get a compile-time
error.

## Solving the Problem Above With Generics
We can solve the above problem with Generics in C#. 

With generics, we will make the **AreEqual()** method to work with different types of data.

```C#
using System;

namespace Generics
{
    internal class ClsMain
    {
        static void Main(string[] args)
        {
            Console.WriteLine(ClsCalculator.AreEqual<int>(10, 20));
            Console.WriteLine(ClsCalculator.AreEqual<string>("Hello", "Hello"));
            Console.WriteLine(ClsCalculator.AreEqual<bool>(true, false));
            Console.WriteLine(ClsCalculator.AreEqual<byte>(99, 25));
            Console.WriteLine(ClsCalculator.AreEqual<float>(19.9f, 19.9f));
            Console.WriteLine(ClsCalculator.AreEqual<double>(8.5, 8.5));
        }
    }

    class ClsCalculator
    {
        public static bool AreEqual<T>(T value1, T value2)
        {
            return value1.Equals(value2);
        }
    }
}
```

Here in the above example, in order to make the **AreEqual()** method generic (generic means the same method will 
work with the different data types), we specified the type parameter T using the angular brackets `<T>`. Then 
we use that type as the data type for the method parameters.