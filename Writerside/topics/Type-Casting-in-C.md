# Type Casting in C#

Type Casting or Type Conversion in C# is the process to change one data type value into another data type.

The Type Conversion is only possible if both the data types are compatible with each other else we will get compile
time error saying `cannot implicitly convert one type to another type.`

Type conversion can be done by the compiler or explicitly by the developer. In line with this, type conversion is
classified into two:
- Implicit type casting
- explicit type casting

## Implicit type casting
The Implicit Conversion or Implicit Type Casting in C# is automatically done by the compiler and in this case, 
there will be no data loss.

Here, the typecasting or type conversion is done from a smaller data type to a larger data type. This type of 
type conversion is safe.

In implicit Type Conversion, the compiler will automatically convert one type to another. Generally, in the case of 
implicit Type Conversion, the smaller data types like int (having less memory size) are automatically converted to 
larger data types like long (having larger memory size).

Implicit type casting happens when:
- The two data types are compatible.
- When we assign a value of a smaller data type to a bigger data type.

For example, in C#, the numeric data types like byte, short, int, long, double, float, decimal, etc. are compatible 
with each other but no automatic conversion is supported from numeric type to char type or Boolean type

Also, char and bool are not compatible with each other. So, before converting, the compiler will first check the 
type compatibility, and then it decides whether it is good to convert or throw some error.

The following diagram shows the implicit types of conversion that are supported by C#:

![Implicit type conversion](implicit-conversion.png)

### Example to understand implicit type casting

In the following example, we have created an integer variable with the name numInt i.e. `int numInt = 1500;`.

Notice the line, `double numDouble = numInt;` Here, we are assigning the int type variable value to a double 
type variable.

In this case, the compiler will automatically convert the int type value to double type. This is because both 
int and double are numeric types and hence the types are compatible. Furthermore, int takes 4-Bytes of memory
and double takes 8-Bytes of memory (use the `sizeof` operator to prove this), and hence there is no 
issue to store 4Bytes of data inside 8-Bytes of memory location.

```C#
using System;

namespace TypeCasting
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // Values before conversion
            Console.WriteLine($"numInt value {numInt}");
            Console.WriteLine($"numInt type {numInt.GetType()}");
            Console.WriteLine($"Int size: {sizeof(int)}");

            // Values after conversion
            Console.WriteLine($"numDouble value {numDouble}");
            Console.WriteLine($"numDouble type {numDouble.GetType()}");
            Console.WriteLine($"double size {sizeof(double)}");
        }
    }
}
```
Note: In implicit type conversion, the smaller types are converted to larger data types and hence, there is no 
loss of data during the conversion.

## Explicit type casting
If you want to convert the large data type to a small data type in C#, then you need to do the same explicitly 
using the cast operator.

Explicit Conversion or Explicit Type Casting in C# is done by using the Cast operator.

It includes the conversion of larger data types to smaller data types.

In the case of Explicit Conversion or Explicit Type Casting. there is a chance of data loss or the conversion 
might not be succeeded for some reason. This is an unsafe type of conversion.

### Example to understand explicit type casting
In the below example, we have created a double variable named numDouble i.e. `double numDouble = 1.23;`.

Notice the line, `int numInt = (int)numDouble;` Here, `(int)` is a cast expression that explicitly converts 
the double type value 1.23 to int type.

```C#
using System;

namespace TypeCasting
{
    internal class Program
    {
        static void Main(string[] args)
        {
            double myDouble = 1.23;
            int myInt = (int)myDouble;
            Console.WriteLine($"Original double value: {myDouble}");
            Console.WriteLine($"Converted int value: {myInt}");
        }
    }
}
```
When you run the program above, you will notice that the original value is 1.23 but the converted value is 1. That means
we have lost some data during the type conversion. This is because we are explicitly converting the larger data
type double to smaller type int.

<note>
We DON'T always lose data when we convert from larger type to smaller types. Losing data is dependent on the value that
we are converting and the size of the data type that is going to store the converted value. Example:

