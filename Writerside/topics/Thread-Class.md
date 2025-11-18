# Thread Class in C#

The Thread class in C# is responsible for creating custom threads.

With the help of the thread class we can create both **foreground** and **background** threads.

The thread class also allows us to set the priority of a thread.

If you go to the definition of the Thread class, then you will see that is a sealed class and as it is a sealed
class, this class cannot be inherited i.e. further inheritance is not possible.

The Thread class in C# provides lots of useful properties, methods, and constructors

## Thread Class Properties
The Thread class in C# provides lots of properties. Some of the important properties are as follows:
- **CurrentThread**: This property is used to get the currently running thread. It returns a Thread that is the 
representation of the currently running thread.
- **IsAlive**: This property is used to get a value indicating the execution status of the current thread. It 
returns true if this thread has been started and has not terminated normally or aborted; otherwise, false.
- **IsBackground**: This property is used to get or set a value indicating whether or not a thread is a background
thread. It returns true if this thread is or is to become a background thread; otherwise, false.
- **ManagedThreadId**: This property is used to get a unique identifier for the current managed thread. It returns
an integer that represents a unique identifier for this managed thread.
- **Name**: This property is used to get or set the name of the thread. It returns a string containing the
name of the thread, or null if no name was set.
- **Priority**: This property is used to get or set a value indicating the scheduling priority of a thread. It 
returns one of the System.Threading.ThreadPriority values. The default value is System.Threading.ThreadPriority.Normal.
- **ThreadState**: This property is used to get a value containing the states of the current thread. It returns one 
of the System.Threading.ThreadState values indicate the state of the current thread. The initial value is Unstarted.
- **IsThreadPoolThread**: This property is used to get a value indicating whether or not a thread belongs to the
managed thread pool. It returns true if this thread belongs to the managed thread pool; otherwise, false.

## Thread Class Methods
The Thread class in C# provides lots of methods. Some of the important methods are as follows:
- **Abort()**: This method is used to terminate the thread. Raises a ThreadAbortException in the thread on which it 
is invoked, to begin the process of terminating the thread. Calling this method usually terminates the thread.
- **Interrupt()**: This method is used to interrupt a thread that is in the WaitSleepJoin thread state.
- **Join()**: This method is used to block the calling thread until the thread represented by this instance 
terminates while continuing to perform standard COM and SendMessage pumping.
- **ResetAbort()**: This method is used to an System.Threading.Thread.Abort(System.Object) requested 
for the current thread.
- **Resume()**: This method is used to resume a thread that has been suspended.
- **Sleep(Int32)**: This method is used to suspend the current thread for the specified number of milliseconds.
- **Start()**: This method causes the operating system to change the state of the current instance to 
System.Threading.ThreadState.Running.
- **Suspend()**: This method is used to either suspend the thread or if the thread is already suspended, have no effect.
- **Yield()**: This method causes the calling thread to yield execution to another thread that is ready to run on 
the current processor. The operating system selects the thread to yield to. It returns true if the operating 
system switched execution to another thread; otherwise, false.

## Thread Class Constructor
The Thread class in C# provides the following 4 constructors.

- **Thread(ThreadStart start)**: It initializes a new instance of the Thread class. Here, the parameter start 
specifies a ThreadStart delegate that represents the methods to be invoked when this thread begins executing. 
It will throw ArgumentNullException if the start parameter is null.
- **Thread(ParameterizedThreadStart start)**: It initializes a new instance of the Thread class, specifying a 
delegate that allows an object to be passed to the thread when the thread is started. Here, the parameter start 
specifies a delegate that represents the methods to be invoked when this thread begins executing. 
It will throw ArgumentNullException if the start parameter is null.
- **Thread(ThreadStart start, int maxStackSize)**: It initializes a new instance of the Thread class, 
specifying the maximum stack size for the thread. Here, the parameter start specifies a ThreadStart delegate 
that represents the methods to be invoked when this thread begins executing. And the parameter maxStackSize 
specifies the maximum stack size, in bytes, to be used by the thread, or 0 to use the default maximum stack 
size specified in the header for the executable. Important For partially trusted code, maxStackSize is
ignored if it is greater than the default stack size. No exception is thrown.
- **Thread(ParameterizedThreadStart start, int maxStackSize)**: It initializes a new instance of the Thread class,
specifying a delegate that allows an object to be passed to the thread when the thread is started and specifies 
the maximum stack size for the thread.

## Examples to Understand Constructors of the Thread Class in C#
In the following example, we are executing the `DisplayNumbers` function using a thread:

```c#
using System;
using System.Threading;

namespace ThreadingDemo
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Thread t1 = new Thread(DisplayNumbers);
            t1.Start();
        }

        static void DisplayNumbers()
        {
            for (int i  = 1; i <= 10; i++)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

As you can see in the above code, here, we created an instance of the Thread class and to the constructor of the 
Thread class, we passed the method name that we want the thread to execute.

### Constructors of the thread class

As discussed earlier, in C#, the Thread class contains four constructors. If you go to the definition of Thread class
then you will see the Constructors as shown below.

![Thread class constructors](multithreading-thread-class-constructors.png)

Now you may have one question, the Thread class constructor which takes one parameter is either of the type 
ThreadStart or ParameterizedThreadStart, but in our example, we are passing the method name as a parameter to the
Thread class Constructor, and it works, how?

If you go to the definition of `ThreadStart`, you will realize tha `ThreadStart` is just a delegate as shown in the 
image below.

![ThreadStart definition](multithreading-threadstart-definition.png)

### Why the constructor of the Thread class is taking a parameter of delegate type
As we already discussed, the main objective of creating a Thread in C# is to execute a function.

A delegate is a type-safe function pointer. It means the delegate points to a function and when we invoke the 
delegate, the function which is pointed by the delegate is going to be executed.

In simple words, we can say that all the threads that we create require an entry point (i.e. a pointer to a
function) from where it should execute. This is the reason why threads always require a delegate.

[You can learn more about delegates here](Delegates.md)

The signature of a delegate should always be the same as the signature of the method it points to.

As you can see, `ThreadStart` delegate does not take any parameters and the return type is void. In our example, 
the `DisplayNumbers()` function signature is the same as the `ThreadStart` delegate signature as the 
`DisplayNumbers()` function return type is void as well as it does not take any parameters.

Therefore, when we have:

```C#
Thread t1 = new Thread(DisplayNumbers);
```

The above instance creation statement is implicitly converted to the `ThreadStart` delegate instance. So you can write
the above statement as shown below and it will still work.

```C#
ThreadStart obj = new ThreadStart(DisplayNumbers);
Thread t1 = new Thread(obj);
```

As you can see in the above example, it is a two steps process. First, we need to create the ThreadStart 
Delegate Instance and while creating the instance, to its constructor we need to pass the method name that 
we want to execute. In the second step, to the Constructor of Thread class, we need to pass the ThreadStart 
instance as a parameter. And when we start the Thread execution by calling the Start method on the thread 
instance, internally it will invoke the ThreadStart delegate instance which internally start the 
execution of the DisplayNumbers method.

### Example to understand ThreadStart Delegate
In the below example, first, we are creating an instance of ThreadStart delegate and to the constructor of 
ThreadStart delegate, we pass the DisplayNumbers function as a parameter.

Then we create an instance of the Thread class and to the constructor of the Thread class, we pass the ThreadStart
delegate instance as a parameter that points to the DisplayNumbers function.

Finally, when we call the Start method on the Thread instance, which will invoke the ThreadStart delegate instance
and the delegate instance will invoke the method it points to i.e. the DisplayNumbers function is going to start 
its execution.

```C#
using System;
using System.Threading;

namespace ThreadingDemo2
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ThreadStart obj = new ThreadStart(DisplayNumbers);
            Thread t1 = new Thread(obj);
            t1.Start();
        }

        static void DisplayNumbers()
        {
            for (int i = 1; i <= 10; i++)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

You can also combine the two statements into one as shown:
```C#
Thread t1 = new Thread(new ThreadStart(DisplayNumbers));
```

### Creating a Thread Class Instance Using Anonymous Method
It is also possible to create a Thread class instance by using the anonymous method as shown in the below example.

We know that [Anonymous methods](Anonymouse-Methods.md) are created by using the delegate keyword, and they are
assigned to a type of delegate.

```C#
using System;
using System.Threading;

namespace ThreadingDemo3
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Thread t1 = new Thread(delegate()
            {
                for (int i = 1; i <= 10; i++)
                {
                    Console.WriteLine(i);
                }
            });
            t1.Start();
        }
    }
}
```

### Creating a Thread Class Instance Using Lambda Expression
It is also possible to create the thread class instance by using the lambda expression as shown in the below example. 

We know that Lambda Expressions are created by using the => Lambda Operator.

```C#
using System;
using System.Threading;

namespace ThreadingDemo4
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Thread t1 = new Thread(() =>
            {
                for (int i = 1; i <= 10; i++)
                {
                    Console.WriteLine(i);
                }
            });
            t1.Start();
        }
    }
}
```

### Thread Function With Parameter
The examples that we have worked on so far do not take any parameters. That is the method that we want to execute
by the custom thread that does not take any parameter.

Now, let us proceed and try to understand how to work with the thread function which takes the input parameter.

In the example below, DisplayNumbers() is taking one input parameter of object type. It then converts that object
type to an integer value and then print the numbers upto that value starting from 1.

```C#
using System;
using System.Threading;

namespace ThreadingDemo5
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Thread t1 = new Thread(DisplayNumbers);
            t1.Start(10);
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

When the thread method or thread function (the function which is going to be executed by the custom thread) takes
one parameter, then the Thread class uses the `ParameterizedThreadStart` delegate internally.

The definition of the `ParameterizedThreadStart` delegate in C# is shown in the below image.

![ParameterizedThreadStart definition](multithreading-parameterizedtthreadstart-definition.png)

As you can see the ParameterizedThreadStart delegate is taking one parameter of object type and like the ThreadStart 
delegate it also does not return any value.

You need to use the ParameterizedThreadStart delegate if your method takes any values else you just need to use 
the ThreadStart delegate which does not take any parameter.

### Problems With ParameterizedThreadStart delegate
As you can see, the parameter type of the ParameterizedThreadStart delegate is an object type. So, the parameter 
of the thread function is also going to be the object data type. And you cannot change the data type from object 
to any other type and if you try then it will give you a compile-time error.

**[IMPORTANT] As the thread function operates on object data type, so we can pass any type of value and it accepts.
As a result, the function is not going to be type-safe as we can pass any type of value.**

Again, as it operates on object data type, so boxing and unboxing will come into the picture, boxing and unboxing
degrades our application performance, so we should avoid object types.

