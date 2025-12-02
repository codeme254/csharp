# Generic Stack Collection

The Generic Stack in C# is a collection class that works on the principle of Last In First Out (LIFO) and
this class is present in System.Collections.Generic namespace.

The Generic Stack Collection is used when we need Last In First Out (LIFO) access to items.

When we add an element into the stack, it is called pushing the element and when we remove an element from the
stack, it is called popping the element.

## How to Create a Generic `Stack<T>` Collection

The Generic Collection `Stack<T>` class in C# provides the following three constructors to create an 
instance of the Generic Stack<T> class.

1. **Stack()**: It is used to initialize a new instance of the Generic Stack class that is empty and has the
default initial capacity.
2. **`Stack(IEnumerable<T> collection)`**: It is used to initialize a new instance of the Generic Stack class 
that contains elements copied from the specified collection and has sufficient capacity to accommodate 
the number of elements copied. Here, the parameters collection specifies the collection to copy elements from. 
If the collection is null, then it will throw ArgumentNullException.
3. **Stack(int capacity)**: It is used to initialize a new instance of the Generic Stack class that is empty 
and has the specified initial capacity or the default initial capacity, whichever is greater. Here, the parameter 
capacity specifies the initial number of elements that the Stack can contain. If capacity is less than zero, 
then it will throw ArgumentOutOfRangeException.

In the example below, we are using the overload that doesn't take any parameters:

```C#
using System;
using System.Collections.Generic;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack<int> stack = new Stack<int>();
        }
    }
}

```

## How to Add Elements Into a Stack Collection
To add elements into a stack, we use the `Push` method.

The `Push(T item)` method is used to insert an element on top of the Stack. Here, the parameter item 
specifies the element to push onto the Stack.

```C#
using System;
using System.Collections.Generic;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack<int> stack = new Stack<int>();
            stack.Push(10);
            stack.Push(20);
            stack.Push(30);
            stack.Push(40);
            stack.Push(50);
        }
    }
}
```

We cannot add elements into a Stack using Collection Initializer and the reason for this is the Generic `Stack<T>` 
Collection Class does not have an Add method.

The point that you need to remember is if any collection class does not have the Add method then you cannot
use Collection Initializer to add elements.

## How to Access the Elements of a Generic Stack
We can access elements of a generic stack collection using a foreach loop as shown:

```C#
using System;
using System.Collections.Generic;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack<int> stack = new Stack<int>();
            stack.Push(10);
            stack.Push(20);
            stack.Push(30);
            stack.Push(40);
            stack.Push(50);

            foreach(int item in stack)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

You cannot use a for loop to access the elements of a generic stack collection and the reason for this is the 
Generic `Stack<T>` collection class does not have any integer indexer.

## How to Remove Elements from a Generic `Stack<T>` Collection
The generic stack collection class provides the following two methods to remove elements:
1. **Pop()**: How to Remove Elements from a Generic Stack<T> Collection
2. **Clear()**: This method is used to remove all objects from the Generic Stack.

```C#
using System;
using System.Collections.Generic;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack<int> stack = new Stack<int>();
            stack.Push(10);
            stack.Push(20);
            stack.Push(30);
            stack.Push(40);
            stack.Push(50);

            stack.Pop();
            // stack.Clear();

            foreach(int item in stack)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

## How to get the Topmost Element of a Generic Stack
The generic stack class in C# provides the following two methods to get the topmost element of the stack:
1. **Pop()**: This method is used to remove and return the object at the top of the Generic Stack. It returns 
the Object (element) removed from the top of the Stack. If there is no object (or element) present in the stack 
and if you are trying to remove an item or object from the stack using the pop() method then it will throw an 
exception i.e. System.InvalidOperationException.
2. **Peek()**: This method is used to return the object at the top of the Generic Stack without removing it. 
If there is no object (or element) present in the stack and if you are trying to return an item (object) from the 
stack using the peek() method then it will throw an exception i.e. System.InvalidOperationException.

```C#
using System;
using System.Collections.Generic;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack<int> stack = new Stack<int>();
            stack.Push(10);
            stack.Push(20);
            stack.Push(30);
            stack.Push(40);
            stack.Push(50);
            
            Console.WriteLine(stack.Peek()); // 50
        }
    }
}
```

## How to check whether an element exists or not in the Generic `Stack<T>` Collection
If you want to check whether an element exists or not in the Generic Stack<T> Collection, then you need to use the
`Contains(T item)` method.

The `Contains(T item)` method is used to determine whether an element exists in the generic stack or not. It returns 
true if the item is found in the generic Stack; otherwise, false. Here, the parameter item specifies the element 
to locate in the Stack. The value can be null for a reference type.

```C#
using System;
using System.Collections.Generic;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack<int> stack = new Stack<int>();
            stack.Push(10);
            stack.Push(20);
            stack.Push(30);
            stack.Push(40);
            stack.Push(50);

            Console.WriteLine(stack.Contains(90));// False
            Console.WriteLine(stack.Contains(40)); // True
        }
    }
}
```