```C#
int myInt = 100;
byte myByte = (byte)myInt;
```

In the above case, we will not lose any data. This is because the integer variable holds the value 100 and in byte 
data type, we can store the values from 0 to 255, and 100 comes under this range and hence no data loss.
</note>

## Conversion with Helper Methods in C#
Observe the following example. Here, we have a string variable that holds the value 100 and we try to convert that 
value to an integer type. But this is not possible with the cast operator. Because cast operator will first check 
the type compatibility and it found that string and int are not compatible with each other because the string is 
used to store textual data which contains both alphanumeric and int contains only numeric data.

```C#
string str = "100";
int i1 = (int)str;
Console.WriteLine(i1);
```

If we try to execute the above code, we will get an error `Cannot convert type 'string' to 'int'`

for the conversion between non-compatible types like integer and string, the .NET Framework provided us with the:
- Convert class
- Parse method
- TryParse method

### Convert Class Helper Methods
The Convert class provides the following methods to convert a value to a particular type.

The following methods are going to convert the value irrespective of type compatibility.

It means if types are compatible, then it will convert and if types are not compatible, then also it will try 
to convert.

![convert class helper methods](convert-class-helper-methods.png)

For example, if you want to convert a string to an Int type, then you need to use either `Convert.ToInt16`, or 
`Convert.ToInt32`, or `Convert.ToInt64`. These helper methods are implemented as static methods inside 
the Convert class and hence you can access them directly.

```C#
using Microsoft.SqlServer.Server;
using System;

namespace TypeCasting
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string str = "100";
            int i1 = Convert.ToInt32(str);
            Console.WriteLine(i1);

            float f = 123.45F;
            string str2 = Convert.ToString(f);
            Console.WriteLine(str2);
        }
    }
}
```

When we are using the Convert class helper method to convert a value to a particular type, if types are not
compatible, then it will not throw you any error at compile time. At run time, it will try to convert the value
to that particular type and if the value is compatible then it will convert and if the value is not compatible, 
then it will throw a runtime error.

Consider the following example to understand this:

```C#
using Microsoft.SqlServer.Server;
using System;

namespace TypeCasting
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string myString = "Hello World";
            int myInt = Convert.ToInt32(myString);
            Console.WriteLine(myInt);
        }
    }
}
```
When we run the above code, we get an error stating "Input string was not in correct format"

This is because at runtime it tries to convert the value Hello to integer type which is not possible.

### Parse() Method in C#
In C#, we can also use the built-in Parse() method to perform type conversion.

```C#
using Microsoft.SqlServer.Server;
using System;

namespace TypeCasting
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string myString = "9278";
            int myInt = int.Parse(myString);
            Console.WriteLine(myInt);

            string myString2 = "TRUE";
            bool b = bool.Parse(myString2);
            Console.WriteLine(b);
        }
    }
}
```
The parse method also throws a runtime error if the types are not compatible.

### TryParse() Method in C#
Suppose, we want to convert a string to an integer type, then we can use the TryParse method as follows.

```C#
bool isConverted = int.TryParse("2342", out int myInt);
```
Here, what the TryParse method will do is, it will try to convert the string value 2342 to an integer. If 
the conversion is successful, then it will do two things. First, it will store the converted value into the
myInt variable and then it will return true. On the other hand, if the conversion is failed, then it will not 
store anything in the myInt variable and it will return false.

```C#
using Microsoft.SqlServer.Server;
using System;

namespace TypeCasting
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string awesomeString = "92834";
            bool isConverted = int.TryParse(awesomeString, out int myAwesomeInt);
            Console.WriteLine(isConverted); // True
            Console.WriteLine(myAwesomeInt); // 92834

            string anotherAwesomeString = "Hello, World!";
            isConverted = int.TryParse(anotherAwesomeString, out int anotherInt);
            Console.WriteLine(isConverted); // False
            Console.WriteLine(anotherInt); // 0
        }
    }
}
```