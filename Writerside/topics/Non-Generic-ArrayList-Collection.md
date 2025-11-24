# Non-Generic ArrayList Collection

The ArrayList in C# is a non-generic collection class that works like an array but provides the facilities such as:
- Dynamic Resizing
- Adding elements anywhere including in the middle.
- Removing elements anywhere including from the middle.

An ArrayList is used to create a dynamic array means the size of the array is increased r decreased automatically 
according to the requirement of our program.

There's no need to specify the size of the array in an array list.

**In ArrayList we can store elements of the same or different data types.**

## Properties of ArrayList Class
1. The Elements can be added and removed from the Array List collection at any point in time.
2. The ArrayList is not guaranteed to be sorted.
3. The capacity of an ArrayList is the number of elements the ArrayList can hold.
4. Elements in this collection can be accessed using an integer index. Indexes in this collection are zero-based.
5. It allows duplicate elements.

## How to Create an ArrayList
C# provides the following three constructors which we can use to create an instance of the ArrayList class:
- **ArrayList()**: The method is used to initialize a new instance of the ArrayList class that is empty and has 
the default initial capacity.
- **ArrayList(ICollection c)**: The method is used to initialize a new instance of the ArrayList class that 
contains elements copied from the specified collection and that have the same initial capacity as the number 
of elements copied. The parameter c specifies the Collection whose elements are copied to the new list.
- **ArrayList(int capacity)**: The method is used to initialize a new instance of the ArrayList class that contains
elements copied from the specified collection and that have the same initial capacity as the number of elements 
copied. The parameter c specifies the Collection whose elements are copied to the new list.

First, we need to import the System.Collections namespace and then we can create an instance of ArrayList by using 
the first constructor as follows.

```C#
using System;
using System.Collections;

namespace ArrayListClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ArrayList arraylist = new ArrayList();
        }
    }
}
```

Note: you can also use the var keyword:
```C#
var arrayList = new ArrayList();
```

## How to Add Elements into ArrayList in C#
We can add elements to an ArrayList using one of the following ways:
- Object initializer syntax
- Using the `Add()` method

Most important point is that we can add multiple different types of elements in an ArrayList.

### Adding Elements Using the Object Initializer Syntax

```C#
using System;
using System.Collections;

namespace ArrayListClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ArrayList arraylist = new ArrayList()
            {
                102, "Jane", 99.448, true, false, null
            };

            foreach(var item in arraylist)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

### Adding Elements Using the Add Method

```C#
using System;
using System.Collections;

namespace ArrayListClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ArrayList myList = new ArrayList();
            myList.Add(101);
            myList.Add("Jane");
            myList.Add("June");
            myList.Add(true);
            myList.Add(false);
            myList.Add(4.555);

            foreach(var item in myList)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

## How to Access Elements of an ArrayList
We can use indexes to access elements of an ArrayList.

While adding the elements into ArrayList, it will automatically cast the elements into object types and then store 
them in the collection. So, while accessing the elements an explicit casting to the appropriate types is required
unless you use the var keyword.

```C#
using System;
using System.Collections;

namespace ArrayListClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ArrayList myList = new ArrayList();
            myList.Add(101);
            myList.Add("Jane");
            myList.Add("June");
            myList.Add(true);
            myList.Add(false);
            myList.Add(4.555);

            int firstItem = (int)myList[0];
            string secondItem = (string)myList[1];
            // no need for casting when using the var keyword
            var thirditem = myList[2];
            var fourthItem = myList[3];
            Console.WriteLine($"{firstItem}, {secondItem}, {thirditem}, {fourthItem}");
        }
    }
}
```

## Number of Items in an ArrayList
You can get the number of items in an ArrayList using the `Count` property.

This property returns the total number of items in an ArrayList.

```C#
using System;
using System.Collections;

namespace ArrayListClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ArrayList myList = new ArrayList();
            myList.Add(101);
            myList.Add("Jane");
            myList.Add("June");
            myList.Add(true);
            myList.Add(false);
            myList.Add(4.555);

            Console.WriteLine(myList.Count); // 6
        }
    }
}
```

## Inserting Elements Into a Specified Position
The Add method will add the element at the end of the collection i.e. after the last element.

If you want to add an element at a specified position, you need to use the `Insert()` method.

It takes in two parameters:
- The first parameter is the index at which the value should be inserted.
- The second parameter is the value to be inserted.

