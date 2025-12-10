# Async and Await in C#

In modern C# code, in order to use asynchronous programming, we need to use async and await keywords. The idea is 
that if we have a method in which we want to use asynchronous programming, then we need to mark the method with the
async keyword as shown in the below image.

![async keyword](async-programming-async-keyword.png)

For those asynchronous operations for which we do not want to block the execution thread i.e. the current thread,
we can use the await operator as shown in the below image.

![await keyword](async-programming-await-keyword.png)

So, when we use await operator, what we are doing is, we are freeing the current thread from having to wait for the
execution of the task. In this way, we are avoiding blocking the current thread that we’re using and then that 
thread can be used in another task.

## Example to Understand Async and Await
Please have a look at the below example. It’s a very simple example. Inside the main method, first, we print 
that main method started, then we call the SomeMethod. Inside the SomeMethod, first, we print that SomeMethod 
started and then the thread execution is sleep for 10. After 10 seconds, it will wake up and execute the other 
statement inside the SomeMethod method. Then it will come back to the main method, where we called SomeMethod. 
And finally, it will execute the last print statement inside the main method.

```C#
using System;
using System.Threading;

namespace AsyncProgramming
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Main method started");
            SomeMethod();
            Console.WriteLine("Main method ended");
        }

        static void SomeMethod()
        {
            Console.WriteLine("SomeMethod started");
            Thread.Sleep(TimeSpan.FromSeconds(10));
            Console.WriteLine("SomeMethod ended");
        }
    }
}
```

When you execute the above code, you will see that after printing "SomeMethod Started", the console window is frozen 
for 10 seconds. This is because here we are not using asynchronous programming. One thread i.e. the Main thread is 
responsible for executing the code And when we call Thread.Sleep method the current thread is blocked for 10 seconds. 
This is a bad user experience.

![Output](async-programming-output-1.png)

Now, let us see how we can overcome this problem by using asynchronous programming.

`Thread.Sleep()` is a synchronous method. In the code below, we are using `Task.Delay()` method, which does the exact
same thing as `Thread.Sleep()` only that it is asynchronous.

If we want to wait for the task i.e. Task.Delay to be done, then we have to use the await operator.

As we said earlier the await operator is going to release the current thread that is running from having to wait for 
this operation. Therefore, that thread is going to be available for all our tasks. And then after 10 seconds, the 
thread will be called to the place (i.e. Task.Delay()) in order to run the rest code of the SomeMethod.

As we have used await keyword inside the SomeMethod, we must have to make the SomeMethod as asynchronous as using the 
async keyword.

```C#
using System;
using System.Threading.Tasks;

namespace AsyncProgramming
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Main method started");
            SomeMethod();
            Console.WriteLine("Main method ended");
            Console.ReadKey();
        }

        async static void SomeMethod()
        {
            Console.WriteLine("SomeMethod started");
            await Task.Delay(TimeSpan.FromSeconds(10));
            Console.WriteLine("SomeMethod ended");
        }
    }
}
```

![Output](async-programming-output-2.png)

Now, if you run the above code, then you will see that after printing the Some Method Started when the statement 
Task.Dealy() executed, it will free the current thread, and then that current thread comes and execute the rest of 
the code inside the main method. And after 10 seconds again thread come back to the SomeMethod and execute the rest 
of the code inside the SomeMethod.

