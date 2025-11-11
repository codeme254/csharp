# Multithreading

## What is Multitasking
Multitasking means performing multiple tasks simultaneously.

Windows operating system for example is a multitasking operating system for example, which means it has the ability to
run multiple applications at the same time: you can run a browser, a media player, a word editing software, a code
editing software at the same time.

**Multitasking refers to the concurrent execution of multiple tasks or processes on a computer system.**

It allows a computer to appear as though it is performing multiple tasks simultaneously, even though it typically
has a single central processing unit (CPU).

## How an operating system is able to execute multiple applications at a time.

The operating system uses processes internally to execute multiple applications (Google Chrome Browser,
Microsoft Word Document, Notepad, VLC Media Player, Visual Studio, etc.) simultaneously.

### What is a process
**A process is an instance of a program in execution.**

In an operating system (OS), a process is a fundamental concept representing a program in execution.

It is the smallest unit of work in a computer system's execution.

It is created and managed by the operating system.

Every time a program or application is executed, the operating system creates a process for it.

![Processes on task manager](multithreading-processes-task-manager.png)

As you can see in the above image, each application is executed by one corresponding process.

**To execute the code of an application, a process contains one or more threads. These threads 
are responsible for running the actual instructions/code of the program.**

### What is a Thread
A thread is the smallest unit of execution within a process.

When a process starts, the operating system creates at least one thread, called the main thread, which begins 
executing the program’s instructions. That thread can then create additional threads if your program supports 
concurrent or parallel tasks.

Threads are sometimes called **lightweight processes** because they share the same memory space as the parent 
process, including its code, data, and resources.

**By default, every process has at least one thread that is responsible for executing the application code, and that 
thread is called Main Thread.** So, every application by default is a single-threaded application.

Threads have their own execution context, including a program counter, registers, and stack. 
Threads within the same process can run concurrently, allowing for parallel execution of tasks.

## Example of Threading in C#
The following is a simple program where we have a class called Program, and in that class, we have a method
called Main, which simply prints a message on the Console window.

```C#
using System;

namespace ThreadingDemo
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```

The above program makes use of a thread, which is what will execute our application code, this default thread is called
the **main thread**.

To prove this, put a debugger on your application code as shown below and run the application:
- On any line where you want the program to pause, click in the gray bar (left margin) next to that line.
- You will see a red dot appear, that's your breakpoint.
- Run the program in debug mode: press <kbd>F5</kbd> or click the green "start debugging" button.
- When the program hits that line, execution stops so that you can inspect variables, step through the code. e.t.c.

![Adding a debugger](multithreading-threading-example-adding-debugger.png)

Once the debugger hits the debugging point, select the **Debug => Windows => Threads** options from the Visual 
Studio menu, as shown in the below image.

![Selecting Debug => Windows => Threads](multithreading-threading-example-selecting-debugger-windows-thread-option.png)

Once you select the Debug => Windows => Threads options, then it will open the following window. You can see here 
that the Main Thread is currently executing the Main method of the Program class.

![The main thread](multithreading-main-thread.png)

So, this proves that by default, every application is a single-threaded application, and by default, the Main 
thread will execute our application code.

## Thread Class in C#
In the thread class of C# (More about it later), there's one static property called **CurrentThread**, which returns
the instance of the currently executing thread, i.e., the thread running your application code.

There is also a non-static property called **Name**, using which we can set and get the name of the currently
executing thread.

By default, the thread does not have any name. You can provide any name to the thread using the Name property of
the Thread class.

All the threading-related classes in C# belong to **System.Threading** namespace. 

```C#
using System;
using System.Threading;

namespace ThreadingDemo
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Thread t = Thread.CurrentThread;
            t.Name = "Main Thread";
            Console.WriteLine($"Current executing thread name: {t.Name}");
            Console.WriteLine($"Current executing thread name: {Thread.CurrentThread.Name}");
        }
    }
}
```

![Changing the name of a thread](multithreading-changing-a-thread-name.png)

## Drawbacks of single-threaded applications in the .NET framework
- **Limited CPU Utilization**: Single-threaded applications can only execute one task or operation simultaneously. 
This means they cannot fully utilize modern multi-core processors, leading to the underutilization of available CPU 
resources. In contrast, multi-threaded or parallel applications can distribute work across multiple threads and 
utilize more CPU cores efficiently.
- **Poor Responsiveness**: In a single-threaded application, time-consuming operations can block the entire 
execution, making the application appear unresponsive to user input. For example, if a long-running computation 
occurs on the main thread, the user interface won’t update until the computation is complete. This can result
in a poor user experience.
- **Difficulty handling concurrent tasks**: Single-threaded applications struggle to handle concurrent tasks, such as 
responding to user input, while performing background tasks like data loading or computation. The application may 
become unresponsive during such operations without additional threads or asynchronous programming techniques.
- **Scalability challenges**: Single-threaded applications often face challenges when scaling to simultaneously 
handle multiple users or workloads. They may not be well-suited for scenarios requiring high concurrency or 
parallel processing, such as web servers or real-time data processing applications.
- **Limited parallelism**: Single-threaded applications cannot perform true parallel processing. This can be a 
significant drawback when dealing with computationally intensive tasks that can benefit from parallelism, 
such as data analysis, rendering, or simulations.

