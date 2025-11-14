# Generic Delegates

A generic delegate is just a delegate that uses type parameters, so you can reuse the same delegate with different 
data types instead of creating a new delegate type every time.

Generic Delegates in C# were introduced as part of .NET Framework 3.5 which doesn’t require defining the delegate
instance in order to invoke the methods.

To understand the Generic Delegates in C# you should have the basic knowledge of Delegates.

## Why do we need Generic Delegates?
Let's do a quick review of how we use delegates to invoke methods.

Let's say we have the following three methods, and we want to invoke these methods using delegates:

![Methods](delegates-generic-delegates-example-1-methods.png)

As you can see in the above code, the AddNumber1 method takes three parameters and returns a value of double type.

Similarly, the AddNumber2 method takes three parameters but it does not return any value and here the return 
type is void.

The third method i.e. the CheckLength method takes one string parameter and returns a Boolean value. If the 
string length is greater than 5, then it will return true else it will return false.

Now if we want to invoke the above three methods using delegates in C#, then we need to create three delegates whose
signature should match the signature of the above three methods as shown in the below image:

![Delegates](delegates-generic-delegates-example-1-delegates.png)

Now, once we have created the delegates. then we can invoke the methods by creating instances of each delegate
referring to the respective methods and then we can invoke the delegate as shown in the below code.

![Delegates invocation](delegates-generic-delegates-example-1-delegates-invocation.png)

The complete code example is given below:

```C#
using System;

namespace GenericDelegates
{
    public delegate double AddNumber1Delegate(int no1, float no2, double no3);
    public delegate void AddNumber2Delegate(int no1, float no2, double no3);
    public delegate bool CheckLengthDelegate(string name);
    internal class GenericDelegates
    {
        public static double AddNumber1(int no1, float no2, double no3)
        {
            return no1 + no2 + no3;
        }

        public static void AddNumber2(int no1, float no2, double no3)
        {
            Console.WriteLine(no1 + no2 + no3);
        }

        public static bool CheckLength(string name)
        {
            if (name.Length > 5) return true;
            return false;
        }

        static void Main(string[] args)
        {
            AddNumber1Delegate obj1 = new AddNumber1Delegate(AddNumber1);
            double Result = obj1.Invoke(100, 125.45f, 456.789);
            Console.WriteLine(Result);

            AddNumber2Delegate obj2 = new AddNumber2Delegate(AddNumber2);
            obj2.Invoke(50, 255.45f, 123.456);

            CheckLengthDelegate obj3 = new CheckLengthDelegate(CheckLength);
            bool Status = obj3.Invoke("Pranaya");
            Console.WriteLine(Status);
        }
    }
}
```

As of now, this is the way, we use delegates to invoke methods.

### Do we really need to create custom delegates to invoke methods in C#?
Simple answer: NO.

## Types of Generic Delegates
As we have seen, up until this point, we have been using custom delegates to invoke methods in C#, but this is not
necessarily required.

C#.NET Framework provides some generic delegates which can do the job for us.

C# provides three Generic Delegates; they are as follows:
- **Func**
- **Action**
- **Predicate**

### Func Generic Delegate
The Func Generic Delegate in C# is present in the System namespace. 

This delegate takes one or more input parameters and returns one out parameter.

The last parameter is considered as the return value.

The Func Generic Delegate in C# can take up to 16 input parameters of different or the same data types.

It must have one return type. The return type is mandatory but the input parameter is not mandatory.

<note>
Whenever your delegate returns some value, whether by taking any input parameter or not, you need to use 
the Func Generic delegate in C#.
</note>

### Action Generic Delegate
The Action Generic Delegate in C# is also present in the System namespace.

It takes one or more input parameters and returns nothing.

This delegate can take a maximum of 16 input parameters of the different or same data types.

<note>
Whenever your delegate does not return any value, whether by taking any input parameter or not, then you need to 
use the Action Generic delegate in C#.
</note>

### Predicate Generic Delegate
The Predicate Generic Delegate in C# is also present in the System namespace.

This delegate is used to verify certain criteria of the method and returns the output as Boolean, either True or False.

It takes one input parameter and always returns a Boolean value which is mandatory.

This delegate can take a maximum of 1 input parameter and always return the value of the Boolean type.

<note>
Whenever your delegate returns a Boolean value, by taking only one input parameter, then you need to use the 
Predicate Generic delegate in C#.
</note>

## Example to Understand Generic Delegate in C#
In our first example, we created three methods:
1. The **AddNumber1** method takes three parameters and returns a **double** value. Here we will use 
the **Func Generic Delegate** to achieve the same thing as we achieved in the first example.
2. Similarly, the **AddNumber2** method takes three parameters but does not return any value. Here we 
will use the **Action Generic Delegate** to achieve the same thing as we achieved in the first example.
3. The **CheckLength** method takes one string input parameter and returns a boolean value. Here we will use the 
**Predicate Generic Delegate** to achieve the same thing as we achieved in the first example.

