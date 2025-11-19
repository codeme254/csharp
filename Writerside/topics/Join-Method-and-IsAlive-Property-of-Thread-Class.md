# Join Method and IsAlive Property of Thread Class

## Join Method of the Thread Class
In the below example we have created three methods and then execute these three methods using three different threads.

The point that you need to remember is the threads thread1, thread2, and thread3 are called the child threads of
the main thread. This is because these three threads are created by the main thread only.

Here, thread1 executes Method1, thread2 executes Method2, and thread3 executes Method3. Further, if you notice, 
we have delayed the execution of Method1 by 3 seconds, Method2 execution by 2 seconds, and Method3 execution by 
5 seconds using the Thread class static Sleep method which takes the time in milliseconds and will make the 
current thread sleep for that millisecond. 

Here, we are using the overloaded version of the Thread class 
constructor which takes the ThreadStart delegate as a parameter.

```C#
using System;
using System.Threading;

namespace JoinAndIsAlive
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Main Thread Started");
            Thread thread1 = new Thread(Method1);
            Thread thread2 = new Thread(Method2);
            Thread thread3 = new Thread(Method3);

            thread1.Start();
            thread2.Start();
            thread3.Start();

            Console.WriteLine("Main Thread Ended");
        }
        
        static void Method1()
        {
            Console.WriteLine("Method1 - thread1 started");
            Thread.Sleep(3000);
            Console.WriteLine("Method1 - thread1 ended");
        }

        static void Method2()
        {
            Console.WriteLine("Method2 - thread2 started");
            Thread.Sleep(2000);
            Console.WriteLine("Method2 - thread2 ended");
        }

        static void Method3()
        {
            Console.WriteLine("Method3 - thread3 started");
            Thread.Sleep(5000);
            Console.WriteLine("Method3 - thread3 ended");
        }
    }
}
```

![Output](multithreading-join-output.png)

As you can see from the above output, the Main thread is not waiting for all the child threads to complete their
execution or task. If you want the Main thread should not be exited until and unless all the child thread or any 
of the child threads completes their task then you need to use the Join method of the Thread class

### Join Method
The Join Method of the Thread Class in C# blocks the current thread and makes it wait until the child thread
on which the Join method invoked completes its execution.

There are three overloaded versions available for the Join Method in Thread class as shown below.

![Join Method Overloads](multithreading-join-method-overloads.png)

- **Join()**: block the calling thread (i.e. the Parent thread) until the thread (child thread) completes 
its execution. In this case, the calling thread is going to wait for an indefinite time until the thread on which 
the Join Method is invoked is completed.
- **Join(int milliSecondsTimeout)**: block the calling thread until the child thread terminates or the 
specified time elapses. This overload takes time in milliseconds. This method returns true if the thread 
has terminated and returns false if the thread has not terminated after the amount of time specified by 
the `millisecondsTimeout` parameter has elapsed.
- **Join(Timespan timeout)**:  here we need to use TimeSpan to set the amount of time to wait for the thread to 
terminate.

### Examples to Understand the Join Method
In the below example, we have called the Join method on all three threads which means it will block the main 
thread until all the child threads complete their tasks.

```C#
using System;
using System.Threading;

namespace JoinAndIsAlive
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Main Thread Started");
            Thread thread1 = new Thread(Method1);
            Thread thread2 = new Thread(Method2);
            Thread thread3 = new Thread(Method3);

            thread1.Start();
            thread2.Start();
            thread3.Start();

            thread1.Join();
            thread2.Join();
            thread3.Join();

            Console.WriteLine("Main Thread Ended");
        }
        
        static void Method1()
        {
            Console.WriteLine("Method1 - thread1 started");
            Thread.Sleep(3000);
            Console.WriteLine("Method1 - thread1 ended");
        }

        static void Method2()
        {
            Console.WriteLine("Method2 - thread2 started");
            Thread.Sleep(2000);
            Console.WriteLine("Method2 - thread2 ended");
        }

        static void Method3()
        {
            Console.WriteLine("Method3 - thread3 started");
            Thread.Sleep(5000);
            Console.WriteLine("Method3 - thread3 ended");
        }
    }
}
```