To address these limitations, developers often use **multi-threading**, **asynchronous programming**, or 
**parallel processing** techniques provided by the .NET Framework to make applications more responsive, 
scalable, and efficient.

## Example to understand the problem with single-threaded applications in C#
In the example below, we have 3 simple methods that print values 1 to 5.

We are using the Thread sleep class to delay the execution of `Method2` for 10 seconds.

The Sleep method of the Thread class takes a time in milliseconds as input and suspends the current thread execution
for that specified number of milliseconds.

```C#
using System;
using System.Threading;

namespace Threading
{
    internal class Example2
    {
        static void Main(string[] args)
        {
            Method1();
            Method2();
            Method3();
        }
        static void Method1()
        {
            for (int i = 0; i < 5; i++)
            {
                Console.WriteLine($"Method 1: {i}");
            }
        }

        static void Method2()
        {
            for (int i = 0; i < 5; i++)
            {
                if (i == 3)
                {
                    Console.WriteLine("Fake database operation started");
                    Thread.Sleep(10000);
                    Console.WriteLine("Fake database operatin completed");
                }
                Console.WriteLine($"Method 2: {i}");
            }
        }

        static void Method3()
        {
            for (int i = 0; i < 5; i++)
            {
                Console.WriteLine($"Method 3: {i}");
            }
        }
    }
}
```

Now, run the application and notice that the Method2 execution is delayed for 10 seconds. Once Method2 completes 
its execution only then will method3 start its execution. This is because all three methods are executed by a single 
thread, which is the drawback of the single-threaded application.

### Solving the above problem
To solve the above problem, we have a concept called Multithreading in C#. As we already discussed Operating System 
has Processes used to run our applications. The Process contains Thread, which will actually run our application code.

A process, by default, uses a single thread to run our application code, but a process can have multiple threads, 
and multiple threads can run our application code simultaneously. In this case, each thread will perform a different 
task, or you can say each thread will execute different parts of our application code.

In our application, we have three methods. So, the three methods we defined in our application can be executed by 
three threads. The advantage is that the execution takes place simultaneously. So, when multiple threads try to 
execute the application code, the operating system allocates some time for each thread.

In our example, we want to execute the three methods using three different threads. let us say t1, t2, and t3. The
thread t1 is going to execute Method1, and thread t2 is going to execute the Method2. At the same time, Method3 
will be executed by thread t3.

```C#
using System;
using System.Threading;

namespace Threading
{
    internal class Example3
    {
        static void Main(string[] args)
        {
            Thread t1 = new Thread(Method1)
            {
                Name = "Thread for method 1"
            };
            Thread t2 = new Thread(Method2)
            {
                Name = "Thread for method 2"
            };
            Thread t3 = new Thread(Method3)
            {
                Name = "Thread for method 3"
            };
            t1.Start();
            t2.Start();
            t3.Start();
        }
        static void Method1()
        {
            Console.WriteLine($"Method 1 started using {Thread.CurrentThread.Name}");
            for (int i = 0; i < 5; i++)
            {
                Console.WriteLine($"Method 1: {i}");
            }
            Console.WriteLine($"Method 1 ended using {Thread.CurrentThread.Name}");
        }

        static void Method2()
        {
            Console.WriteLine($"Method 2 started using {Thread.CurrentThread.Name}");
            for (int i = 0; i < 5; i++)
            {
                if (i == 3)
                {
                    Console.WriteLine("Fake database operation started");
                    Thread.Sleep(10000);
                    Console.WriteLine("Fake database operatin completed");
                }
                Console.WriteLine($"Method 2: {i}");
            }
            Console.WriteLine($"Method 2 ended using {Thread.CurrentThread.Name}");
        }

        static void Method3()
        {
            Console.WriteLine($"Method 3 started using {Thread.CurrentThread.Name}");
            for (int i = 0; i < 5; i++)
            {
                Console.WriteLine($"Method 3: {i}");
            }
            Console.WriteLine($"Method 3 ended using {Thread.CurrentThread.Name}");
        }
    }
}
```

As you can see in the above code, we have created three different instances of the Thread class. To the constructor 
of the Thread class, we need to pass the method name that needs to be executed by that Thread. Then, we call the 
`Start()` method on the Thread class, which will start executing the method. You will not get the output 
sequentially. Run the application and see the output as shown below. The output may vary in your machine.

![Output](multithreading-threads-output.png)

Here, the Main thread is going to create all other Threads. Here, the main thread will execute the Main method, 
and the Main thread will create the child threads called **Worker Threads**.

If we inspect the threads, we will see the following:

![Main thread and worker threads](multithreading-worker-threads.png)

## So What is Multithreading
If multiple threads are used to execute your application code, it is called **Multithreading**.

Multithreading is a mechanism to implement Concurrent Programming where multiple threads operate simultaneously.

Thread usage increases the efficiency of an application and reduces CPU cycle time wastage. The main advantage 
of using Multithreading is the maximum utilization of CPU resources.

Threads are lightweight, independent sequences of instructions that can run concurrently, allowing you to 
perform multiple tasks simultaneously.

Multithreading can greatly enhance the performance and responsiveness of C# applications, but it also introduces 
complexities related to synchronization, coordination, and potential issues like deadlocks. Therefore, it’s 
essential to use multithreading judiciously and follow best practices to ensure robust and reliable concurrent code.
