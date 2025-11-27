# Non-Generic SortedList Collection

The Non-Generic SortedList Collection Class in C# represents a collection of key/value pairs that are sorted by the 
keys and are accessible by key and by index. 

By default, it sorts the key/value pairs in ascending order.

## Properties of Non-Generic SortedList Class in C#
1. The Non-Generic SortedList Class in C# implements the IEnumerable, ICollection, IDictionary, 
and ICloneable interfaces.
2. We can access elements using their keys or their index in a SortedList.
3. The Non-Generic SortedList object internally maintains two arrays to store the elements of the list, i.e, 
one array for the keys and another array for the associated values. Here, the key cannot be null, but the 
value can be null. And one more, it does not allow duplicate keys.
4. The capacity of the Non-Generic SortedList object is the number of key/value pairs it holds.
5. In the Non-Generic SortedList object in C#, we can store values of the same type and of the different types 
as it operates on the object data type.
6. In the same SortedList, it is not possible to store keys of different data types. If you try then the 
compiler will throw an exception.

## Methods, Properties, and Constructor of Non-Generic SortedList Collection Class
If you go to the definition of the Non-Generic SortedList Collection Class, then you will see the following.

![SortedList definition](collections-sortedlist-definition.png)

## How to Create a SortedList Collection
The Non-Generic SortedList Collection Class in C# is provided with six constructors that we can use to create
an instance of `SortedList`.

Among these constructors is the `SortedList()` constructor that doesn't take any parameters
- **SortedList()**: It initializes a new instance of the SortedList class that is empty, has the 
default initial capacity and is sorted according to the IComparable interface implemented by each key added to
the SortedList object.

```C#
using System;
using System.Collections;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList sl = new SortedList();
        }
    }
}
```

## How to Add Elements Into a SortedList Collection
If you want to add a key/value pair to a SortedList, then you need to use the `Add()` method of the SortedList class.

The **Add(object key, object value)** method is used to add an element with the specified key and value 
to a SortedList. Here, the parameter key specifies the key of the element to add and the parameter value 
specifies the element to add. The value can be null.

NOTE: The keys are supposed to be of the same data type, the values can be of different data types but the keys must
be of the same data type.

```C#
using System;
using System.Collections;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList sl = new SortedList();
            sl.Add(1, "One");
            sl.Add(2, "Two");
            sl.Add(3, "Three");
            sl.Add(50, 5);
            sl.Add(100, null);
        }
    }
}
```
## How to Access Elements of a SortedList
We can access the key/value pairs of the SortedList collection in C# using four different ways. 

They are as follows:

### Using Keys to Access SortedList Elements
You can access the individual value of the SortedList in C# by using the keys. In this case, we need to pass the 
key as a parameter to find the respective value.

This is done as shown:

```C#
using System;
using System.Collections;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList sl = new SortedList();
            sl.Add(1, "One");
            sl.Add(2, "Two");
            sl.Add(3, "Three");
            sl.Add(50, 5);
            sl.Add(100, null);

            Console.WriteLine($"Key 100, value {sl[100]}"); // null
            Console.WriteLine($"Key 50, value {sl[50]}"); // 5
            Console.WriteLine($"Key 1, value {sl[1]}");  // One
        }
    }
}
```

### Using Indexes to Access SortedList Elements
You can access the individual value of the SortedList in C# by using the Index position. In this case, 
we need to pass the Integer Index Position as a parameter to find the respective value.

This is done as shown:

```C#
using System;
using System.Collections;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList sl = new SortedList();
            sl.Add(1, "One");
            sl.Add(2, "Two");
            sl.Add(3, "Three");
            sl.Add(50, 5);
            sl.Add(100, null);
            
            Console.WriteLine(sl.GetByIndex(0)); // One
            Console.WriteLine(sl.GetByIndex(1)); // Two
            Console.WriteLine(sl.GetByIndex(3)); // 5
        }
    }
}
```

### Accessing Elements Using a For Loop
You can use for loop to access the key/value pairs of the SortedList Collection as shown below.

Use the `Count` property to get the number of items in a SortedList

