# Thread Synchronization Through Monitor Class

We can also protect shared resource using the monitor class in C#.

## Understanding the Monitor Class
Like the lock, we can also use this Monitor Class to protect the shared resources in a multi-threaded
environment from concurrent access.

The Monitor class is a static class belonging to the `System.Threading` namespace. As a static class, it provides
a collection of static methods, as shown in the image below. 

Using these static methods, we can provide synchronized access to the critical section associated with a
particular object.

![Monitor class](multithreading-monitor-class.png)

Following is a list of some of the important methods in the monitor class:
- **Enter()**: When we invoke the Enter method of the Monitor class, it acquires an exclusive lock on the
specified object. This also marks the beginning of a critical section or the beginning of a shared resource.
- **Exit()**: When the Monitor class’s Exit method is invoked, it releases the lock on the specified object. 
This marks the end of a critical section or the end of the shared resource protected by the locked object.
- **Pulse()**: When the Pulse method is invoked of the Monitor class, it sends a signal to a thread in the 
waiting queue of a change in the locked object’s state.
- **Wait()**: When the Monitor class’s Wait method is invoked, it releases the lock on an object and 
blocks the current thread until it reacquires the lock.
- **PulseAll()**: When the Monitor class’s PulseAll method is invoked, it sends signals to all waiting 
threads about a change in the locked object’s state.
- **TryEnter()**: When we invoke the Monitor class’s TryEnter method, it attempts to acquire an exclusive 
lock on the specified object.

## Example to understand Monitor Class in C# to Protect Shared Resource from Concurrent Access
The following is the syntax for using the Enter and Exit methods of the Monitor class to protect a shared resource in
a multithreaded environment from concurrent access in C#.

All the methods of the Monitor class are static. So, you can see here that we are accessing the Enter and Exit 
methods using the class name, i.e., Monitor.

![monitor syntax](multithreading-monitor-syntax.png)

Let us see an example to understand how to use the Monitor class Enter and Exit method to protect a shared resource
in a multithreaded environment in C# from concurrent access.

In the example below, we have one shared resource, and we are accessing that resource concurrently using three 
different threads. Then, we used the Monitor class Enter and Exit Methods to protect the critical section code. 
In this case, all three threads will try to acquire an exclusive lock, but at any given point in time, only one 
thread gets an exclusive lock and will enter into the critical section, and all other threads will wait until the 
thread releases the lock.

```C#
using System;
using System.Threading;

namespace MonitorClass
{
    internal class MonitorClass
    {
        static object lockPrintNumbers = new object();
        static void PrintNumbers()
        {
            Console.WriteLine($"{Thread.CurrentThread.Name} trying to enter the critical section");
            try
            {
                Monitor.Enter(lockPrintNumbers);
                Console.WriteLine($"{Thread.CurrentThread.Name} has entered the critical section");
                for (int i = 0; i < 10; i++)
                {
                    Console.Write($"{i} ");
                }
                Console.WriteLine();
            }
            finally
            {
                Monitor.Exit(lockPrintNumbers);
                Console.WriteLine($"{Thread.CurrentThread.Name} has exited from the critical section");
            }
        }

        static void Main(string[] args)
        {
            Thread t1 = new Thread(PrintNumbers)
            {
                Name = "Thread 1"
            };
            Thread t2 = new Thread(PrintNumbers)
            {
                Name = "Thread 2"
            };
            Thread t3 = new Thread(PrintNumbers)
            {
                Name = "Thread 3"
            };
            t1.Start();
            t2.Start();
            t3.Start();
        }
    }
}
```

![Output](multithreading-monitor-class-example-1-output.png)

## Monitor.Enter(lockObject, ref IslockTaken) Method
Let us understand the other overloaded version of the Enter method.

The Monitor.Enter(lockObject, ref IslockTaken) acquires an exclusive lock on the specified object. It then 
automatically sets a value that indicates whether the lock was taken or not.

The second parameter, which is a Boolean parameter, returns true if the lock is acquired; otherwise, it returns false.
The syntax for using this overloaded version is given below.

![Monitor overload syntax](multithreading-monitor-overload-syntax.png)

The following example shows how to use `Enter(lockObject, ref IslockTaken)` method of the Monitor class in C#.

The following example is the same as the previous example, except here, we are using the overloaded version of 
the Enter method, which takes two parameters. The second boolean parameter specifies whether the thread acquires a
lock or not, true indicates that it acquires a lock on the object and false indicates that it does not acquire a 
lock on the object and again in the finally block we are checking the boolean value and accordingly we are 
releasing the lock.

```C#
using System;
using System.Threading;

namespace MonitorClass
{
    internal class EnterOverload
    {
        static object lockPrintNumbers = new object();
        static void PrintNumbers()
        {
            bool isLockTaken = false;
            Console.WriteLine($"{Thread.CurrentThread.Name} trying to enter the critical section");
            try
            {
                Monitor.Enter(lockPrintNumbers, ref isLockTaken);
                Console.WriteLine(isLockTaken);
                if (isLockTaken )
                {
                    Console.WriteLine($"{Thread.CurrentThread.Name} has entered the critical section");
                    for (int i = 0; i < 10; i++)
                    {
                        Console.Write($"{i} ");
                    }
                    Console.WriteLine();
                }
            }
            finally
            {
                if (isLockTaken)
                {
                    Monitor.Exit(lockPrintNumbers);
                    Console.WriteLine($"{Thread.CurrentThread.Name} has exited from the critical section");
                }
            }
        }

        static void Main(string[] args)
        {
            Thread t1 = new Thread(PrintNumbers)
            {
                Name = "Thread 1"
            };
            Thread t2 = new Thread(PrintNumbers)
            {
                Name = "Thread 2"
            };
            Thread t3 = new Thread(PrintNumbers)
            {
                Name = "Thread 3"
            };
            t1.Start();
            t2.Start();
            t3.Start();
        }
    }
}
```

