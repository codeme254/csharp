# Non-Generic Stack Collection

The Stack Collection Class in C# represents a Last-In, First-Out (LIFO) collection of objects.

We need to use the Stack Collection Class in C#, when we want Last-In-First-Out access to the items of a collection. 
That means the item which is added last to the collection will be the first item to be removed from the collection.

When we add an item to a stack, the operation is called **pushing**, when we remove an element from a stack, the
operation is called **popping**.

Imagine we have a stack of books where each book is added on top of the other. The last book which is added to 
the stack will be the first one to be removed from the stack. It is not possible to remove a book from the 
middle of the stack. For a better understanding, please have a look at the following image.

![Stack](collections-stack.png)

In C#, the Non-Generic Stack Collection also works in the same way. Elements are added to the stack, on top of 
each other. When we add an item to the stack, then it is called pushing an item. The process of adding an element 
to the stack is called a Push operation. Similarly, when we remove an item from the stack then it is called 
popping an item. This operation is known as Pop.

![Stack](collections-stack-2.png)

Note: Stack is Defined as both generic and non-generic types of collection. The Generic Stack is defined 
in **System.Collections.Generic** namespace whereas Non-Generic Stack is defined under **System.Collections** namespace.

In this section, we will be discussing the Non-Generic Stack Collection Class.

## How to Create a Non-Generic Stack Collection
The non-generic collection Stack class in C# has three constructors which we can use to create a stack. 

The constructors are as follows:
1. **Stack()**: It is used to initialize a new instance of the Stack class that is empty and has the default
initial capacity.
2. **Stack(ICollection col)**: It is used to initialize a new instance of the non-generic Stack class that
contains elements copied from the specified collection and has the same initial capacity as the number of
elements copied. Here, the parameters col specifies the System.Collections.ICollection to copy elements from.
3. **Stack(int initialCapacity)**: It is used to initialize a new instance of the System.Collections.Stack
class that is empty and has the specified initial capacity or the default initial capacity, whichever is
greater. Here, the parameter initialCapacity specifies the initial number of elements that the Stack can contain.

```C#
using System;
using System.Collections;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack stack = new Stack();
        }
    }
}
```

## How to Add Elements to a Stack
If you want to add elements to a stack, then you need to use the Push() method of the Stack class.

It takes in one parameter - the item to be added to the stack.

```C#
using System;
using System.Collections;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack stack = new Stack();
            stack.Push("John");
            stack.Push(10);
            stack.Push(3.14f);
            stack.Push("Hello");
            stack.Push("A");
            stack.Push(true);
            stack.Push(false);

            foreach(var item in stack)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

## How to Remove Elements From a Stack
In Stack, you are allowed to remove elements from the top of the stack.

You can use one of the following methods:
- **Pop()**: This method is used to remove and return the object at the top of the Stack. It returns the
Object (element) removed from the top of the Stack.
- **Clear()**: This method is used to remove all objects from the Stack.

```C#
using System;
using System.Collections;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack stack = new Stack();
            stack.Push("John");
            stack.Push(10);
            stack.Push(3.14f);
            stack.Push("Hello");
            stack.Push("A");
            stack.Push(true);
            stack.Push(false);

            stack.Pop();
            stack.Pop();

            // You can also remove all items using the Clear method
            //stack.Clear();

            foreach(var item in stack)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

## How to Get the Topmost Element of a Stack
The Stack class in C# provides the following two methods to get the topmost element of the Stack.

1. `Pop()`: This method is used to remove and return the object at the top of the Stack. It returns the Object 
(element) removed from the top of the Stack. If there is no object (or element) present in the stack and if
you are trying to remove an item or object from the stack using the pop() method then it will throw an 
exception i.e. System.InvalidOperationException.
2. `Peek()`: The peek() method is used to return the object from the top of the Stack without removing it. If 
there is no object (or element) present in the stack and if you are trying to return an item (object) from
the stack using the peek() method then it will throw an exception i.e. System.InvalidOperationException

```C#
using System;
using System.Collections;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack stack = new Stack();
            stack.Push("John");
            stack.Push(10);
            stack.Push(3.14f);
            stack.Push("Hello");
            stack.Push("A");
            stack.Push(true);
            stack.Push(false);

            Console.WriteLine(stack.Peek()); // False (element at the top)
        }
    }
}
```

## How to Check Whether an Element Exists in a Stack
If you want to check whether an element exists or not in the stack, then you need to use the `Contains()` method.

This method is used to determine whether an element is in the Stack.

It takes in one parameter - the item to locate in the stack. It returns true if the item is found, otherwise it returns
false.

```C#
using System;
using System.Collections;

namespace StackCollection
{
    internal class StackCollection
    {
        static void Main(string[] args)
        {
            Stack stack = new Stack();
            stack.Push("John");
            stack.Push(10);
            stack.Push(3.14f);
            stack.Push("Hello");
            stack.Push("A");
            stack.Push(true);
            stack.Push(false);


            Console.WriteLine(stack.Contains("Hello")); // True
            Console.WriteLine(stack.Contains("World")); // False

        }
    }
}
```