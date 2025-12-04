# Generic SortedDictionary Collection

The `SortedDictionary<TKey, TValue>` is a Generic Collection class in C# which is used to store the key/value 
pairs in the sorted form and the sorting is done based on the key.

As it is a Generic Collection, so, it belongs to `System.Collections.Generic namespace`.

The keys of the SortedDictionary collection must be unique and maintains ascending order based on 
the key. With the help of a key, we can easily search or remove elements from the generic 
`SortedDictionary<TKey, TValue>` collection.

It is dynamic in nature which means the size of the sorted dictionary is increased automatically as we added 
key/value pairs to the collection. The keys of `SortedDictionary<TKey, TValue>` collection cannot be null but 
the value can be null for a reference type.

## How to Create a SortedDictionary Collection
The Generic `SortedDictionary<TKey, TValue>` Collection class in C# provides several constructors that we can use to
create an instance of the SortedDictionary, in the example below, we are using the overload that doesn't take any
parameters:

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
        }
    }
}
```

## How to Add Elements to a Generic SortedDictionary
If you want to add a key/value pair to a Generic SortedDictionary Collection, you can use one of the following
approaches:

### Add(TKey, TValue) method
The Add(TKey key, TValue value) method is used to add an element with the specified key and value into the
Generic SortedDictionary collection.

Here, the parameter key specifies the key of the element to add and the parameter value specifies the element to add.

The value can be null for reference types. If the key is null, then it will throw ArgumentNullException and 
if an element with the same key already exists in the Generic SortedDictionary, then it will throw ArgumentException.

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");
        }
    }
}
```

### Using Collection Initializer
We can add elements to a SortedDictionary using the collection initializer as shown:

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>()
            {
                { 1, "One" },
                { 2, "Two" },
                { 10, "Ten" },
                { 3, "Three" },
                { 5, "Five" },
                { 7, "Seven" }
            };
        }
    }
}
```
You can add the elements into the collection in random order. But they are going to be stored in the collection 
in Ascending order based on key.

### Using Indexer
In order to add value to a SortedDictionary with an indexer, we need to use square brackets after the 
SortedDictionary name. 

This is because a SortedDictionary works with key/value pairs, and we have to specify both key and value while 
adding the elements. 

The key is specified between square brackets.

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");

            sd[4] = "Four";
            sd[6] = "Six";
            sd[8] = "Eight";
            sd[9] = "Nine";
        }
    }
}
```

We can also use indexers to update the values in a SortedDictionary:

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");

            sd[4] = "Four";
            sd[6] = "Six";
            sd[8] = "Eight";
            sd[9] = "Nine";

            sd[8] = "New Eight";
            sd[5] = "New Five";
        }
    }
}
```

## How to Access a Generic SortedDictionary
You can use one of the following approaches to access the elements of a SortedDictionary collection;

### foreach loop
We can use a for-each loop to access the key/value pairs of the Generic SortedDictionary Collection.

The data type for the key value pairs is `KeyValuePair<TKey, TValue>`

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");

            foreach(KeyValuePair<int, string> kvp in sd)
            {
                Console.WriteLine($"{kvp.Key} - {kvp.Value}");
            }
        }
    }
}
```

### Using Index to Access Individual SortedDictionary Collection Elements
You can access the individual value of the Generic SortedDictionary Collection in C# by using the indexer. 

In this case, you just need to pass the key as a parameter to find the corresponding value.

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");

            Console.WriteLine(sd[2]); // Two
            Console.WriteLine(sd[10]); // Ten
            Console.WriteLine(sd[7]); // Seven
        }
    }
}
```

## How to Remove Elements from a Generic SortedDictionary Collection
If you want to remove elements from a SortedDictionary, you can use one of the following methods:

### Remove(TKey key)
This method is used to remove the element with the specified key from the Generic SortedDictionary.

The parameter key specifies the element to remove. It returns true if the element is successfully removed;
otherwise, false.

This method also returns false if the key was not found in the original Generic SortedDictionary. If the key 
is null, then it will throw ArgumentNullException.

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");

            sd.Remove(10);
            sd.Remove(5);
            sd.Remove(7);

            foreach(KeyValuePair<int, string> kvp in sd)
            {
                Console.WriteLine($"{kvp.Key} - {kvp.Value}");
            }
        }
    }
}
```

