# Non-Generic Queue Collection

The Non-Generic Queue Collection Class in C# represents a First-In, First-Out collection of objects.

That means we need to use this collection when we need First-In, First-Out access to items of a collection.

When we add an item to the queue, then it is called **enqueuing** an item. Similarly, when we remove an 
item from the queue then it is called **dequeuing** an item.

Imagine a queue of people waiting for a ticket in a cinema hall. Normally, the first person who enters the 
queue will be the first person to get the ticket from the counter. Similarly, the last person who enters the 
queue will be the last person to get the ticket from the counter.

![Queue](collections-queue.png)

Note: Queue is defined as both Generic and Non-Generic types of Collections in C#. The Generic Queue Collection 
is defined in `System.Collections.Generic` namespace whereas Non-Generic Queue Collection is defined under 
`System.Collections` namespace.

In this section, we will be discussing the Non-Generic Queue Collection class in C#.

## Characteristics of Non-Generic Queue Collection Class
1. The Enqueue method adds an element to the end of the Queue.
2. The Dequeue method removes the oldest element from the start of the Queue.
3. The Peek method returns the oldest element that is at the start of the Queue but does not remove it from the Queue.
4. The capacity of a Queue is the number of elements the queue can hold. As we add elements to a queue, 
the capacity of the queue is automatically increased.
5. The Non-Generic Queue Collection allows both null and duplicate values.

## Methods, Properties, and Constructor of Non-Generic Queue Collection Class in C#
If you go to the definition of Queue Collection Class in C#, then you will see the following signature.

![Queue Class](collections-queue-definition.png)

## How to Create a Queue
The non-generic Queue collection class in C# has provided four constructors which we can use to create a queue. 

The constructors are as follows:
1. **Queue()**: It is used to initialize a new instance of the Queue class that is empty and has the default 
initial capacity, and uses the default growth factor.
2. **Queue(ICollection col)**: It is used to initialize a new instance of the Queue class that contains elements
copied from the specified collection and has the same initial capacity as the number of elements copied and uses 
the default growth factor. Here, the parameters col specifies the System.Collections.ICollection to copy elements from.
3. **Queue(int capacity)**: It is used to initialize a new instance of the Queue class that is empty, has the specified
initial capacity, and uses the default growth factor. Here, the parameter capacity specifies the initial number 
of elements that the Queue can contain.
4. **Queue(int capacity, float growFactor)**: It is used to initialize a new instance of the Queue class that is 
empty, has the specified initial capacity, and uses the specified growth factor. Here, the parameter capacity 
specifies the initial number of elements that the Queue can contain and the parameter growFactor specifies the factor
by which the capacity of the Queue is expanded.

Let's use the overload that doesn't take any parameter:

```C#
using System;
using System.Collections;

namespace QueueCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Queue q = new Queue();
        }
    }
}
```

## How to Add Elements into a Queue
If we want to add elements to a queue, then we need to use the `Enqueue()` method of the Queue class.

It takes in one parameter - the item that we want to add to the queue.

```C#
using System;
using System.Collections;

namespace QueueCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Queue q = new Queue();

            q.Enqueue(101);
            q.Enqueue("Hello");
            q.Enqueue(3.142f);
            q.Enqueue(false);
            q.Enqueue('A');

            foreach (var item in q)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

## How to Remove Elements From the Queue Collection
In Queue, you are allowed to remove elements from the beginning of the Queue. If you want to remove elements from the 
queue, then you need to use the following two methods provided by the Non-Generic Collection Queue class.
- `Dequeue()`: This method is used to remove and return the object at the beginning of the Queue. It returns the 
object that is removed from the beginning of the Queue.
- `Clear()`: This method is used to remove all objects from the queue.

```C#
using System;
using System.Collections;

namespace QueueCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Queue q = new Queue();

            q.Enqueue(101);
            q.Enqueue("Hello");
            q.Enqueue(3.142f);
            q.Enqueue(false);
            q.Enqueue('A');

            q.Dequeue();
            q.Dequeue();

            foreach (var item in q)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

## How to Get the First Element of the Queue Collection
The Non-Generic Queue Collection class in C# provides the following two methods to get the first element of
the queue collection

- `Dequeue()`: The Dequeue() method of the Queue class is used to Remove and return the object from the beginning 
of the Queue. If there is no object (or element) present in the Queue and if we are trying to remove an item or 
object from the Queue using the `Dequeue()` method then it will throw an exception i.e. 
`System.InvalidOperationException`.
- `Peek()`: The peek() method of the Queue class is used to return the oldest object i.e. the object present at 
the start of the Queue without removing it. If there is no object (or element) present in the Queue and if we are 
trying to return an item (object) from the Queue using the `Peek()` method then it will throw an exception i.e. 
System.InvalidOperationException

```C#
using System;
using System.Collections;

namespace QueueCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Queue q = new Queue();

            q.Enqueue(101);
            q.Enqueue("Hello");
            q.Enqueue(3.142f);
            q.Enqueue(false);
            q.Enqueue('A');

            Console.WriteLine($"First element: {q.Dequeue()}"); // 101
            Console.WriteLine($"First element: {q.Peek()}"); // "Hello"

            foreach (var item in q)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

Note: If you want to remove and return the first element from the queue, then use the Dequeue method and if you 
only want to return the first element from the queue without removing it, then use the Peek method and this is the 
only difference between these two methods of Queue Collection Class in C#.

## How to Check Whether an Element Exists
If you want to check whether an element exists or not in the queue collection, then you need to use the `Contains()`
method.

The method is used to determine whether an element is in the Queue.

It takes in one parameter, the element to locate in the queue.

It returns true if the element is found in the queue, otherwise it returns false.

```C#
using System;
using System.Collections;

namespace QueueCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Queue q = new Queue();

            q.Enqueue(101);
            q.Enqueue("Hello");
            q.Enqueue(3.142f);
            q.Enqueue(false);
            q.Enqueue('A');

            //q.Dequeue();
            //q.Dequeue();

            Console.WriteLine($"First element: {q.Dequeue()}"); // 101
            Console.WriteLine($"First element: {q.Peek()}"); // "Hello"

            Console.WriteLine(q.Contains("Hello")); // True
            Console.WriteLine(q.Contains("World")); // False

            foreach (var item in q)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```