### How to use Func Generic Delegate
The Func Generic Delegate in C# is used whenever your delegate returns some value, whether by taking any input 
parameter or not.

In our example, the AddNumber1 method takes some input and returns one output. So, the AddNumber1 method signature
is matched with the Func generic delegate signature. So, here, instead of creating our own delegate to invoke the 
AddNumber1 method, we can use the Func generic delegate to invoke the AddNumber1 method as shown in the below code.

![Func generic delegate](delegates-generic-delegates-func.png)

As shown in the above code, the Func Generic Delegate takes four parameters, the first three are input parameters and 
the last one is the return value. To the Func Generic Delegate constructor, we pass the AddNumber1 method which is 
going to execute when we invoke the Func delegate.

```C#
using System;

namespace GenericDelegates2
{
    internal class GenericDelegates
    {
        public static double AddNumber1(int no1, float no2, double no3)
        {
            return no1 + no2 + no3;
        }

        public static void AddNumber2(int no1, float no2, double no3)
        {
            Console.WriteLine(no1 + no2 + no3);
        }

        public static bool CheckLength(string name)
        {
            if (name.Length > 5) return true;
            return false;
        }

        static void Main(string[] args)
        {
            Func<int, float, double, double> obj1 = new Func<int, float, double, double>(AddNumber1);
            double Result = obj1.Invoke(100, 124.45f, 456.789);
            Console.WriteLine(Result);
        }
    }
}
```

### How to use Action Generic Delegate
The Action Generic Delegate in C# is used whenever your delegate does not return any value, whether by taking
any input parameter or not.

In our example, the AddNumber2 method takes some input but does not return any value. So, the AddNumber2 method 
signature is matched with the Action generic delegate signature. So, here, instead of creating our own delegate 
to invoke the AddNumber2 method, we can use the Action generic delegate to invoke the AddNumber2 method as shown 
in the below code.

![Action Generic Delegate](delegates-generic-delegate-action.png)

```C#
using System;

namespace GenericDelegates2
{
    internal class GenericDelegates
    {
        public static double AddNumber1(int no1, float no2, double no3)
        {
            return no1 + no2 + no3;
        }

        public static void AddNumber2(int no1, float no2, double no3)
        {
            Console.WriteLine(no1 + no2 + no3);
        }

        public static bool CheckLength(string name)
        {
            if (name.Length > 5) return true;
            return false;
        }

        static void Main(string[] args)
        {
            Action<int, float, double> obj2 = new Action<int, float, double>(AddNumber2);
            obj2.Invoke(50, 255.45f, 123.456);
        }
    }
}
```

### How to use Predicate Generic Delegate
The Predicate Generic Delegate in C# is used whenever your delegate returns a Boolean value, by taking only one 
input parameter.

In our example, the CheckLength method takes one input parameter of string type and returns a Boolean value. 
So, the CheckLength method signature is matched with the Predicate generic delegate signature. So, here, instead
of creating our own delegate to invoke the CheckLength method, we can use the Predicate generic delegate to invoke 
the CheckLength method as shown in the below code.

![Predicate Generic Delegate](delegates-generic-delegate-predicate.png)

```C#
using System;

namespace GenericDelegates2
{
    internal class GenericDelegates
    {
        public static double AddNumber1(int no1, float no2, double no3)
        {
            return no1 + no2 + no3;
        }

        public static void AddNumber2(int no1, float no2, double no3)
        {
            Console.WriteLine(no1 + no2 + no3);
        }

        public static bool CheckLength(string name)
        {
            if (name.Length > 5) return true;
            return false;
        }

        static void Main(string[] args)
        {
            Predicate<string> obj3 = new Predicate<string>(CheckLength);
            bool Status = obj3.Invoke("Pranaya");
            Console.WriteLine(Status);
        }
    }
}
```

## Points to Remember When Working With Generic Delegates in C#
1. Func, Action, and Predicate are Generic Inbuilt delegates that are present in the System namespace which is 
introduced in C# 3.
2. All these three delegates can be used with the method, Anonymous Method, and Lambda Expressions in C# (more about 
these later).
3. The Func delegates can contain a maximum of 16 input parameters and must have one return type and that 
will be the last parameter in the parameter list.
4. Action delegate can contain a maximum of 16 input parameters and does not have any return type.
5. The Predicate delegate should satisfy some criteria of a method and must have only one input parameter. 
By default, it is having one output parameter of return type and we don’t have to pass the output parameter 
to the Predicate.