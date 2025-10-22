# Literals in C#

The Literals in C# are the fixed values (or hard-coded values) given to your variable and these values cannot be 
modified during the execution of the program.

For example, `int x = 100;` Here `x` is a variable, and `100` is literal.

C# has the following types of literals:
- Integer literals
- Floating-point literals
- Character literals
- String literals
- Boolean literals

## Integer Literals
The Integer literals in C# are used to write values of types int, uint, long, ulong, etc.

We can represent the Integer Literals in the form of Decimal, Binary, or Hexadecimal.

Here, we need to use a prefix to specify whether the Integer Literal is Binary (prefixed with 0b), or Hexadecimal (0X)
type. No prefix is required for the Decimal numbers.

By default, every Integer Literal is of int type. For Integral data types (byte, short, int, long), we can specify 
literals or fixed values in the following 3 ways:
- **Decimal (base-10)**: Digits from 0-9 are allowed in this form. No prefix is required for the decimal type of 
literal. Example: `int x=101;`
- **Hexadecimal (base-16)**: Digits 0-9 are allowed and also characters from a-f are allowed in this form. 
Furthermore, both uppercase and lowercase characters can be used. Here, the hexadecimal number should be prefixed 
with 0X or 0x. and suffix with F. Example: `int x = 0X123F;` or `int x = 0x123f;`
- **Binary (0 and 1)**:  In this form, the allowed digits are only 1’s and 0’s. The binary number should be 
prefixed with 0b. Example: `int x = 0b1111;`.

Octal numbers allow digits from 0 to 7 and are prefixed with 0 for example `int x = 0156;`. **However, C# DOES NOT
SUPPORT OCTAL** [Learn more here](https://stackoverflow.com/questions/4247037/octal-equivalent-in-c-sharp).

[Refer to this for conversions](https://calculator.name/baseconvert/decimal/hexadecimal/)

```C#
using System;

namespace Literals
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // Decimal literal
            // allowed digits are 0 to 9
            // No prefix or suffix is required
            int decimalNumber = 210;
            Console.WriteLine($"Decimal literal: {decimalNumber}");

            // Hexadecimal literal
            // allowed digits are 0 to 9 and characters a to f
            // prefix with 0x or 0X and suffix with f or F (not case sensitive)
            int hexadecimalNumber = 0x372F;
            Console.WriteLine($"Hexadecimal literal: {hexadecimalNumber}");

            // Binary literal
            // allowed digits are 0 and 1 only.
            // prefix with 0b
            int binaryNumber = 0b110111;
            Console.WriteLine($"Binary literal: {binaryNumber}");
        }
    }
}
```

## Floating Point Literal in C#
The Literals in C# which have an integer part and a decimal point are known as Floating-Point literals i.e. 
Numbers with Decimal.

The Floating-Point Literals are used to write values of types float, double, and decimal.

By default, every floating-point literal is of double type and hence we can’t assign values directly to 
float and decimal variables.

If you want to assign values to a float variable, then you need to add the suffix `f` at the end 
of the floating-point literal.

Similarly, if you want to assign values to a decimal variable, then you need to add the suffix `m` or `M` at 
the end of the floating-point literal.

If you are not suffixing the floating-point literal with anything, then the floating-point literal is going 
to be double by default. If you want, you can also specify explicitly floating-point literal as double type
by suffixing it with `d` or `D`.

```C#
using System;

namespace Literals
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // Double literal
            // No suffix is required but you can suffix with D or d
            double myDouble = 99.25D;
            double myDouble2 = 88.92;
            Console.WriteLine($"{myDouble} {myDouble2}");

            // Float literal
            // Suffix with f or F
            float myFloat = 12.3f;
            Console.WriteLine(myFloat);

            // Decimal literal
            // Suffix with d or D
            decimal myDecimal = 12.3M;
            Console.WriteLine(myDecimal);
        }
    }
}
```

## Character Literals in C#
The Character Literals in C# are enclosed in single quotes, for example, 'a', and can be stored in a simple 
variable of char data type.

A character literal can be a plain character for example, 'a', an escape sequence for example, '\t', or a 
universal character for example, '\u02B0'.

We can specify character literals in 3 ways:
- **Using single quotes**: We can specify Character literals to a char data type as a single character using
a single quote. Example `char ch = 'A';`
- **Character literals using escape sequence**: Every escape character in C# can be specified as a character literal.
For example, the new line character `\n` can be represented as `char ch = '\n'`.
- **Character literals using unicode representation**: We can specify Character literals using Unicode 
representation '\uXXXX' where XXXX is the 4 hexadecimal numbers. Example `char ch = '\u0041';`, here, \u0041 represents
letter A. [Here is a list of unicode characters](https://en.wikipedia.org/wiki/List_of_Unicode_characters)

```C#
using System;

namespace Literals
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // character literals using a single quote
            char ch = 'A';
            Console.WriteLine(ch);

            // character literals using unicode representation
            char ch2 = '\u0041';
            Console.WriteLine(ch2);

            // character literals using escape characters
            char ch3 = '\t';
            Console.WriteLine(ch3);
        }
    }
}
```

## String literals in C#
The Literals in C# which are enclosed with double quotes ("") or start with @"" are known as string literals.

In C#, we can represent string literals in 2 ways as follows:
- **Regular string literals**: A regular string literal in C# consists of zero or more characters enclosed in 
double quotes, for example "Hello, World!" and may include both simple escape sequence and unicode sequence.
- **Verbatim string literals**: A verbatim string literal starts with an @ character followed by a double-quote
which may contain zero or more characters, and ends with a double-quote character. Verbatim strings can store escape
sequence and in this case, the escape sequence will be printed as it is in the output.

```C#
using System;

namespace Literals
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // Regular String literal
            string s1 = "Hello, World!";
            Console.WriteLine(s1);

            // Verbatim String literal
            string s2 = @"This is cool\n";
            Console.WriteLine(s2);
        }
    }
}
```

## Boolean Literals in C#
The only two values allowed here are `true` and `false`.

```C#
using System;

namespace Literals
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // boolean literals - true or false
            bool b1 = true;
            bool b2 = false;
            Console.WriteLine($"{b1} {b2}");
        }
    }
}
```