### Clear()
This method is used to remove all elements from a Generic SortedDictionary Collection.

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");

            sd.Clear();

            foreach(KeyValuePair<int, string> kvp in sd)
            {
                Console.WriteLine($"{kvp.Key} - {kvp.Value}");
            }
        }
    }
}
```

## How to Check the Availability of key/value Pairs in a Generic SortedDictionary Collection
If you want to check whether the key/value pair exists or not in the Generic SortedDictionary Collection in C#,
then you can use the following methods provided by the Generic SortedDictionary class:

### ContainsKey(TKey key)
This method is used to determine whether the Generic SortedDictionary collection contains a specific key.

It returns true if the Generic SortedDictionary collection contains an element with the specified key; otherwise, 
false. If the key is null, then it will throw ArgumentNullException.

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");
            
            Console.WriteLine(sd.ContainsKey(10)); // True
            Console.WriteLine(sd.ContainsKey(1000)); // False
        }
    }
}
```

### ContainsValue(TValue value)
This method is used to determine whether a Generic SortedDictionary contains a specific value.

It takes one parameter - the value to locate.

The value can be null for reference types. It returns true if the Generic SortedDictionary Collection contains an 
element with the specified value; otherwise, false.

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");

            Console.WriteLine(sd.ContainsValue("Three")); // True
            Console.WriteLine(sd.ContainsValue("Nine")); // False
        }
    }
}
```

## TryGetValue()
This is one of the important methods of Dictionary collection class in C#.

This method takes two parameters, one is the key and the other one is the value. The value is of out type parameter. 
If the key exists in the dictionary, then it will return true and the value with that associated key is stored on
the output variable.

If you are not sure if a key is present or not in the dictionary, then you can use the TryGetValue() 
method to get the value from a dictionary because if you are not using TryGetValue then in that case you 
will get KeyNotFoundException.

Have a look at the following example, we are passing the key as 10 and out variable, i.e `ten`, as we can see, the
key 10 is present in the dictionary, so the method will return the associated value and this associated
value will be stored in the variable `ten`.

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");

            bool tenExists = sd.TryGetValue(10, out string ten);
            if (tenExists)
            {
                Console.WriteLine(ten);
            }
            else
            {
                Console.WriteLine("Value does not exist");
            }
        }
    }
}
```

In the following example, the key doesn't exist, the TryGetValue method will now return false and hence the out 
variable will not be populated, all of this happens without any exception being thrown.

```C#
using System;
using System.Collections.Generic;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");

            bool twentyExists = sd.TryGetValue(20, out string twenty);
            if (twentyExists)
            {
                Console.WriteLine(twenty);
            }
            else
            {
                Console.WriteLine("Twenty does not exist");
            }
        }
    }
}
```

## How to Get all the Keys and Values of a SortedDictionary
To get all keys, use the `Keys` property, it represents a list of all the keys present in a dictionary.

To get all values, use the `Values` property, it represents a list of all the values present in a dictionary.

```C#
using System;
using System.Collections.Generic;
using System.Runtime.InteropServices;

namespace SortedDictionaryCollection
{
    internal class SortedDictionaryCollection
    {
        static void Main(string[] args)
        {
            SortedDictionary<int, string> sd = new SortedDictionary<int, string>();
            sd.Add(1, "One");
            sd.Add(2, "Two");
            sd.Add(10, "Ten");
            sd.Add(3, "Three");
            sd.Add(5, "Five");
            sd.Add(7, "Seven");

            Console.WriteLine("===KEYS===");
            foreach(int key in sd.Keys)
            {
                Console.WriteLine(key);
            }

            Console.WriteLine("===VALUES===");
            foreach(string value in sd.Values)
            {
                Console.WriteLine(value);
            }
        }
    }
}
```