![Sample Output](multithreading-enter-overload-output.png)

## Example to Understand TryEnter(Object, TimeSpan, Boolean) Method of Monitor Class
This method attempts to acquire an exclusive lock on the specified object for a specified amount of time.

It automatically sets a value that indicates whether the lock was taken or not. The syntax for using the 
`TryEnter(Object, TimeSpan, Boolean)` Method of Monitor Class in C# is given below.

![TryEnter Syntax](multithreading-try-enter-syntax.png)

For a better understanding, please have a look at the example below, which shows how to use the 
`TryEnter(Object, TimeSpan, Boolean)` Method of the Monitor Class in C#. In the example below, we specified 
the timeout as 1000 milliseconds, or you can say 1 second. If the thread does not acquire the lock 
within 1 second, it will not enter the critical section.

```C#
using System;
using System.Threading;

namespace TryEnterDemo
{
    internal class MonitorClass
    {
        static object lockPrintNumbers = new object();
        static void PrintNumbers()
        {
            bool isLockTaken = false;
            TimeSpan timeout = TimeSpan.FromMilliseconds(1000);
            Console.WriteLine($"{Thread.CurrentThread.Name} trying to enter the critical section");
            try
            {
                Monitor.TryEnter(lockPrintNumbers, timeout, ref isLockTaken);
                if (isLockTaken )
                {
                    Console.WriteLine($"{Thread.CurrentThread.Name} has entered the critical section");
                    for (int i = 0; i < 10; i++)
                    {
                        Console.Write($"{i} ");
                    }
                    Console.WriteLine();
                }
                else
                {
                    Console.WriteLine($"{Thread.CurrentThread.Name} was denied entry into the critical section");
                }
            }
            finally
            {
                if ( isLockTaken )
                {
                    Monitor.Exit(lockPrintNumbers);
                    Console.WriteLine($"{Thread.CurrentThread.Name} has exited from the critical section");
                }
            }
        }

        static void Main(string[] args)
        {
            Thread t1 = new Thread(PrintNumbers)
            {
                Name = "Thread 1"
            };
            Thread t2 = new Thread(PrintNumbers)
            {
                Name = "Thread 2"
            };
            Thread t3 = new Thread(PrintNumbers)
            {
                Name = "Thread 3"
            };
            t1.Start();
            t2.Start();
            t3.Start();
        }
    }
}
```

![Example output](multithreading-try-enter-output.png)

## Example to Understand Wait() and Pulse() Methods of the Monitor Class
The Wait() Method of Monitor Class is used to Release the lock on an object in order to permit other threads 
to lock and access the object.

The Pulse signals are used to notify waiting threads about changes to a locked object’s state. 

Assuming we want to print even and odd numbers using two different threads, one thread will print even numbers, the
other will print odd numbers:
```
Thread T1: 0,2,4,6,8…
Thread T2: 1,3,5,7,9…
Output: 0,1,2,3,4,5,6,7,8,9…
```

In the following example, we use the Monitor.Wait() method to make the thread waiting and Monitor.Pulse() 
method is used to signal other threads. The process is as follows:
- First, the Even thread will start to print the number on the console.
- Then, the Even thread will signal the Odd thread to be ready to print the next number using the 
Monitor.Pulse() method.
- Then, the Event thread will call the Monitor.Wait() method, which will allow the current thread to block 
and the Odd thread to start execution.
- The Odd Thread will also do the same thing.
- The Odd thread will start to print the number on the console.
- Then, the Odd thread will signal the Even thread to be ready to print the next number using the
Monitor.Pulse() method.
- Then the Odd thread will call the Monitor.Wait() method, which will allow the current thread to block and 
allow the Even thread to start execution.

```C#
using System;
using System.Threading;

namespace MonitorClass
{
    internal class Program
    {
        const int numberLimit = 20;
        static readonly object _lockMonitor = new object();
        static void Main(string[] args)
        {
            Thread EvenThread = new Thread(PrintEvenNumbers);
            Thread OddThread = new Thread(PrintOddNumbers);

            EvenThread.Start();
            // Let's Pause for 10ms to guarantee that the even thread will always start first
            Thread.Sleep(100);
            OddThread.Start();

            // Main thread should wait for all the child threads to complete
            EvenThread.Join();
            OddThread.Join();
        }

        static void PrintEvenNumbers()
        {
            try
            {
                Monitor.Enter(_lockMonitor);
                for (int i = 0; i < numberLimit; i = i + 2)
                {
                    Console.Write($"{i} ");

                    // notify the odd thread to print the next number
                    Monitor.Pulse(_lockMonitor);

                    // it will wait here until the odd thread notifies it
                    if (i <= numberLimit)
                    {
                        // The thread will wait here till the odd thread notifies it
                        Monitor.Wait(_lockMonitor);
                    }
                }
            }
            finally
            {
                // Release the lock
                Monitor.Exit(_lockMonitor);
            }
        }

        static void PrintOddNumbers()
        {
            try
            {
                Monitor.Enter(_lockMonitor);
                for (int i = 1; i < numberLimit; i = i + 2)
                {
                    Console.Write($"{i} ");

                    // Notify the even thread to be ready to print the next number
                    Monitor.Pulse(_lockMonitor);

                    if (i < numberLimit - 1)
                    {
                        Monitor.Wait(_lockMonitor);
                    }
                }
            }
            finally
            {
                Monitor.Exit(_lockMonitor);
            }
        }
    }
}

```