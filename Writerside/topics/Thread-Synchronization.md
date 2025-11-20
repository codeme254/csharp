# Thread Synchronization

Data inconsistency occurs when more than one threads access a shared resource such as in-memory data 
(instance or class variables) and external objects such as files at the same time.

Consider that we have two threads Thread1 and Thread2, and both the threads access a shared resource let’s say
Resource1 simultaneously. If Thread1 is trying to read data from the shared resource Resource1 when Thread2 is 
attempting to write data onto the shared resource Resource1, then there would be data inconsistency. Hence, 
in situations like this thread synchronization comes into the picture.

Synchronization in C# language is a process that allows access to shared resources smoothly. Synchronization 
in C# ensures that only one thread is accessing the shared resource at any given point in time, preventing
other threads from doing the same at the same time.

Thread Synchronization in C# is a mechanism that is used to restrict multiple threads from accessing a shared 
resource at the same time. In simple words, we can also say that thread synchronization can help us to prevent 
multiple threads from gaining access to a shared resource simultaneously. As a result, we can have one and only 
one thread entering a critical section to access the shared resource at any given point in time.

## How Thread Synchronization is Achieved in C#
We can achieve thread synchronization in C# through one of the following ways:
- Lock
- Monitor
- Mutex
- Semaphore
- Semaphore Slim

In this section, we will discuss the **Lock** mechanism and then we will discuss the other mechanism in future sections.

## Thread Synchronization With the Lock Mechanism
Synchronization in C# can be achieved in multiple ways. One of the ways to achieve Synchronization in C# is by
using the feature of lock, which locks the access to a block of code within the locked object.

When a thread locks an object, no other thread can access the block of code within the locked object.

Only when a thread releases the lock, then it is available for other threads to access it.

In C# Language, every object has a built-in lock. By using the feature of Synchronization, we can lock an object.
Locking an object can be done by using the lock keyword, and the following is the syntax to use the lock.

```C#
lock(object)
{
    // code here
}
```

So, when a thread acquires a lock over an object, then that particular thread can only access the block of 
statements within the locked object. Now, all the other threads wishing to access the same block of statements 
within the same locked object will have to wait until, the thread that has got the lock on the object, 
releases the lock, by exiting the block of statements.


## Example Without Thread Synchronization

In the below example, we are creating three different threads that are going to access the same 
resource i.e. in this case the shared resource is `SomeMethod`.

As you can see, we have delayed the `SomeMethod` execution by 1 second, and all three threads trying to 
execute the same method, and they will execute it.

The first thread which executes the method does not get its sole access, this thread executes the method for a 
while and after some time, other threads will come and execute the same method. So, here, we will not get the 
output as expected.

```C#
using System;
using System.Threading;

namespace WithoutSynchronization
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Thread t1 = new Thread(SomeMethod);
            Thread t2 = new Thread(SomeMethod);
            Thread t3 = new Thread(SomeMethod);
            t1.Start();
            t2.Start();
            t3.Start();
        }

        static void SomeMethod()
        {
            Console.Write("[Welcome to the");
            Thread.Sleep(1000);
            Console.WriteLine("world of C#]");
        }
    }
}
```

When we run the code above, we will get the following output, the output might vary on your machine:

![Output](multithreading-without-synchronization-output.png)

As you can see in the above output, here we are not getting the output as expected. So, the point that you need 
to keep in mind is that if the shared resource is not protected in a multithreaded environment from concurrent 
access, then the output or the behavior of the application becomes inconsistent and highly unpredictable.

## Example Using Thread Synchronization
In the below example, we are creating three threads that are going to access the SomeMethod, but this time access 
to SomeMethod will be synchronized because we are going to use the lock, to lock the object within which the method 
is going to be accessed by multiple threads.

The first thread to enter the method gets its sole access until it exits the method, thereby avoiding the collision 
between multiple threads trying to access a method.

```C#
using System;
using System.Threading;

namespace WithSynchronization
{
    internal class Program
    {
        static object lockObject = new object();
        static void Main(string[] args)
        {
            Thread t1 = new Thread(SomeMethod);
            Thread t2 = new Thread(SomeMethod);
            Thread t3 = new Thread(SomeMethod);
            t1.Start();
            t2.Start();
            t3.Start();
        }

        static void SomeMethod()
        {
            lock (lockObject)
            {
                Console.Write("[Welcome to the");
                Thread.Sleep(1000);
                Console.WriteLine("world of C#]");
            }
        }
    }
}
```

![With Synchronization](multithreading-with-synchronization-output.png)

## Exclusive vs Non-Exclusive Lock
When a process or a thread wants to access an object, it requests a lock on that object.

There are two locks that determine access to a shared resource:
- **Exclusive lock**: An exclusive lock makes sure that only one thread can gain access or enter a critical 
section at any given point in time. In C#, we can implement Exclusive Lock using the 
**lock keyword, Monitor class, Mutex Class, and SpinLock class.**
- **Non-Exclusive lock**: Non-Exclusive locks provide read-only access to a shared resource and limit concurrency, 
i.e., limit the number of concurrent accesses to a shared resource. In C#, we can implement Non-Exclusive 
Lock using the **Semaphore, SemaphoreSlim, and ReaderWriterLockSlim classes.**