```C#
using System;
using System.Collections;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList sl = new SortedList();
            sl.Add(1, "One");
            sl.Add(2, "Two");
            sl.Add(3, "Three");
            sl.Add(50, 5);
            sl.Add(100, null);

            for (int i = 0; i < sl.Count; i++)
            {
                Console.WriteLine("---");
                Console.WriteLine($"Key: {sl.GetKey(i)}");
                Console.WriteLine($"Value: {sl.GetByIndex(i)}");
                Console.WriteLine("---");
            }
        }
    }
}
```

### Using foreach Loop to Access SortedList Elements
We can also use a for-each loop to access the key/value pairs of the SortedList in C# as follows:

```C#
using System;
using System.Collections;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList sl = new SortedList();
            sl.Add(1, "One");
            sl.Add(2, "Two");
            sl.Add(3, "Three");
            sl.Add(50, 5);
            sl.Add(100, null);

            foreach(DictionaryEntry item in sl)
            {
                Console.WriteLine($"Key: {item.Key}, Value: {item.Value}");
            }
        }
    }
}
```

## Adding Element Using Collection Initializer Syntax
You can add elements to a SortedList using the collection initializer syntax as shown:

```C#
using System;
using System.Collections;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList sortedList = new SortedList()
            {
                {"one", 1}, {"two", 2}, {"three", 3}, {"four", 4}
            };
            foreach (DictionaryEntry item in sortedList)
            {
                Console.WriteLine($"Key: {item.Key}, Value: {item.Value}");
            }
        }
    }
}
```

## How to Remove Elements From a SortedList Collection
The Non-Generic SortedList Collection Class in C# provides the following methods to remove elements from SortedList.

1. **Remove(object key)**: This method is used to remove the element with the specified key from a 
SortedList object. The parameter key specifies the element to remove.
2. **RemoveAt(int index)**: This method is used to remove the element at the specified index of a 
SortedList object. The parameter index specifies the element to remove. It is 0 based Index.
3. **Clear()**: This method is used to remove all elements from a SortedList object.

```C#
using System;
using System.Collections;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList sortedList = new SortedList()
            {
                {"one", 1}, {"two", 2}, {"three", 3}, {"four", 4}
            };
            sortedList.Remove("two");
            sortedList.RemoveAt(2);
            foreach (DictionaryEntry item in sortedList)
            {
                Console.WriteLine($"Key: {item.Key}, Value: {item.Value}");
            }
        }
    }
}
```

## How to check the availability of key/value pairs in a SortedList in C#
If you want to check whether the key/value pair exists or not in the SortedList, then you can use the 
following methods of the SortedList class.

- **Contains(object key)**: This method is used to determine whether the SortedList object contains a specific 
key. The parameter key to locate in the SortedList object. It returns true if the SortedList object contains
an element with the specified key; otherwise, false. If the key is null, then it will throw 
System.ArgumentNullException.
- **ContainsKey(object key)**: This method is used to determine whether a SortedList object contains a specific key. 
The parameter key to locate in the SortedList object. It returns true if the SortedList object contains an 
element with the specified key; otherwise, false. If the key is null, then it will throw System.ArgumentNullException.
- **ContainsValue(object value)**: This method is used to determine whether a SortedList 
object contains a specific value. The parameter value to locate in the SortedList object. The value can be 
null. It returns true if the SortedList object contains an element with the specified value; otherwise, false.

```C#
using System;
using System.Collections;

namespace SortedListCollection
{
    internal class SortedListCollection
    {
        static void Main(string[] args)
        {
            SortedList sortedList = new SortedList()
            {
                {"one", 1}, {"two", 2}, {"three", 3}, {"four", 4}
            };
            
            Console.WriteLine(sortedList.Contains("one")); // True
            Console.WriteLine(sortedList.ContainsKey("two")); // True
            Console.WriteLine(sortedList.ContainsKey("hello")); // False
            Console.WriteLine(sortedList.ContainsValue(500)); // False
            Console.WriteLine(sortedList.ContainsValue(4)); // True
            Console.WriteLine(sortedList.ContainsValue("hello world")); // False
            foreach (DictionaryEntry item in sortedList)
            {
                Console.WriteLine($"Key: {item.Key}, Value: {item.Value}");
            }
        }
    }
}
```