# Generic List Collection

The Generic `List<T>` in C# is a Collection Class that belongs to `System.Collections.Generic` namespace.

This Generic `List<T>` Collection Class represents a strongly typed list of objects which can be 
accessed by using the integer index which is starting from 0.

It also provides lots of methods that can be used for searching, sorting, and manipulating the list of items.

The size of the collection grows automatically when we add items to the collection.

## How to Create a Generic List Collection
The Generic `List<T>` is present in `System.Collections.Generic` namespace.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
        }
    }
}
```

## How to Add Elements to a Generic List Collection
To add elements to a generic list, you can either use the `Add` method or collection initializer

### Adding Elements Using the `Add` Method
The `Add(T item)` method is used to add an element to the end of the Generic List. Here, the parameter item
specifies the object to be added to the end of the Generic List. The value can be null for a reference type.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");
        }
    }
}
```

### Adding Elements Using Collection Initializer Syntax
It is possible to add elements using the collection initializer syntax:

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>
            {
                "Germany",
                "France",
                "Kenya",
                "Russia",
                "India"
            };
        }
    }
}
```

## How to Access Elements of a Generic List Collection
We can use integer indexes or a loop.

### Using Index to Access Generic List Collection
We can access the individual elements of the List Collection in C# by using the integral index. In this 
case, we just need to specify the index position of the element that we want to access. The Index is 0 Based.
If the specified index is not present, then the compiler will throw an exception.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");

            Console.WriteLine(countries[0]);
            Console.WriteLine(countries[2]);
        }
    }
}
```

### Using a Loop
You can use either for loop or foreach loop.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");

            for (int i = 0; i < countries.Count; i++)
            {
                Console.WriteLine(countries[i]);
            }

            foreach(string country in countries)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

## How to Insert Elements at a Specific Position in a Generic List Collection
If you want to insert an element at a specific position, you can use the `Insert(int index, T item)` method.

This method is used to insert an element into the Generic List at the specified index. 

Here, the parameter index specifies the zero-based index at which an item should be inserted and the parameter 
item specifies the object to insert. The value can be null for reference types. If the index is less than 
0 or the index is greater than Generic List Count, then it will throw ArgumentOutOfRangeException.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");

            countries.Insert(0, "Croatia");
            countries.Insert(3, "Morocco");
            countries.Insert(4, "USA");

            foreach(string country in countries)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

## How to Check the Availability of an Item in a List Collection
If you want to check whether an element exists or not in the Generic List Collection, then you need to use the 
`Contains` method.

The `Contains(T item)` method of the Generic List Collection Class is used to check if the given item is present 
in the List or not. 

The parameter item specifies the object to locate in the Generic List. The value can be null for reference 
types. It returns true if the item is found in the Generic List; otherwise, false.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");

            Console.WriteLine(countries.Contains("Germany")); // True
            Console.WriteLine(countries.Contains("Monnaco")); // False
        }
    }
}
```

## How to Remove Elements from a Generic List Collection
You can use one of the following methods:

### `Remove(T item)`

This method is used to remove the first occurrence of a specific object from the Generic List. 

Here, the parameter item specifies the object to remove from the Generic List. 

It returns true if the item is successfully removed; otherwise, false. 

This method also returns false if the item was not found in the Generic List.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");

            countries.Remove("France");
            countries.Remove("Russia");

            foreach(string country in countries)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

### `RemoveAt(int index)`

This method is used to remove the element at the specified index of the Generic List. Here, the 
parameter `index` is the zero-based index of the element to remove. If the index is less than 0 or the index 
is equal to or greater than Generic List Count, then it will throw `ArgumentOutOfRangeException`.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");

            countries.RemoveAt(0);
            countries.RemoveAt(3);

            foreach(string country in countries)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

### `RemoveRange(int index, int count)`
This method is used to remove a range of elements from the Generic List. Here, the parameter index is 
the zero-based starting index of the range of elements to remove and the parameter count is the number 
of elements to remove. 

If the index is less than 0 or the count is less than 0, then it will throw ArgumentOutOfRangeException. If 
the index and count do not denote a valid range of elements in the Generic List, then it will throw `ArgumentException`.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");

            // Remove 3 elements starting from index 0
            countries.RemoveRange(0, 3);

            foreach(string country in countries)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

### `RemoveAll(Predicate<T> match)`
This method is used to remove all the elements that match the conditions defined by the specified predicate.

Here, the parameter match specifies the predicate delegate that defines the conditions of the elements 
to remove. It returns the number of elements removed from the Generic List. If the parameter match is null, 
then it will throw ArgumentNullException.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");

            // Remove all countries whose length is less than 7
            countries.RemoveAll(countryName => countryName.Length < 7);

            foreach(string country in countries)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

### `Clear()`
This method is used to remove all elements from the Generic List.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");

            countries.Clear();

            foreach(string country in countries)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

## How to Find an Element in a Generic List Collection

If you want to find elements in a generic list collection, you can use one of the following methods:

### `Find()`
The Find() method is used to find the first element from a list based on a condition that is specified by a 
lambda expression.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");
            countries.Add("Indonesia");

            string country = countries.Find(countryName => countryName[0] == 'I');
            Console.WriteLine(country); // India
        }
    }
}
```

### `FindLast()`
The FindLast() method is used to search for an element that matches the conditions specified by a predicate.

If it found any elements with that specified condition then it returns the Last matching element from the list.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");
            countries.Add("Indonesia");

            string country = countries.FindLast(countryName => countryName[0] == 'I');
            Console.WriteLine(country); // Indonesia
        }
    }
}
```

### `FindAll()`
The `FindAll()` method is used to retrieve all the elements from a list that matches the conditions 
specified by a predicate.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");
            countries.Add("Indonesia");

            List<string> result = countries.FindAll(country => country[0] == 'I');
            foreach(string country in result)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

### `FindIndex()`
The `FindIndex()` method is used to return the index position of the first element that matches the conditions 
specified by a predicate.

This method returns -1 if an element that matches the specified conditions is not found.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");
            countries.Add("Indonesia");

            int idx = countries.FindIndex(c => c[0] == 'I');
            Console.WriteLine(idx); // 4
        }
    }
}
```

### `FindLastIndex()`
The FindLastIndex() Method searches for an element in the list that matches the condition specified by the 
lambda expression and then returns the index of the last occurrence of the item within the list.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");
            countries.Add("Indonesia");

            int idx = countries.FindLastIndex(c => c[0] == 'I');
            Console.WriteLine(idx); // 5
        }
    }
}
```

### `Exists()`
The `Exists()` method is used to check or determine whether an item exists or not in a list based on a condition. 

If the item exists then it will return true else it will return false.

In the example below, we are checking whether there's any country whose length is greater than 10 characters.

```C#
using System;
using System.Collections.Generic;

namespace GenericList
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<string> countries = new List<string>();
            countries.Add("Germany");
            countries.Add("France");
            countries.Add("Kenya");
            countries.Add("Russia");
            countries.Add("India");
            countries.Add("Indonesia");

            bool exists = countries.Exists(c => c.Length > 10);
            Console.WriteLine(exists); // False
        }
    }
}
```