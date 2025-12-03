# Generic Hashset Collection

The generic hashset is an unordered collection of unique elements. It does not allow for the addition of duplicate
elements.

It is recommended to use the HashSet collection if you want to store only unique elements.

## How to Create a Generic HashSet Collection
There are many constructors that we can use to create an instance of the generic hashset, but we are going to use the
constructor that does not take any parameters:

```C#
using System;
using System.Collections.Generic;

namespace HashsetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            HashSet<string> set = new HashSet<string>();
        }
    }
}
```

## How to Add Elements Into a HashSet Collection
You can use one of the following approaches:

### Using the Add(T item) Method
This method is used to add the specified element to a set. The parameter item specifies the element to add to the set. 

It returns true if the element is added to the HashSet object; false if the element is already present.

```C#
using System;
using System.Collections.Generic;

namespace HashsetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            HashSet<string> set = new HashSet<string>();
            set.Add("India");
            set.Add("Canada");
            set.Add("USA");
            set.Add("Morocco");
            set.Add("Kenya");
            set.Add("India");
        }
    }
}
```

### Using Collection Initializer
You can also add elements into a HashSet using collection initializer:

```C#
using System;
using System.Collections.Generic;

namespace HashsetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            HashSet<string> set = new HashSet<string>()
            {
                "India", "Canada", "USA", "Morocco", "Kenya", "India"
            };
        }
    }
}
```

## How to Access a Generic HashSet Collection
We can access elements of a generic HashSet using a foreach loop as shown:

```C#
using System;
using System.Collections.Generic;

namespace HashsetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            HashSet<string> set = new HashSet<string>();
            set.Add("India");
            set.Add("Canada");
            set.Add("USA");
            set.Add("Morocco");
            set.Add("Kenya");
            set.Add("India");

            foreach(string country in set)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```
You cannot use a for loop to access the elements of a generic HashSet collection and the reason for this is the 
Generic HashSet collection class does not have any integer indexer.

## How to Remove Elements From a Generic HashSet Collection
To remove an element from a generic HashSet collection, you can use one of the following methods:

### Remove(T item)
Used to remove the specified element from a hashset object.

Here, the parameter item specifies the element to remove. It returns true if the element is successfully found 
and removed; otherwise, false.

```C#
using System;
using System.Collections.Generic;

namespace HashsetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            HashSet<string> set = new HashSet<string>();
            set.Add("India");
            set.Add("Canada");
            set.Add("USA");
            set.Add("Morocco");
            set.Add("Kenya");
            set.Add("India");

            set.Remove("Morocco");
            set.Remove("Canada");

            foreach(string country in set)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

### RemoveWhere(`Predicate<T>` match)
This method is used to remove all elements that match the conditions defined by the specified predicate from 
a HashSet collection. 

It returns the number of elements that were removed from the HashSet collection. 

Here, the parameter match specifies the Predicate delegate that defines the conditions of the elements to remove.

In the following example, we are removing all country names whose length is less than 7.

```C#
using System;
using System.Collections.Generic;

namespace HashsetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            HashSet<string> set = new HashSet<string>();
            set.Add("India");
            set.Add("Canada");
            set.Add("USA");
            set.Add("Morocco");
            set.Add("Kenya");
            set.Add("India");

            set.RemoveWhere(country => country.Length < 7);

            foreach(string country in set)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

### Clear()
This method is used to remove all elements from a HashSet

```C#
using System;
using System.Collections.Generic;

namespace HashsetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            HashSet<string> set = new HashSet<string>();
            set.Add("India");
            set.Add("Canada");
            set.Add("USA");
            set.Add("Morocco");
            set.Add("Kenya");
            set.Add("India");

            set.Clear();

            foreach(string country in set)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

## How to Check the Availability of an Element in a HashSet
If you want to check whether an element exists or not in the HashSet, then you can use the 
Contains(T item) method of the HashSet class.

This method is used to determine whether a HashSet object contains the specified element. The parameter item
specifies the element to locate in the HashSet object. It returns true if the HashSet object contains the
specified element; otherwise, false.

```C#
using System;
using System.Collections.Generic;

namespace HashsetCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            HashSet<string> set = new HashSet<string>();
            set.Add("India");
            set.Add("Canada");
            set.Add("USA");
            set.Add("Morocco");
            set.Add("Kenya");
            set.Add("India");

            Console.WriteLine(set.Contains("India")); // True
            Console.WriteLine(set.Contains("China")); // False

            foreach(string country in set)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

## Set Operations on Generic HashSet Collection Class
The Generic HashSet Collection Class in C# also provides some methods that we can use to perform different set 
operations. 

The methods are as follows:

### `UnionWith(IEnumerable<T> other)`
It modifies your set by adding all the elements from the other set that are not already there.

- set 1: {1, 2, 3}
- set 2: {3, 4, 5}
- After union: {1, 2, 3, 4, 5}

`A ∪ B = {x: x ∈ A or x ∈ B}`

```C#
using System;
using System.Collections.Generic;

namespace HashSetOperations
{
    internal class HashSetOperations
    {
        static void Main(string[] args)
        {
            HashSet<int> ints1 = new HashSet<int>()
            {
                1, 2, 3,
            };

            HashSet<int> ints2 = new HashSet<int>()
            {
                3, 4, 5
            };

            ints1.UnionWith(ints2);

            foreach(int i in ints1)
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

namespace HashSetOperations
{
    internal class HashSetOperations
    {
        static void Main(string[] args)
        {
            HashSet<int> ints1 = new HashSet<int>()
            {
                1, 2, 3, 4
            };

            HashSet<int> ints2 = new HashSet<int>()
            {
                3, 4, 5
            };

            ints1.IntersectWith(ints2);

            foreach(int i in ints1)
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

namespace HashSetOperations
{
    internal class HashSetOperations
    {
        static void Main(string[] args)
        {
            HashSet<int> ints1 = new HashSet<int>()
            {
                1, 2, 3, 4, 5
            };

            HashSet<int> ints2 = new HashSet<int>()
            {
                2, 5, 7
            };
            
            ints1.ExceptWith(ints2);

            foreach(int i in ints1)
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

namespace HashSetOperations
{
    internal class HashSetOperations
    {
        static void Main(string[] args)
        {
            HashSet<int> ints1 = new HashSet<int>()
            {
                1, 2, 3, 4
            };

            HashSet<int> ints2 = new HashSet<int>()
            {
                3, 4, 5, 6
            };
            
            ints1.SymmetricExceptWith(ints2);

            foreach(int i in ints1)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```