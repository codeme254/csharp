# Non-Generic Hashtable Collection

In the case of Array and ArrayList in C#, we access the elements from the collection using the index position. 
The index position of the elements starts from zero (0) to the number of elements – 1. But, it is very difficult 
for us to remember the index position of the element in order to access the values.

If you have a huge number of elements in a collection, then it is very difficult to remember the 
index position of each element. So, it would not be nice, instead of using the index position of the element,
we can access the elements by using a key.

This is where Hashtable in C# comes into the picture.

## What is a Hashtable
The Hashtable in C# is a Non-Generic Collection that stores the element in the form of "Key-Value Pairs".

The data in the Hashtable are organized based on the hash code of the key. The key in the HashTable is defined by 
us and more importantly, that key can be of any data type. Once we created the Hashtable collection, then we 
can access the elements by using the keys.

The Hashtable class comes under the System.Collections namespace.

The Hashtable computes a hash code for each key. Then it uses that hash code to look up the elements very quickly 
which increases the performance of the application.

## Hashtable Characteristics
1. The Hashtable Collection Class in C# stores the elements in the form of key-value pairs.
2. Hashtable Class belongs to System.Collection namespace i.e. it is a Non-Generic Collection class.
3. It implements the IDictionary interface.
4. The Keys can be of any data type but they must be unique and not null.
5. The Hashtable accepts both null and duplicate values.
6. We can access the values by using the associated key.
7. The capacity of a Hashtable is the number of elements that a Hashtable can hold.
8. A hashtable is a non-generic collection, so we can store elements of the same type as well as of different types.

## How to Create a Non-Generic Hashtable
The Non-Generic Hashtable class in C# provides 16 different types of constructors that we can use to create a
hashtable as shown in the below image. You can use any of the overloaded constructors to create an instance 
of Hashtable.

![Hashtable Constructors](collections-hashtable.png)

Here, we are going to use the overloaded version which does not take any parameter i.e. the following Hashtable 
constructor:
```C#
public Hashtable()
```

```C#
using System;
using System.Collections;

namespace HashtableCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Hashtable ht = new Hashtable();
        }
    }
}
```

## How to Add Elements Into a Hashtable Collection
Now, if you want to add elements i.e. a key/value pair into the hashtable, then you need to use 
`Add()` method of the Hashtable class.

It takes in two parameters:
- The first parameter is the key (can be of any data type)
- The second parameter is the value (can be of any data type)

```C#
using System;
using System.Collections;

namespace HashtableCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Hashtable employeeDetails = new Hashtable();
            employeeDetails.Add("Id", 1000);
            employeeDetails.Add("FirstName", "John");
            employeeDetails.Add("LastName", "Doe");
            employeeDetails.Add("Age", 35);
            employeeDetails.Add("EmailAddress", "john@company.com");
        }
    }
}
```

It is also possible to add elements to a hashtable using collection-initializer syntax as follows:

```C#
using System;
using System.Collections;

namespace HashtableCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Hashtable employee = new Hashtable()
            {
                {"Id", 1000},
                {"FirstName", "John"},
                {"LastName", "Doe"},
                {"Age", 35},
                {"EmailAddress", "john@company.com"}
            };
        }
    }
}
```

## How to Access Elements of a Non-Generic Hashtable Collection
You can access the individual value of the Hashtable in C# by using the keys. In this case, we need to pass the 
key as a parameter to find the respective value. If the specified key is not present, then the compiler will 
throw an exception.

```C#
using System;
using System.Collections;

namespace HashtableCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Hashtable employeeDetails = new Hashtable();
            employeeDetails.Add("Id", 1000);
            employeeDetails.Add("FirstName", "John");
            employeeDetails.Add("LastName", "Doe");
            employeeDetails.Add("Age", 35);
            employeeDetails.Add("EmailAddress", "john@company.com");

            Console.WriteLine(employeeDetails["FirstName"]);
            Console.WriteLine(employeeDetails["LastName"]);
        }
    }
}
```

## Using foreach Loop on a Hashtable
We can also use a for-each loop to access the key/value pairs of a Hashtable collection in C#.

Elements of a hashtable are stored as DictionaryEntry objects.

```C#
using System;
using System.Collections;

namespace HashtableCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Hashtable employeeDetails = new Hashtable();
            employeeDetails.Add("Id", 1000);
            employeeDetails.Add("FirstName", "John");
            employeeDetails.Add("LastName", "Doe");
            employeeDetails.Add("Age", 35);
            employeeDetails.Add("EmailAddress", "john@company.com");

            // Adding elements using collection initializer syntax
            Hashtable employee = new Hashtable()
            {
                {"Id", 1000},
                {"FirstName", "John"},
                {"LastName", "Doe"},
                {"Age", 35},
                {"EmailAddress", "john@company.com"}
            };

            Console.WriteLine(employeeDetails["FirstName"]);
            Console.WriteLine(employeeDetails["LastName"]);

            foreach(DictionaryEntry entry in employeeDetails)
            {
                Console.WriteLine($"{entry.Key} - {entry.Value}");
            }
        }
    }
}
```

