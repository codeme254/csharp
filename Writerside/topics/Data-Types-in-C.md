# Data Types in C#

A data type in C# specifies the type of data that a variable can store such as integer, floating, boolean,
character, string, etc.

In the real world, we have different types of data like integers, floating-point, characters, boolean, strings, etc.

To store all these different kinds of data in a program to perform business-related operations, we need the data types.

Data types give information about:
- **size** of the memory location.
- **Range of data** that can be stored in that memory location.
- **Legal operations** that can be performed on that memory location.
- **Type of results** that come out from an expression when these types are used inside those expressions.

The following diagram shows the different types of data available in C#.

![data types classification](data-types-classification.png)

There are three categories of data type available in C#:
- Value data types
- Reference data types
- Pointer data types

## Value Data Types
The data type which stores the value directly in the memory is called the Value Data Type in C#.

The examples are int, char, boolean, and float which store numbers, alphabets, true/false, and floating-point 
numbers respectively.

The value data types in C# again classified into two types are as follows:
- **Predefined data types**: Example includes Integer, Boolean, Boolean, Long, Double, Float, etc.
- **User-defined data types**: Example includes Structure, Enumerations, etc.

Following are some value data types in C#:

### `byte`
It is a .NET Data Type that is used to represent an 8-Bit unsigned integer (only positive values).

As it represents an 8-bit unsigned integer, so it can store 2<sup>8</sup> i.e. 256 numbers.

As it stores only positive numbers, so the minimum value it can store is 0 and the maximum value it can store is 255.
<note>
Because ASCII characters map neatly into that 0–127 range, you can store ASCII codes in a byte, but that’s just a
use case, not the purpose of the type.

ASCII stands for American Standard Code for Information Interchange. It’s basically one of the oldest and simplest 
character encoding systems computers use to represent text.

ASCII assigns a number (0–127) to each character letters, digits, punctuation marks, and control
characters (like newline or tab).

So when your computer stores text like "Hello", what it’s really storing (in ASCII) is something like:
`72 101 108 108 111`
</note>

![ASCII](ascii.png)

```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            byte b1 = 55;
            Console.WriteLine(b1);
            Console.WriteLine($"ASCII equivalent of {b1} is {(char)b1}");

            Console.WriteLine($"Byte max value {byte.MaxValue}");
            Console.WriteLine($"Byte min value {byte.MinValue}");
        }
    }
}
```
Try the following:
- Assigning a negative value to b1.
- Assigning a digit above 255

### `sbyte`
Now, if you want to store both positive and negative values, then you need to use the signed byte data type i.e. 
`SByte`.

This SByte data type represents an 8-bit signed integer.

When data types are signed they can hold both positive and negative values.

The maximum value it can store is 127 and the minimum value it can store is -128

```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            sbyte b2 = -50;
            Console.WriteLine(b2);
            Console.WriteLine($"SByte max value {sbyte.MaxValue}");
            Console.WriteLine($"SByte min value {sbyte.MinValue}");
        }
    }
}
```

### `char`
Char data type is used to represent characters.

Characters are enclosed in single quotes.

```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            char studentGrade = 'A';
            Console.WriteLine(studentGrade);
        }
    }
}
```

Unicode is also allowed;

```c#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            char c2 = '\u0061';
            Console.WriteLine(c2);
        }
    }
}
```

### `string`
A string is a series of characters enclosed within double quotes.

```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string firstName = "John";
            string lastName = "Doe";
            Console.WriteLine($"{firstName} {lastName}");
        }
    }
}
```

### `Boolean`
Only stores `true` or `false`.

You can use the `Boolean` or the `bool` keyword.

```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // boolean
            Boolean isMale = true;
            Console.WriteLine(isMale);
      }
    }
}

```

### Integer types
They are used to store whole numbers.

Divided into three as follows:
- 16-bit signed: `Int16` also known as `short`
- 32-bit signed: `Int32` also known as `int`
- 64-bit signed: `Int64` also known as `long`

As above data types are signed, they can store both positive and negative numbers.

Based on the data type, the size they can hold is going to vary.

If we want to store only positive numbers, the dotnet framework provides the unsigned versions of each of these data
types.
- `UInt16` or `ushort`
- `UInt32` or `uint`
- `UInt64` or `ulong`

#### 16-bit signed: `Int16`
As it is 16-Bit, so it is going to store 2<sup>16</sup> numbers i.e. 65536.

As it is signed, so it is going to store both positive and negative values. So, we need to divide 65536/2 i.e. 32,768. 
So, it is going to store 32,768 positive numbers as well as 32,768 negative numbers. So, the positive numbers will 
start from 0 up to 32,767 and the negative numbers will start from -1 up to -32,768.

```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Int16 myNum = 30000;
            Console.WriteLine(myNum);
            Console.WriteLine($"Int16 max value: {Int16.MaxValue}");
            Console.WriteLine($"Int16 min value: {Int16.MinValue}");
        }
    }
}

```