Run the above code, and you will see that the Main thread is started first and will wait until all the child 
threads complete their execution as shown in the below output.

![Output](multithreading-join-output-2.png)

Now, for example, if you don’t want the main thread to wait until thread3 completes its execution. 
Then you just need to call the Join method on thread1 and thread2

#### Other Overloaded Versions of the Thread Class Join Method
You need to use the second and third overloaded version of the Thread Class Join Method in C# when you want the 
main thread to wait for a specified amount of time.

For example, you want the main thread to wait for 3 seconds for thread2 and thread3 to complete their task. Then 
you need to use the Join method as shown below in the below example. Remember the overloaded versions which take
time in milliseconds and TimeSpan returns a boolean value indicating whether the thread completes its execution or 
not. Boolean true means method execution completed and false means method execution not completed.

```C#
using System;
using System.Threading;

namespace JoinAndIsAlive2
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Main Thread Started");
            Thread thread1 = new Thread(Method1);
            Thread thread2 = new Thread(Method2);
            Thread thread3 = new Thread(Method3);

            thread1.Start();
            thread2.Start();
            thread3.Start();

            // Main thread will wait for 3 seconds and wait thread2 to complete its execution
            if (thread2.Join(TimeSpan.FromSeconds(3)))
            {
                Console.WriteLine("Thread 2 Execution Completed in 3 Seconds");
            } else
            {
                Console.WriteLine("Thread 2 execution not completed in 3 seconds");
            }

            if (thread3.Join(3000))
            {
                Console.WriteLine("Thread 3 completed execution in 3 seconds");
            } else
            {
                Console.WriteLine("Thread 3 did not complete execution in 3 seconds");
            }
                Console.WriteLine("Main Thread Ended");
        }

        static void Method1()
        {
            Console.WriteLine("Method1 - thread1 started");
            Thread.Sleep(3000);
            Console.WriteLine("Method1 - thread1 ended");
        }

        static void Method2()
        {
            Console.WriteLine("Method2 - thread2 started");
            Thread.Sleep(2000);
            Console.WriteLine("Method2 - thread2 ended");
        }

        static void Method3()
        {
            Console.WriteLine("Method3 - thread3 started");
            Thread.Sleep(5000);
            Console.WriteLine("Method3 - thread3 ended");
        }
    }
}
```
In the above example, main thread will be blocked for only 3 seconds after which it will be allowed to continue with
execution and finish.

## IsAlive Property of Thread Class
The IsAlive property gets a value indicating the execution status of the current thread. It returns true if
the thread has been started and has not terminated normally or aborted; otherwise, false.

That means the IsAlive property of the Thread class returns true if the thread is still executing else returns false.

```C#
using System;
using System.Threading;

namespace IsAlive
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Main Thread Started");
            Thread thread1 = new Thread(Method1);
            thread1.Start();

            if (thread1.IsAlive)
            {
                Console.WriteLine("Thread1 Method1 is still executing");
            } else
            {
                Console.WriteLine("Thread1 Method1 completed its work");
            }

            // Making the main thread to wait till thread1 has finished
            // to visualize IsAlive being false
            thread1.Join();
            if (thread1.IsAlive)
            {
                Console.WriteLine("Thread1 Method1 is still executing");
            }
            else
            {
                Console.WriteLine("Thread1 Method1 completed its work");
            }
            Console.WriteLine("Main Thread Ended");
        }

        static void Method1()
        {
            Console.WriteLine("Method1 - Thread1 Started");
            Thread.Sleep(2000);
            Console.WriteLine("Method1 - Thread1 Ended");
        }
    }
}
```

![Output](multithreading-isalive-output.png)