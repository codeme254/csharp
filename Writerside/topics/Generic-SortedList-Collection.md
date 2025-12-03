# Generic SortedList Collection

The Generic `SortedList<TKey, TValue>` Collection Class in C# represents a collection of key/value pairs 
that are sorted by the keys.

With the help of a key, we can easily search for or remove elements from the SortedList collection. The generic 
SortedList collection can be accessible either by using the keys or by using the integral index.

The `SortedList<TKey, TValue>` Collection allows us to store duplicate values, but the keys must 
be unique and cannot be null.


## How to Create a Generic SortedList Collection
There are various constructors that we can use to create an instance of the Generic SortedList collection, in the
example below, we are using the constructor that doesn't take any parameters:

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>();
        }
    }
}
```

## How to Add Elements to a Generic SortedList Collection
You can use one of the following approaches to add elements to a generic SortedList collection:

### Add(TKey key, TValue value)
The Add(TKey key, TValue value) method is used to add an element with the specified key and value into the 
Generic SortedList.

Here, the parameter key specifies the key of the element to add and the parameter value specifies the element to add.

The value can be null for reference types. If the key is null, then it will throw ArgumentNullException and if an 
element with the same key already exists in the Generic SortedList, then it will throw ArgumentException.

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>();

            sl.Add(1, "One");
            sl.Add(5, "Five");
            sl.Add(3, "Three");
            sl.Add(2, "Two");
            sl.Add(4, "Four");
        }
    }
}
```

### Using Collection Initializer
You can also use the collection initializer to add elements to a SortedList.

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>()
            {
                { 1, "One" },
                { 5, "Five" },
                { 3, "Three" },
                { 2, "Two" },
                { 4, "Four" }
            };
        }
    }
}
```

## How to Access a Generic SortedList
You can use one of the following approaches:

### Using a foreach loop
You can use a foreach loop to access elements of a SortedList.

The type of each key value pair is `KeyValuePair<TKey, TValue>`

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>();

            sl.Add(1, "One");
            sl.Add(5, "Five");
            sl.Add(3, "Three");
            sl.Add(2, "Two");
            sl.Add(4, "Four");

            foreach(KeyValuePair<int, string> kv in sl)
            {
                Console.WriteLine($"Key: {kv.Key}, Value: {kv.Value}");
            }
        }
    }
}
```

### Using Indexes

You can access the individual value of the Generic SortedList Collection in C# by using the index. In this case,
we need to pass the key as a parameter to find the respective value.

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>();

            sl.Add(1, "One");
            sl.Add(5, "Five");
            sl.Add(3, "Three");
            sl.Add(2, "Two");
            sl.Add(4, "Four");

            //Console.WriteLine(sl[0]); // Error, key 0 is not present
            Console.WriteLine(sl[1]); // One
            Console.WriteLine(sl[4]); // Four

            foreach(KeyValuePair<int, string> kv in sl)
            {
                Console.WriteLine($"Key: {kv.Key}, Value: {kv.Value}");
            }
        }
    }
}
```

You can also use indexes to add new items to a SortedList and update existing items:

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>();

            sl.Add(1, "One");
            sl.Add(5, "Five");
            sl.Add(3, "Three");
            sl.Add(2, "Two");
            sl.Add(4, "Four");

            // Adding new items
            sl[9] = "Nine";

            // Updating items
            sl[4] = "new four";

            foreach(KeyValuePair<int, string> kv in sl)
            {
                Console.WriteLine($"Key: {kv.Key}, Value: {kv.Value}");
            }
        }
    }
}
```

## How to Remove Elements From a Generic SortedList

You can use one of the following methods:

### Remove(TKey key)
This method is used to remove the element with the specified key from the SortedList. 

The parameter key specifies the element to remove. 

It returns true if the element is successfully removed; otherwise, false. 

This method also returns false if the key was not found in the original Generic SortedList.

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>();

            sl.Add(1, "One");
            sl.Add(5, "Five");
            sl.Add(3, "Three");
            sl.Add(2, "Two");
            sl.Add(4, "Four");

            sl.Remove(5);

            foreach(KeyValuePair<int, string> kv in sl)
            {
                Console.WriteLine($"Key: {kv.Key}, Value: {kv.Value}");
            }
        }
    }
}
```

### RemoveAt(int index)
This method is used to remove the element at the specified index of a Generic SortedList. The parameter 
index specifies the element to remove. It is 0 based Index.

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>();

            sl.Add(1, "One");
            sl.Add(5, "Five");
            sl.Add(3, "Three");
            sl.Add(2, "Two");
            sl.Add(4, "Four");

            sl.RemoveAt(0);

            foreach(KeyValuePair<int, string> kv in sl)
            {
                Console.WriteLine($"Key: {kv.Key}, Value: {kv.Value}");
            }
        }
    }
}

```

### Clear()
This method is used to remove all elements from a Generic SortedList Collection.

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>();

            sl.Add(1, "One");
            sl.Add(5, "Five");
            sl.Add(3, "Three");
            sl.Add(2, "Two");
            sl.Add(4, "Four");
            
            sl.Clear();

            foreach(KeyValuePair<int, string> kv in sl)
            {
                Console.WriteLine($"Key: {kv.Key}, Value: {kv.Value}");
            }
        }
    }
}
```

## How to Check the Availability of Key Value Pairs in a Generic SortedList Collection
If you want to check whether the key/value pair exists or not in the Generic SortedList Collection in C#, then you 
can use the following methods provided by the Generic SortedList class:

### ContainsKey(TKey key)
This method is used to determine whether the Generic SortedList collection contains a specific key.

It returns true if the Generic SortedList collection contains an element with the specified key; otherwise, false. 

If the key is null, then it will throw System.ArgumentNullException.

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>();

            sl.Add(1, "One");
            sl.Add(5, "Five");
            sl.Add(3, "Three");
            sl.Add(2, "Two");
            sl.Add(4, "Four");

            Console.WriteLine(sl.ContainsKey(1)); // True
            Console.WriteLine(sl.ContainsKey(20)); // False
        }
    }
}
```

### ContainsValue(TValue value)
This method is used to determine whether a Generic SortedList contains a specific value.

The value can be null for reference types. It returns true if the Generic SortedList Collection contains an element 
with the specified value; otherwise, false.

```C#
using System;
using System.Collections.Generic;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList<int, string> sl = new SortedList<int, string>();

            sl.Add(1, "One");
            sl.Add(5, "Five");
            sl.Add(3, "Three");
            sl.Add(2, "Two");
            sl.Add(4, "Four");

            Console.WriteLine(sl.ContainsValue("One")); // True
            Console.WriteLine(sl.ContainsValue("Fifty")); // False
        }
    }
}
```