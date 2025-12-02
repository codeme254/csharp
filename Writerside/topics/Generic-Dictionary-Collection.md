# Generic Dictionary Collection

A Dictionary class is a data structure that represents a collection of keys values pair of data.

The working of the Generic Dictionary is very much similar to the working of the Non-Generic Hashtable collection. 
The difference is while creating the generic dictionary object we need to specify the type for both the keys 
and the type for values.

It belongs to `System.Collection.Generic` namespace.

Following are a few points that you need to remember while working with Dictionary in C#.
1. In Generic `Dictionary<TKey, TValue>` Collection, the key cannot be null, but the value can be null if 
its type `TValue` is a reference type.
2. Every key in Generic `Dictionary<TKey, TValue>` Collection must be unique. Duplicate keys are not allowed. 
If you try to add a duplicate key then the compiler will throw an exception.
3. In Generic `Dictionary<TKey, TValue>` Collection, you can only store the same types of elements.
4. The capacity of a Dictionary collection is the number of elements that the Dictionary can hold.

## How to create a Generic Dictionary Collection in C#
The Generic Dictionary collection class in C# provides the following constructors that we can use to create an instance
of the dictionary class:
1. **Dictionary()**: It initializes a new instance of the Generic Dictionary class that is empty, has the 
default initial capacity and uses the default equality comparer for the key type.
2. **Dictionary(IDictionary<TKey, TValue> dictionary)**: it initializes a new instance of the generic dictionary class
that contains elements copied from the specified dictionary.
3. **Dictionary(int capacity)**: It initializes a new instance of the Generic Dictionary class that is empty, 
has the specified initial capacity and uses the default equality comparer for the key type.

Other constructors are:
- **Dictionary(IEnumerable<KeyValuePair<TKey, TValue>> collection)**
- **Dictionary(IEqualityComparer`<TKey>`? comparer)**
- **Dictionary(IDictionary<TKey, TValue> dictionary, IEqualityComparer`<TKey>`? comparer)**
- **Dictionary(int capacity, IEqualityComparer`<TKey>`? comparer)**
- **Dictionary(SerializationInfo info, StreamingContext context)**

In the following example, we are creating an instance of the dictionary class using the overload that doesn't take
any parameters - `Dictonary()`

The general syntax is: 
`Dictionary<KeyDataType, ValuDataType> dictionary_name = new Dictionary<KeyDataType, ValuDataType>();`.

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
        }
    }
}
```

## How to Add Elements into a Generic Dictionary
You can add elements to a dictionary through one of the following ways:

### Using the `Add` method.
The `Add(TKey key, TValue value)` method is used to add an element with the specified key and value into 
the Dictionary. 

Here, the parameter key specifies the key of the element to add and the parameter value specifies the value 
of the element to add. 

The value can be null for a reference type but the Key cannot be null.

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
            dict.Add("One", 1);
            dict.Add("Two", 2);
            dict.Add("Three", 3);
            dict.Add("Four", 4);
            dict.Add("Five", 5);
        }
    }
}
```

### Using the Collection Initializer syntax
You can add elements using the collection initializer syntax:

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>()
            {
                { "One", 1 },
                { "Two", 2 },
                { "Three", 3 },
                { "Four", 4 },
                { "Five", 5 }
            };
        }
    }
}
```

### Using Indexers
In order to add value to a Dictionary with an indexer, we need to use square brackets after the Dictionary name. 
This is because a Dictionary works with key/value pairs, and we have to specify both key and value while 
adding the elements. The key is specified between square brackets. The syntax is given below.

`dictionary[key] = value;`

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
            dict.Add("One", 1);
            dict.Add("Two", 2);
            dict.Add("Three", 3);
            dict.Add("Four", 4);
            dict.Add("Five", 5);

            // Adding elements using indexer
            dict["six"] = 6;
            dict["seven"] = 7;
            dict["eight"] = 8;
        }
    }
}
```

## How to access a Generic Dictionary Collection
We can access the key value pairs of a generic dictionary collection through one of the following ways:

### Using Keys
You can access the individual value of the Dictionary collection in C# by using the keys. 

In this case, we just need to specify the key to get the value from the given dictionary.

If the specified key is not present, the compiler will throw an exception.

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
            dict.Add("One", 1);
            dict.Add("Two", 2);
            dict.Add("Three", 3);
            dict.Add("Four", 4);
            dict.Add("Five", 5);

            Console.WriteLine(dict["One"]); // 1
            Console.WriteLine(dict["Two"]); // 2
        }
    }
}
```

### Using a foreach Loop
The type for each key value pair is `KeyValuePaier<TKey, TValue>`.

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
            dict.Add("One", 1);
            dict.Add("Two", 2);
            dict.Add("Three", 3);
            dict.Add("Four", 4);
            dict.Add("Five", 5);

            //Console.WriteLine(dict["One"]); // 1
            //Console.WriteLine(dict["Two"]); // 2

            foreach(KeyValuePair<string, int> kvp in dict)
            {
                Console.WriteLine($"Key: {kvp.Key}, value: {kvp.Value}");
            }
        }
    }
}
```