## Adding Values to a Hashtable Using Indexer
In order to add value to a Hashtable with an indexer, we need to use square brackets after the Hashtable name. 

This is because a Hashtable works with key/value pairs, we must have to specify both key and value while adding 
the elements. 

The key is specified between square brackets.

```C#
using System;
using System.Collections;

namespace HashtableCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Hashtable employeeDetails = new Hashtable();
            employeeDetails.Add("Id", 1000);
            employeeDetails.Add("FirstName", "John");
            employeeDetails.Add("LastName", "Doe");
            employeeDetails.Add("Age", 35);
            employeeDetails.Add("EmailAddress", "john@company.com");

            // Adding elements using the indexer
            employeeDetails["Salary"] = 30000;
            employeeDetails["Gender"] = "Male";

            foreach(DictionaryEntry entry in employeeDetails)
            {
                Console.WriteLine($"{entry.Key} - {entry.Value}");
            }

        }
    }
}
```

## Updating Values of a Hashtable Using Indexer
We can update the values of a Hashtable using indexer syntax.

```C#
using System;
using System.Collections;

namespace HashtableCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Hashtable employeeDetails = new Hashtable();
            employeeDetails.Add("Id", 1000);
            employeeDetails.Add("FirstName", "John");
            employeeDetails.Add("LastName", "Doe");
            employeeDetails.Add("Age", 35);
            employeeDetails.Add("EmailAddress", "john@company.com");

            // Adding elements using the indexer
            employeeDetails["Salary"] = 30000;
            employeeDetails["Gender"] = "Male";

            // Updating values using indexer
            employeeDetails["FirstName"] = "Jack"; // Updates from John to Jack
            employeeDetails["LastName"] = "Smith"; // Updates from Doe to Smith

            foreach(DictionaryEntry entry in employeeDetails)
            {
                Console.WriteLine($"{entry.Key} - {entry.Value}");
            }
        }
    }
}
```

## How to Check the Availability of a Key/Value Pair in a Hashtable in C#
If you want to check whether the key/value pair exists or not in the Hashtable, then you can use the following
methods of the Hashtable class.

### Contains(object key)
The Contains(object key) method of the Hashtable is used to check whether the Hashtable contains a specific key.

It takes in one parameter - the key to locate in the hashtable.

It returns true if the hashtable contains an element with the specified key, otherwise it returns false.

If the key is null, it throws System.ArgumentNullException

### Contains(object value)
The ContainsValue(object value) Method of the Hashtable class is used to check if a value is present in the 
Hashtable or not.

It takes in one parameter - the value to locate in the hashtable.

If the given value is present in the collection then it will return true else it will return false.

```C#
using System;
using System.Collections;

namespace HashtableCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Hashtable employeeDetails = new Hashtable();
            employeeDetails.Add("Id", 1000);
            employeeDetails.Add("FirstName", "John");
            employeeDetails.Add("LastName", "Doe");
            employeeDetails.Add("Age", 35);
            employeeDetails.Add("EmailAddress", "john@company.com");

            // Checking for existence of keys
            Console.WriteLine(employeeDetails.Contains("Id"));// True
            Console.WriteLine(employeeDetails.Contains("Location")); // False

            // Checking for existence of values
            Console.WriteLine(employeeDetails.ContainsValue("John")); // True
            Console.WriteLine(employeeDetails.ContainsValue("Sales and Marketing")); // False
        }
    }
}
```

## How to Remove Elements From a Hashtable
You can use the `Remove(object key)` method.

The method is used to remove the element with the specified key from the Hashtable. Here, the parameter key 
specifies the element to remove.

It throws the KeyNotfoundException if the specified key is not found in the Hashtable, so check for an existing 
key using the ContainsKey() method before removing it.

```C#
using System;
using System.Collections;

namespace HashtableCollection
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Hashtable employeeDetails = new Hashtable();
            employeeDetails.Add("Id", 1000);
            employeeDetails.Add("FirstName", "John");
            employeeDetails.Add("LastName", "Doe");
            employeeDetails.Add("Age", 35);
            employeeDetails.Add("EmailAddress", "john@company.com");

            if (employeeDetails.ContainsKey("Age"))
            {
                employeeDetails.Remove("Age");
            }

            foreach(DictionaryEntry entry in employeeDetails)
            {
                Console.WriteLine($"{entry.Key} - {entry.Value}");
            }
        }
    }
}
```

If you want to remove all the elements of a hashtable, you can use the `Clear` method.

For example: `employeeDetails.Clear()`.