#### 32-bit signed: `Int32`
As it is 32-Bit, so it is going to store 2<sup>32</sup> numbers i.e. 4,294,967,296.

As it is signed, so it is going to store both positive and negative values. So, we need to divide 4,294,967,296/2 i.e.
2,14,74,83,648. So, it is going to store 2,14,74,83,648 positive numbers as well as 2,14,74,83,648 negative numbers. 
So, the positive numbers will start from 0 up to 2,14,74,83,647 and the negative numbers will start from -1 up to 
-2,14,74,83,648.

```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Int32 myNum2 = 2_000_000;
            Console.WriteLine(myNum2);
            Console.WriteLine($"Int32 max value: {Int32.MaxValue}");
            Console.WriteLine($"Int32 min value: {Int32.MinValue}");
        }
    }
}
```

#### 64-bit signed: `Int64`
As it is 64-Bit, so it is going to store 2<sup>64</sup> numbers.

```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Int64 myNum3 = 2_000_000_000;
            Console.WriteLine(myNum3);
            Console.WriteLine($"Int64 max value: {Int64.MaxValue}");
            Console.WriteLine($"Int64 min value: {Int64.MinValue}");
        }
    }
}

```

As for the unsigned version of the above data types, ref the code below.

Remember **ushort** is alias to **UInt16**, **uint** is alias to **UInt16** and **ulong** is alias to **UInt64**.

Also, **short** is alias to **Int16**, **int** is alias to **Int32** and **long** is alias to **Int64**.
```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine($"UInt16 max value: {UInt16.MaxValue}");
            Console.WriteLine($"UInt16 min value: {UInt16.MinValue}");
            Console.WriteLine($"ushort max value: {ushort.MaxValue}");
            Console.WriteLine($"ushort min value: {ushort.MinValue}");

            Console.WriteLine($"UInt32 max value: {UInt32.MaxValue}");
            Console.WriteLine($"UInt32 min value: {UInt32.MinValue}");
            Console.WriteLine($"uint max value: {uint.MaxValue}");
            Console.WriteLine($"uint min value: {uint.MinValue}");

            Console.WriteLine($"UInt64 max value: {UInt64.MaxValue}");
            Console.WriteLine($"UInt64 min value: {UInt64.MinValue}");
            Console.WriteLine($"ulong max value: {ulong.MaxValue}");
            Console.WriteLine($"ulong min value: {ulong.MinValue}");
        }
    }
}

```

### Decimal Number Types
They are used to store numbers with decimal points.

In numbers with decimals, we are provided with 3 flavors:
- **Single**: single-precision floating-point number.
- **Double**: double-precision floating-point number.
- **Decimal**: represents a decimal floating point number.

<note>
In order to create a single value, we need to add the suffix f at the end of the number, similarly, if you want to 
create a Decimal value, you need to suffix the value with m (Capital or Small does not matter). If you are not 
suffixing with anything, then the value is going to be double by default.
</note>

You can also use the short hand names, i.e:
- **float** for **Single**
- **double** for **Double**
- **decimal** for **Decimal**

```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Single myVal = 10.234F;
            Console.WriteLine(myVal);
            Console.WriteLine($"Single max value: {Single.MaxValue}");
            Console.WriteLine($"Single min value: {Single.MinValue}");

            Double myVal2 = 4323.242342;
            Console.WriteLine(myVal2);
            Console.WriteLine($"Double max value: {Double.MaxValue}");
            Console.WriteLine($"Double min value: {Double.MinValue}");

            Decimal myVal3 = 92342897.243141M;
            Console.WriteLine(myVal3);
            Console.WriteLine($"Decimal max value: {Decimal.MaxValue}");
            Console.WriteLine($"Decimal min value: {Decimal.MinValue}");
        }
    }
}
```

## How to Get the Size of PreDefined Data Types in C#
If you want to know the actual size of pre-defined or built-in data types, then you can make use of `sizeof` operator.

The method returns the size of a data type in bytes.

```C#
using System;

namespace DataTypes
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine($"Size of int {sizeof(int)}");
            Console.WriteLine($"Size of decimal {sizeof(decimal)}");
            Console.WriteLine($"Size of byte {sizeof(byte)}");
            Console.WriteLine($"Size of sbyte {sizeof(sbyte)}");
        }
    }
}
```

## Reference Data Types in C#
Reference types do not store the actual data stored in a variable, rather they store the reference to the variables.

Reference types are categorized into two:
- **Predefined types**: such as objects, strings, e.t.c
- **User-defined types**: such as classes and interfaces.

More about reference types later.

## Pointer type in C#
Pointers are used to store the memory address of other variables.

To get the pointer details, we have two symbols, ampersand (&) and asterisk (*)
1. ampersand (&): It is known as Address Operator. It is used to determine the address of a variable.
2. asterisk (*):  It is also known as Indirection Operator. It is used to access the value of an address.