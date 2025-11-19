# How to Pass Data to Thread Function in Type Safe Manner

In the below example, the DisplayNumbers function takes an argument of the object type. Then in the main method, 
we created an instance of the ParameterizedThreadStart delegate, and to the constructor of the 
`ParameterizedThreadStart` delegate, we pass the DisplayNumbers function.

Next, we created an instance of the Thread class and to the constructor of the Thread class, we pass the 
`ParameterizedThreadStart` delegate instance as a parameter that points to the DisplayNumbers function.

Finally, we call the Start method and pass a string value “Hi”, and here we will not get any compile-time error.

```C#
using System;
using System.Threading;

namespace ThreadingDemo
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ParameterizedThreadStart ptsd = new ParameterizedThreadStart(DisplayNumbers);
            Thread t1 = new Thread(ptsd);
            t1.Start("Hi"); // we should pass a number but nothing prevents us from passing anything else
        }

        static void DisplayNumbers(object max)
        {
            int limit = Convert.ToInt32(max);
            for (int i = 1; i <= limit; i++)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

At the time of compilation, we will not get any compile-time error. But when we run the application, we will
get the following runtime error

```

Unhandled Exception: System.FormatException: Input string was not in a correct format.  
   at System.Number.StringToNumber(String str, NumberStyles options, NumberBuffer& number, NumberFormatInfo 
   info, Boolean parseDecimal)  
   at System.Number.ParseInt32(String s, NumberStyles style, NumberFormatInfo info)  
   at System.String.System.IConvertible.ToInt32(IFormatProvider provider)  
   at System.Convert.ToInt32(Object value)  
   at ThreadingDemo.Program.DisplayNumbers(Object max)...
```

This is because the thread function is not type-safe as it operates on the object data type.

## How to Make the Thread Function Type Safe
When we are saying type-safe, it means we should not use the object data type.

Here in our example, we need to use the data type as an integer. So at the time of compilation, if we pass any data 
other than an integer, then it should give us a compile-time error.

Let us see how to achieve this step by step.

### Step 1
In order to pass the data in a type-safe manner to a Thread function in C#, first, you need to encapsulate 
the thread function and the data it requires in a helper class.

```C#
using System;
using System.Threading;

namespace ThreadingDemo2
{
    class NumberHelper
    {
        private int _Number;
        public NumberHelper(int Number)
        {
            _Number = Number;
        }
        void DisplayNumbers()
        {
            for (int i = 1; i <= _Number; i++)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

As you can see, we have created the above NumberHelper class with one private variable i.e. _Number, 
one parameterized constructor, and one method i.e. DisplayNumbers.

The private variable _Number is going to hold the target number. The constructor takes one input parameter of integer 
type and then assigns that value to the private variable. So, while we are creating the instance of NumberHelper 
class we need to supply the Number value.

Finally, the DisplayNumbers function is used to display the values starting from 1 to the value that is present 
in the _Number variable.

### Step 2
In the main method, we need to create an instance of NumberHelper class and to its constructor, we need to pass the 
integer value. Then create the ThreadStart delegate instance and pass the DisplayNumbers function as a parameter 
to its constructor.

```C#
using System;
using System.Threading;

namespace ThreadingDemo2
{
    class NumberHelper
    {
        private int _Number;
        public NumberHelper(int Number)
        {
            _Number = Number;
        }
        public void DisplayNumbers()
        {
            for (int i = 1; i <= _Number; i++)
            {
                Console.WriteLine(i);
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            int Max = 10;
            NumberHelper nh = new NumberHelper(Max);
            Thread t1 = new Thread(nh.DisplayNumbers);
            t1.Start();
        }
    }
}
```