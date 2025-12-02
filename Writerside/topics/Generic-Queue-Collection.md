# Generic Queue Collection

The Generic Queue in C# is a collection class that works on the principle of First In First Out (FIFO) and 
this class is present in System.Collections.Generic namespace. That means we need to go for Generic Queue Collection 
when we need First In First Out (FIFO) access to items.

When we add an element into the queue, it is called **Enqueueing** the element and when we remove an 
element from the queue, it is called **Dequeueing** the element.

## How to Create a Generic `Queue<T>` Collection 

We can use one of the following constructors to create an instance of the generic queue class:
1. **Queue()**: It is used to initialize a new instance of the Generic Queue class that is empty and has the default 
initial capacity.
2. **Queue(`IEnumerable<T>` collection)**: It is used to initialize a new instance of the Generic Queue class that 
contains elements copied from the specified collection and has sufficient capacity to accommodate the number of 
elements copied. Here, the parameters collection specifies the collection whose elements are copied to the new 
Generic Queue. If the collection is null, then it will throw ArgumentNullException.
3. **Queue(int capacity)**: It is used to initialize a new instance of the Generic Queue class that is empty and
has the specified initial capacity. Here, the parameter capacity specifies the initial number of elements that
the Queue can contain. If capacity is less than zero, then it will throw ArgumentOutOfRangeException.

In the example below, we are using the overload that does not take any parameters:

```C#
using System;
using System.Collections.Generic;

namespace QueueCollection
{
    internal class QueueCollection
    {
        static void Main(string[] args)
        {
            Queue<int> queue = new Queue<int>();
        }
    }
}
```

## How to Add Elements Into a Queue Collection
If you want to add elements to a generic queue collection in C#, then you need to use the
`Enqueue()` method of the `Queue<T>` class.

The Enqueue(T item) method is used to add an element at the end of the queue. Here, the parameter item specifies 
the element to add to the queue. The value can be null for a reference type i.e. when T is a reference type.


```C#
using System;
using System.Collections.Generic;

namespace QueueCollection
{
    internal class QueueCollection
    {
        static void Main(string[] args)
        {
            Queue<int> queue = new Queue<int>();
            queue.Enqueue(10);
            queue.Enqueue(20);
            queue.Enqueue(30);
            queue.Enqueue(40);
            queue.Enqueue(50);
        }
    }
}
```

## How to Access a Generic Queue Collection
We can access all the elements of the Generic Queue collection in C# using a for each loop as follows.

```C#
using System;
using System.Collections.Generic;

namespace QueueCollection
{
    internal class QueueCollection
    {
        static void Main(string[] args)
        {
            Queue<int> queue = new Queue<int>();
            queue.Enqueue(10);
            queue.Enqueue(20);
            queue.Enqueue(30);
            queue.Enqueue(40);
            queue.Enqueue(50);

            foreach(int item in queue)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

## How to Remove Elements from a Generic `Queue<T>` Collection
You can use one of the following methods to remove an elements from a generic queue collection:

1. `Dequeue()`: This method is used to remove and return the object at the beginning of the Generic Queue. 
It returns the Object (element) removed from the beginning of the Generic Queue. If the Queue is empty, 
then it will throw InvalidOperationException.
2. `Clear()`: This method is used to remove all objects from the Generic Queue.

```C#
using System;
using System.Collections.Generic;

namespace QueueCollection
{
    internal class QueueCollection
    {
        static void Main(string[] args)
        {
            Queue<int> queue = new Queue<int>();
            queue.Enqueue(10);
            queue.Enqueue(20);
            queue.Enqueue(30);
            queue.Enqueue(40);
            queue.Enqueue(50);

            queue.Dequeue();
            // queue.Clear()
        }
    }
}
```

## How to Get the First Element From a Generic Queue
The Generic `Queue<T>` Collection Class in C# provides the following two methods to get the first element of the 
queue collection:
1. **Dequeue()**: The Dequeue() method of the Queue class is used to Remove and return the object from the 
beginning of the Queue. That means it returns the object that is removed from the beginning of the Generic Queue. 
If the queue is empty, it will throw InvalidOperationException
2. **Peek()**: The peek() method of the Queue class is used to return the object at the beginning of the Queue 
without removing it. That means it returns the object from the beginning of the Queue. If the queue is empty, 
then it will throw InvalidOperationException.

```C#
using System;
using System.Collections.Generic;

namespace QueueCollection
{
    internal class QueueCollection
    {
        static void Main(string[] args)
        {
            Queue<int> queue = new Queue<int>();
            queue.Enqueue(10);
            queue.Enqueue(20);
            queue.Enqueue(30);
            queue.Enqueue(40);
            queue.Enqueue(50);
            
            Console.WriteLine(queue.Peek()); // 10
        }
    }
}
```

## How to check whether an Element Exists or Not in the Generic `Queue<T>` Collection
If you want to check whether an element exists or not in the Generic `Queue<T>` Collection, then you need to use 
the **Contains()** method provided by the Generic Queue Class in C#.

The Contains(T item) method is used to determine whether an element exists in the generic queue or not. It returns 
true if the item is found in the generic queue; otherwise, false. Here, the parameter item specifies the element to 
locate in the queue. The value can be null for a reference type.

```C#
using System;
using System.Collections.Generic;

namespace QueueCollection
{
    internal class QueueCollection
    {
        static void Main(string[] args)
        {
            Queue<int> queue = new Queue<int>();
            queue.Enqueue(10);
            queue.Enqueue(20);
            queue.Enqueue(30);
            queue.Enqueue(40);
            queue.Enqueue(50);

            Console.WriteLine(queue.Contains(90)); // False
            Console.WriteLine(queue.Contains(40)); // True
        }
    }
}
```