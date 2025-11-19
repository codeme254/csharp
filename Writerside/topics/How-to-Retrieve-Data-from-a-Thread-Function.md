# How to Retrieve Data from a Thread Function

As of now, we have discussed the uses of ThreadStart and ParameterizedThreadStart delegates. If you notice,
the return type of these two delegates is void as shown:

![return types for ThreadStart and ParameterizedThreadStart are void](multithreading-return-types.png)

So, using the above two delegates we cannot return any data from a method as the return type is void.

To retrieve data from a thread function, we use a **callback method**.

## How to Retrieve Data from a Thread Function using Callback Method
Let us see how to achieve this step by step.

### Step 1
In order to retrieve the data from a thread function, first, you need to encapsulate the thread function and
the data it requires in a helper class.

To the constructor of the Helper class, you need to pass the required data if any as well as a delegate representing 
the callback method.

From the thread function body, you need to invoke the callback delegate just before the thread function ends. 
And one more thing you need to take care that the callback delegate and the actual callback method signature 
should be the same.

```C#
using System;
using System.Threading;

namespace ThreadingDemo3
{
    class NumberHelper
    {
        public delegate void ResultCallbackDelegate(int Results);

        private int _Number;
        private ResultCallbackDelegate _resultCallbackDelegate;
        public NumberHelper(int Number, ResultCallbackDelegate ResultCallbackDelegate)
        {
            _Number = Number;
            _resultCallbackDelegate = ResultCallbackDelegate;
        }

        public void CalculateSum()
        {
            int Result = 0;
            for (int i = 1; i <= _Number; i++)
            {
                Result = Result + i;
            }
            // Before the end of the thread function, call the callback method
            if (_resultCallbackDelegate != null)
            {
                _resultCallbackDelegate(Result);
            }
        }
    }

}
```

### Step 2
In the second step, we need to create the callback method whose signature should be the same as the signature of the 
CallBack Delegate. In our example, ResultCallBackMethod is the callback method and its signature is the same as 
the signature of the ResultCallbackDelegate delegate.

Within the Main method, we need to create an instance of the ResultCallbackDelegate delegate and while creating the 
instance we need to pass the ResultCallBackMethod as the parameter to its constructor. So when we invoke the 
delegate it will call the ResultCallBackMethod method.

```C#
using System;
using System.Threading;

namespace ThreadingDemo3
{
    public delegate void ResultCallbackDelegate(int Results);
    class NumberHelper
    {
        private int _Number;
        private ResultCallbackDelegate _resultCallbackDelegate;
        public NumberHelper(int Number, ResultCallbackDelegate ResultCallbackDelegate)
        {
            _Number = Number;
            _resultCallbackDelegate = ResultCallbackDelegate;
        }

        public void CalculateSum()
        {
            int Result = 0;
            for (int i = 1; i <= _Number; i++)
            {
                Result = Result + i;
            }
            // Before the end of the thread function, call the callback method
            if (_resultCallbackDelegate != null)
            {
                _resultCallbackDelegate(Result);
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            ResultCallbackDelegate rcd = new ResultCallbackDelegate(ResultCallBackMethod);
            int Number = 10;
            NumberHelper nh = new NumberHelper(Number, rcd);
            Thread t1 = new Thread(nh.CalculateSum);
            t1.Start();
        }

        public static void ResultCallBackMethod(int Result)
        {
            Console.WriteLine($"Result is {Result}");
        }
    }

}
```