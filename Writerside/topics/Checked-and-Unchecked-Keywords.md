# Checked and Unchecked Keywords

C# provides checked and unchecked keywords which are used to handle integral type exceptions.

The Checked Keyword in C# is used to explicitly enable overflow checking for integral-type arithmetic 
operations and conversions.

The Unchecked Keyword in C# is used to suppress overflow-checking for integral-type arithmetic operations and 
conversions.

when the value of any integral type exceeds its range, it does not raise any exception, instead it will give us
unexpected or garbage results.

## Example Without Checked Keyword
In the following example, you can see that we have three integer variables. The integer variables a and b hold the 
maximum value that an integer can hold. Then we just simply add the integer a and b and stored them in the third 
integer variable i.e. c.

```C#
namespace CheckedAndUnchecked
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine($"Max integer value is: {int.MaxValue}");
            int a = 2147483647;
            int b = 2147483647;
            int c = a + b;
            Console.WriteLine(c);
        }
    }
}
```
Executing the above program, we get `-2` as the output.

What we expect is some error (overflow) or exception because in variable C we are definitely exceeding int max value.

This is where the Checked keyword helps us to achieve and throws overflow exception.

## Example With the Checked Keyword
The following code example uses the checked keyword. As we use the checked keyword, it should throw runtime 
exception rather than displaying -2.

```C#
namespace CheckedAndUnchecked
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine($"Max integer value is: {int.MaxValue}");
            int a = 2147483647;
            int b = 2147483647;
            int c = checked(a + b);
            Console.WriteLine(c);
        }
    }
}
```

**In simple words, we can say that the checked keyword is used in scenarios where you want to ensure that your 
left hand side data type is not getting overflow**

## Unchecked Keyword in C#
The unchecked keyword behaves almost the same way as the default behavior of the compiler.

```C#
namespace CheckedAndUnchecked
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine($"Max integer value is: {int.MaxValue}");
            int a = 2147483647;
            int b = 2147483647;
            int c = unchecked(a + b);
            Console.WriteLine(c);
        }
    }
}
```

When we run the above program, we get `-2` as the output.

The question that comes to our minds is, when by default, the compiler works the same as the unchecked keyword in C#,
then why do we need the unchecked keyword?

To understand this, consider the example below where num1 and num2 are const:

```C#
namespace CheckedAndUnchecked
{
    internal class Program
    {
        static void Main(string[] args)
        {
            const int num1 = 2147483647;
            const int num2 = 2147483647;
            int sum = num1 + num2;
            Console.WriteLine(sum);
        }
    }
}
```
When we try to compile the above project, we get the following error:
```Plain Text
The operation overflows at compile time in checked mode
```

If you want to bypass this behavior then you need to use the unchecked keyword in C#.

```C#
namespace CheckedAndUnchecked
{
    internal class Program
    {
        static void Main(string[] args)
        {
            const int num1 = 2147483647;
            const int num2 = 2147483647;
            int sum = unchecked(num1 + num2);
            Console.WriteLine(sum);
        }
    }
}
```