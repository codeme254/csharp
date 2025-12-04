# Generic SortedSet Collection

SortedSet Collection store the elements in sorted order. That means it stores the element in ascending order and
also, and it does not store duplicate elements. So, it is recommended to use the SortedSet collection if 
you want to store only unique elements in ascending order.

The collection is of generic type and hence belongs to `System.Collections.Generic` namespace.

## How to Create a Generic SortedSet Collection
The generic SortedSet collection class provides various constructors that we can use to create an instance of SortedSet,
in the example below, we are using the version that doesn't take any parameters:

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> st = new SortedSet<int>();
        }
    }
}
```

## How to Add Elements Into SortedSet
If you want to add elements into a SortedSet collection, you can use one of the following approaches:

### Add(T item) method
This method is used to add an element to the set and returns a value that indicates if it was successfully added. 

The parameter item specifies the element to add to the set. It returns true if the element is added to the 
SortedSet object; otherwise, false.

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> st = new SortedSet<int>();
            st.Add(10);
            st.Add(5);
            st.Add(60);
            st.Add(70);
            st.Add(25);
        }
    }
}
```

### Using Collection Initializer
You can also add elements into a SortedSet using the collection initializer syntax as follows:

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> st = new SortedSet<int>()
            {
                10, 5, 60, 70, 25
            };
        }
    }
}
```

## How to Access a Generic SortedSet Collection
We can access elements of a generic SortedSet collection using the `foreach` loop as shown:

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> st = new SortedSet<int>();
            st.Add(10);
            st.Add(5);
            st.Add(60);
            st.Add(70);
            st.Add(25);
            st.Add(60);

            foreach (int i in st)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

## How to Remove Elements From a Generic SortedSet Collection
To remove elements from a generic SortedSet, you can use one of the following methods:

### Remove(T item)
This method is used to remove the specified element from a SortedSet object.

Here, the parameter item specifies the element to remove. It returns true if the element is successfully found 
and removed; otherwise, false. 

This method returns false if the item is not found in the Generic SortedSet collection.

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> st = new SortedSet<int>();
            st.Add(10);
            st.Add(5);
            st.Add(60);
            st.Add(70);
            st.Add(25);
            st.Add(60);

            st.Remove(10);
            st.Remove(5);

            foreach (int i in st)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

### `RemoveWhere(Predicate<T> match)`
This method is used to remove all elements that match the conditions defined by the specified predicate from a 
SortedSet collection. 

It returns the number of elements that were removed from the SortedSet collection. 

Here, the parameter match specifies the Predicate delegate that defines the conditions of the elements to remove.

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> st = new SortedSet<int>();
            st.Add(10);
            st.Add(5);
            st.Add(60);
            st.Add(70);
            st.Add(25);
            st.Add(60);

            st.RemoveWhere(num => num < 20);

            foreach (int i in st)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

### `Clear()`
Removes all the elements from a SortedSet object.

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> st = new SortedSet<int>();
            st.Add(10);
            st.Add(5);
            st.Add(60);
            st.Add(70);
            st.Add(25);
            st.Add(60);

            st.Clear();

            foreach (int i in st)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

## How to Check the Availability of an Element in a SortedSet
If you want to check whether an element exists or not in the SortedSet, then you can use the `Contains(T item)` method.

This method is used to determine whether a SortedSet object contains the specified element. 

The parameter item specifies the element to locate in the SortedSet object. 

It returns true if the SortedSet object contains the specified element; otherwise, false.

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> st = new SortedSet<int>();
            st.Add(10);
            st.Add(5);
            st.Add(60);
            st.Add(70);
            st.Add(25);
            st.Add(60);
            
            Console.WriteLine(st.Contains(10)); // True
            Console.WriteLine(st.Contains(100)); // False
        }
    }
}
```

## Set Operations on Generic SortedSet Collection
The Generic SortedSet Collection Class in C# also provides some methods that we can use to perform different set
operations. The methods are as follows:

### `UnionWith(IEnumerable<T> other)`
It modifies your set by adding all the elements from the other set that are not already there.

- set 1: {1, 2, 3}
- set 2: {3, 4, 5}
- After union: {1, 2, 3, 4, 5}

`A ∪ B = {x: x ∈ A or x ∈ B}`

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> set1 = new SortedSet<int>()
            {
                1, 2, 3,
            };
            SortedSet<int> set2 = new SortedSet<int>()
            {
                3, 4, 5, 6
            };
            
            set1.UnionWith(set2);

            foreach (int i in set1)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

### `IntersectWith(IEnumerable<T> other)`
It modifies the current set so that it keeps ONLY the elements that also exist in the other set.

- set 1: {1, 2, 3, 4}
- set 2: {3, 4, 5}
- after intersection: {3, 4}

`A∩B = {x: x ∈ A and x ∈ B}`

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> set1 = new SortedSet<int>()
            {
                1, 2, 3, 4
            };
            SortedSet<int> set2 = new SortedSet<int>()
            {
                3, 4, 5, 6
            };
            
            set1.IntersectWith(set2);

            foreach (int i in set1)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

### `ExceptWith(IEnumerable<T> other)`
It removes everything from your current set that appears in the other set.

- set 1: { 1, 2, 3, 4, 5 }
- set 2: { 2, 5, 7 }
- after except with: { 1, 3, 4 }

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> set1 = new SortedSet<int>()
            {
                1, 2, 3, 4
            };
            SortedSet<int> set2 = new SortedSet<int>()
            {
                3, 4, 5, 6
            };
            
            set1.ExceptWith(set2);

            foreach (int i in set1)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

### `SymmetricExceptWith(IEnumerable<T> other)`
It modifies the current set such that it contains all elements that are in either the current set OR the other
set BUT NOT in both.

- set 1: { 1, 2, 3, 4 }
- set 2: { 3, 4, 5, 6}
- after symmetric except with: { 1, 2, 5, 6 }

```C#
using System;
using System.Collections.Generic;

namespace SortedSetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            SortedSet<int> set1 = new SortedSet<int>()
            {
                1, 2, 3, 4
            };
            SortedSet<int> set2 = new SortedSet<int>()
            {
                3, 4, 5, 6
            };

            set1.SymmetricExceptWith(set2);

            foreach (int i in set1)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```