## How to Update a Dictionary
We already discussed that we can retrieve the value from the Dictionary by using the key in the indexer. In the 
same way, we can also use the key indexer to update an existing key-value pair in the Dictionary collection

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
            dict.Add("One", 1);
            dict.Add("Two", 2);
            dict.Add("Three", 3);
            dict.Add("Four", 4);
            dict.Add("Five", 5);

            // Updating elements using indexer
            dict["One"] = 11;
            dict["Two"] = 22;
            dict["Three"] = dict["Three"] * 11;
            dict["Four"] = dict["Four"] * 11;
            dict["Five"] = dict["Five"];

            foreach(KeyValuePair<string, int> kvp in dict)
            {
                Console.WriteLine($"Key: {kvp.Key}, value: {kvp.Value}");
            }
        }
    }
}
```

## How to Check the Availability of a key/value Pair in a Dictionary
If you want to check whether the key/value pair exists or not in the Dictionary collection, then you can use
the following methods of the Generic Dictionary Collection Class in C#:

1. **ContainsKey(TKey key)**: The ContainsKey(TKey key) method of the Dictionary is used to check if 
the given key is present in the Dictionary or not. It takes one parameter - the key to locate. If the given key is
present, it will return true, else it will return false. If the key is null, it will throw an exception.
2. **ContainsValue(TValue value)**: The ContainsValue(TValue value) Method of the Dictionary class is used to
check if the given value is present in the Dictionary or not. It takes in one parameter - the value to locate. If the
given value is present, it will return true, else it will return false.

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
            dict.Add("One", 1);
            dict.Add("Two", 2);
            dict.Add("Three", 3);
            dict.Add("Four", 4);
            dict.Add("Five", 5);

            Console.WriteLine(dict.ContainsKey("One")); // True
            Console.WriteLine(dict.ContainsKey("Ten")); // False
            Console.WriteLine(dict.ContainsValue(1)); // True
            Console.WriteLine(dict.ContainsValue(9)); // False
        }
    }
}
```

## How to Remove Elements from a Generic Dictionary Collection
You can remove elements from a dictionary using one of the following ways:
1. **Remove(TKey key)**: This method is used to remove the element with the specified key from the Dictionary 
collection. Here, the parameter key specifies the element to remove. It throws `KeyNotfoundException` if the 
specified key is not found in the Dictionary, so check for an existing key using the `ContainsKey()` method 
before removing it.
2. **Clear()**: This method is used to remove all elements i.e. all the keys and values from the Dictionary object.

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
            dict.Add("One", 1);
            dict.Add("Two", 2);
            dict.Add("Three", 3);
            dict.Add("Four", 4);
            dict.Add("Five", 5);

            if (dict.ContainsKey("One"))
            {
                dict.Remove("One");
            }

            // dict.Clear();
        }
    }
}
```

## TryGetValue()
This is one of the important methods of Dictionary collection class in C#.

This method takes two parameters, one is the key and the other one is the value. The value is of out type parameter. 
If the key exists in the dictionary, then it will return true and the value with that associated key is stored on
the output variable.

If you are not sure if a key is present or not in the dictionary, then you can use the TryGetValue() method to
get the value from a dictionary because if you are not using TryGetValue then in that case you will get 
`KeyNotFoundException`.

Have a look at the following example, we are passing the key as `"Two"` and out variable, i.e `twoVal`, as we can see,
the key `"Two"` is present in the dictionary, so the method will return the associated value and this associated
value will be stored in the variable `twoVal`.

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
            dict.Add("One", 1);
            dict.Add("Two", 2);
            dict.Add("Three", 3);
            dict.Add("Four", 4);
            dict.Add("Five", 5);

            bool twoExists = dict.TryGetValue("Two", out int twoVal);
            if (twoExists)
            {
                Console.WriteLine(twoVal);
            }
            else
            {
                Console.WriteLine("Two doesn't exist");
            }
        }
    }
}
```

In the following example, the key doesn't exist, the TryGetValue method will now return false and hence the out variable
will not be populated, all of this happens without any exception being thrown.

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
            dict.Add("One", 1);
            dict.Add("Two", 2);
            dict.Add("Three", 3);
            dict.Add("Four", 4);
            dict.Add("Five", 5);

            bool nineExists = dict.TryGetValue("Nine", out int nineVal);
            if (nineExists)
            {
                Console.WriteLine(nineVal);
            }
            else
            {
                Console.WriteLine("Nine doesn't exist");
            }
        }
    }
}
```

## How to get all the keys and Values of a Dictionary
To get all keys, use the `Keys` property, it represents a list of all the keys present in a dictionary.

To get all values, use the `Values` property, it represents a list of all the values present in a dictionary.

```C#
using System;
using System.Collections.Generic;

namespace DictionaryCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Dictionary<string, int> dict = new Dictionary<string, int>();
            dict.Add("One", 1);
            dict.Add("Two", 2);
            dict.Add("Three", 3);
            dict.Add("Four", 4);
            dict.Add("Five", 5);

            Console.WriteLine("===KEYS===");
            foreach(string key in dict.Keys)
            {
                Console.WriteLine(key);
            }

            Console.WriteLine("===VALUES===");
            foreach(int value in dict.Values)
            {
                Console.WriteLine(value);
            }
        }
    }
}
```