```C#
using System;
using System.Collections;

namespace ArrayListClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            var lst = new ArrayList()
            {
                101, 102, "John", "Ann", true
            };
            lst.Insert(0, "First Element");
            lst.Insert(2, "Third Element");

            foreach (var item in lst)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

## Inserting an ArrayList Into Another ArrayList
If we have an ArrayList and we want to insert it into another ArrayList, we can use the `InsertRange()` method.

The method inserts the elements of a collection to the given array list at the specified index.

It takes two parameters:
- The first parameter is the index to insert
- The second parameter is the collection to insert at the index above.

```C#
using System;
using System.Collections;

namespace ArrayListClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ArrayList lst1 = new ArrayList() { 1, 2, 3, 4, 5 };
            Console.WriteLine("Array List Elements Before");
            foreach(var item in lst1)
            {
                Console.WriteLine(item);
            }

            ArrayList lst2 = new ArrayList() { 6, 7, 8, 9, 10 };
            lst1.InsertRange(5, lst2);

            Console.WriteLine("Array List Elements After");
            foreach(var item in lst1)
            {
                Console.WriteLine(item);
            }
        }
    }
}
```

## How to Remove Elements From an ArrayList
If you want to remove elements from an ArrayList, you can use one of the following methods:
1. **Remove(object? obj)**: This method is used to remove the first occurrence of a specific object from the 
System.Collections.ArrayList. The parameter obj specifies the Object to remove from the ArrayList. 
The value can be null.
2. **RemoveAt(int index)**: This method is used to remove the element at the specified index of the 
ArrayList. The parameter index specifies the index position of the element to remove.
3. **RemoveRange(int index, int count)**: This method is used to remove a range of elements from the ArrayList. 
The parameter index specifies the starting index position of the range of elements to remove and the 
parameter count specifies the number of elements to remove.

```C#
using System;
using System.Collections;

namespace ArrayListClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ArrayList countries = new ArrayList()
            {
                "USA", "Kenya", "India", "Morocco", "Libya", "UK", "China", "USA"
            };

            // Remove the first occurence of an element
            countries.Remove("USA");
            foreach(var country in countries)
            {
                Console.WriteLine(country);
            }
            Console.WriteLine();

            // Remove an item at a specific index
            countries.RemoveAt(2);
            foreach (var country in countries)
            {
                Console.WriteLine(country);
            }
            Console.WriteLine();

            // Remove a range of elements
            countries.RemoveRange(3, 2);
            foreach (var country in countries)
            {
                Console.WriteLine(country);
            }
        }
    }
}
```

## Remove All Elements of an ArrayList
If you want to remove all elements or clear all the elements from the ArrayList, then you can use the 
`Clear()` method of the ArrayList class

Note: the method does not reduce the Capacity of the given ArrayList, the capacity is the number of elements an
ArrayList can hold, Count is the number of items currently in an ArrayList.

```C#
using System;
using System.Collections;

namespace ArrayListClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ArrayList countries = new ArrayList()
            {
                "USA", "Kenya", "India", "Morocco", "Libya", "UK", "China", "USA"
            };

            Console.WriteLine(countries.Capacity); // 8
            Console.WriteLine(countries.Count); // 8
            countries.Clear();
            Console.WriteLine("After Clearing");
            Console.WriteLine(countries.Capacity); // 8
            Console.WriteLine(countries.Count); // 0
        }
    }
}
```

## How to Check Whether an Element is Present in an ArrayList
In order to check whether an element exists or not in ArrayList, we need to use the `Contains()` method of the
ArrayList non-generic collection class in C#. It returns true if exists otherwise returns false.

It takes one parameter - the item we are checking for in the ArrayList.

```C#
using System;
using System.Collections;

namespace ArrayListClass
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ArrayList countries = new ArrayList()
            {
                "USA", "Kenya", "India", "Morocco", "Libya", "UK", "China", "USA"
            };
            
            Console.WriteLine($"{countries.Contains("Kenya")}"); // true
            Console.WriteLine($"{countries.Contains("Monnaco")}"); // false
        }
    }
}
```

## Difference Between Array and ArrayList
### Array
- Fixed length
- Cannot insert in the middle
- Cannot delete from the middle
- Type-safe, so we can store only similar types of data based on the data type
- Boxing and unboxing are not required

### ArrayList
- Variable length
- Can insert elements in the middle of the collection
- Can delete elements from the middle of the collection
- Not type-safe, so we can store any type of data
- Boxing and unboxing is required as it is operated on the object data type