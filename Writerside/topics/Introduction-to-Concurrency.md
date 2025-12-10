# Introduction to Concurrency

Concurrency means doing several things at the same time. For example, if we have to do twenty tasks, 
then instead of doing them sequentially one by one, we can do them simultaneously, thus reducing the 
duration of the program execution.

Picture a restaurant with only one exhausted waiter doing everything, taking orders, serving food, clearing 
tables, so customers end up waiting forever because every task happens strictly one after another. Now imagine
the owner finally hires more waiters: suddenly multiple tasks can progress during the same time period, 
with different waiters handling different tables at once.

This concept of having a **Set of Tasks** and dividing them into several parts and those several parts that can 
be performed simultaneously is called <u>**Parallelism**</u>.

In our restaurant analog above, we were able to achieve parallelism by adding new waiters.

## How do we Achieve Parallelism in Programming?
In Programming, we can achieve Parallelism by using threads. A thread is a sequence of instructions that can be 
executed independently of other code.

Since they are independent within a process, so we can have several threads. And if our processor allows, 
then we can run several threads simultaneously. When we are executing multiple threads simultaneously, then
it is called multithreading. So, Parallelism uses multiple threads to perform multiple tasks simultaneously. 
Therefore, parallelism uses multithreading and multithreading is a form of concurrency.

However, there are other ways to do concurrency. We just talk about efficiency and we associate it with speed. 
Efficiency also has to do with Resource use. For example, if we have a web server, we want to serve as many 
web requests as we can concurrently. For that, we need to release threads when they are not in use. We can do 
this by using Asynchronous Programming.

Asynchronous Programming allows us to use threads efficiently and threads are prevented from being unnecessarily 
blocked.

## Introduction to Parallel Programming
Parallel Programming helps us to divide a task into different parts and execute those parts simultaneously. For 
example, if we have a set of images and we want to apply a series of filters to each image, we can do this by taking 
the advantage of Parallel Programming.

In C#, we can implement Parallel Programming in two ways. They are as follows:
- The Task Parallel Library (TPL)
- Parallel LINQ (PLINQ)

The Task Parallel Library is a library that makes life easier for us. When we see parallelism or Parallel 
Programming in our programs the TPL (Task Parallel Library) abstracts the low-level detail of thread handling i.e. 
how to create threads and how to execute the tasks using multiple threads is handled by the TPL. This allows us to 
concentrate on program logic rather than threads.

On the other hand, PLINQ or Parallel LINQ is an implementation of LINQ that allows us to work in parallel. 
For example, in LINQ, we can filter the elements of an array. Then with Parallel LINQ, we can filter the same array 
in parallel. This allows us to use the cores of our processor to perform the evaluations of the elements of the
array simultaneously.

There are two forms of parallelism:
- Data parallelism
- Task parallelism

In Data Parallelism, we have a collection of values and we want to use the same operation on each of the elements in
the collection. The examples will be to filter the elements of an array in parallel.

Task Parallelism occurs when we have a set of independent tasks that we want to perform in parallel. An example 
would be if we want to send an email and SMS to a user, we can perform both operations in parallel if they are
independent.

## Introduction to Asynchronous Programming
Asynchronous Programming allows us to handle the threads of our processes in a more efficient way. The idea is to 
avoid blocking a thread while waiting for a response, either from an external system such as a Web service or from 
the computer’s file management system.

To work with asynchronous programming in C# we use **async** and **await** keywords. The idea is that we need to use the 
**async** keyword to mark a method as asynchronous and with **await**, we can wait for an asynchronous operation in such 
a way that the original thread is not blocked.

The method which is marked with the **async** keyword must return a **Task** or **Task<T>**. The idea of a **Task**
is that it represents an asynchronous operation and does not return anything. In the case of **Task<T>**, it is like 
a promise that in the future this method will return a value of the data type **T**.

## CPU vs I/O Bound Operations
We have already discussed what asynchronous programming and parallel programming are, it is also important to understand
what kind of operations both are intended to improve.

In the case of Asynchronous Programming, we discussed that it has the specialty to handle IO-Bound operations 
where IO-bound operations are characterized by communication with external systems. Some examples of IO-bound 
operations are calls to a Web Service, interaction with a Database, interaction with a file system, etc. Therefore, 
when we need to perform such kinds of operations, we can consider the use of asynchronous programming to increase 
the level of scalability of our systems.

When we make a call to an external entity, we have to wait for a response and while waiting for the response, it 
is productive to free the thread that started the operation so that it can proceed to perform other tasks.

On the other hand, CPU-bound operations are those that are performed primarily using processor power. Here, 
there are usually no dependencies on external systems, everything depends on our system. If we have multiple CPU 
operations that are independent, we may want to use parallel programming to decrease the time it takes to perform 
these operations. Some examples of CPU operations are finding the inverse of a matrix, sorting the elements of 
an array, etc.

On the other hand, CPU-bound operations are those that are performed primarily using processor power. Here, 
there are usually no dependencies on external systems, everything depends on our system. If we have multiple 
CPU operations that are independent, we may want to use parallel programming to decrease the time it takes to 
perform these operations. Some examples of CPU operations are finding the inverse of a matrix, sorting the 
elements of an array, etc.