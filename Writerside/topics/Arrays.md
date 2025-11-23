# Arrays

As we know a primitive type variable such as int, double, bool, etc. can hold only a single value at any
given point in time.

For example, `int Number = 10;`. Here the variable Number holds a value of 10. As per your business requirement, 
if you want to store 100 integer values, then you need to create 100 integer variables in your program which
is not a good programming approach as it will take lots of time as well as your code becomes bigger.

We can overcome this problem by using the concept called Arrays, and Arrays are not new in C#, they are existing 
in other programming languages such as C, C++, Java, etc. Using Arrays, instead of creating 100 variables to hold 
100 values, we can create a single variable which can hold 100 values.

## What is an Array in C#
An array is a collection of similar data elements.

It is a collection of similar types of values that are stored in a contiguous memory location under a single name.

## Types of Arrays in C#
C# supports two types of arrays. They are:
- **Single dimensional arrays**
- **Multi-dimensional arrays**

In the Single dimensional array, the data is arranged in the form of a row whereas in the multidimensional arrays,
the data is arranged in the form of rows and columns.

Again, the multidimensional arrays are of two types:
- **Jagged arrays**: whose rows and columns are not equal.
- **Rectangular arrays**: The array whose columns are equal from row to row.

We can access the values of an array using the index positions whereas the array index starts from 0 which 
means the first item of an array will be stored at the 0th position and the position of the last item of an 
array will be the total number of the item – 1.

In this section, we will discuss single dimensional arrays, in the next section, we will discuss multidimensional 
arrays.

## How to Declare an Array in C#
The general syntax for declaring an array in C# is:
```
<data type>[] VariableName = new <data type>[size of the array];
```

For example:
```C#
int[] A = new int[5];
```
Here we have created an array with the name A and with a size of 5. So, you can store 5 values with the same name A.

## How to Declare and Initialize an Array in the Same Statement
Just like declaring and initializing a normal variable in a single statement, we can also do the same for an array if 
we want to hardcode the input of the array.

Here is an example:
```C#
int[] A = {1, 2, 3, 4, 5};
```

<note>
In C#, the arrays can be declared as fixed-length or dynamic. The Fixed length array means we can store a fixed 
number of elements while in the case of the dynamic array, the size of the array automatically increases as 
we add new items to the array. The Arrays in C# are reference types that are derived from the 
<strong>System.Array</strong> class.
</note>

## How to Access Array Elements
We can access array elements using indexes.

The first element has an index of 0 and the last element has an index of the number of items in the array minus 1.

The index of an array is basically a pointer that is used to indicate which element in the array will be used.

To access an array element, use its index number within square brackets to the right of the array name.

```C#
using System;

namespace Arrays
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] empno = { 1001, 1002, 5003, 1004, 2005 };
            Console.WriteLine(empno[0]); // 1001
            Console.WriteLine(empno[1]); // 1002
        }
    }
}
```

## Assigning Values to Array in C#
By writing `int[] n={1,2,3};` we are declaring and assigning values to the array at the same time, thus initializing it.

But when we declare an array like `int[] n = new int[3];`, we need to assign values to it separately. 
Because `int[] n = new int[3];` will allocate space for 3 integers in the heap memory but there are no 
values in that space. To initialize it, assign a value to each of the elements of the array using its index 
position as shown below.

```C#
using System;

namespace Arrays
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string[] students = new string[5];
            students[0] = "John";
            students[1] = "Ruth";
            students[2] = "Jane";
            students[3] = "Kane";
            students[4] = "June";
        }
    }
}
```

## Number of Elements in an Array
You can get the number of elements in an array using the `Length` property on the array name:
```C#
using System;

namespace Arrays
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string[] students = new string[5];
            students[0] = "John";
            students[1] = "Ruth";
            students[2] = "Jane";
            students[3] = "Kane";
            students[4] = "June";
            Console.WriteLine(students.Length); // 5
        }
    }
}
```

## Looping Over an Array With The For Loop

```C#
using System;

namespace Arrays
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string[] students = new string[5];
            students[0] = "John";
            students[1] = "Ruth";
            students[2] = "Jane";
            students[3] = "Kane";
            students[4] = "June";
            Console.WriteLine(students.Length);

            for (int i = 0; i < students.Length; i++)
            {
                Console.WriteLine($"students[{i}] is {students[i]}");
            }
        }
    }
}
```

## For Each Loop in C#
The For Each loop is specially designed in C# for accessing the values from a collection like an Array, 
ArrayList, List, etc.

When we use a for-each loop for accessing the values of an array or collection, we only require to hand over 
the array or collection to the loop which does not require any initialization, condition, or iteration. The loop 
itself starts its execution by providing access to each and every element present in the array or collection 
starting from the first up to the last element in sequential order.

### Difference Between For Each Loop and For Loop When Working With Arrays
In the case of for loop in C#, the loop variable refers to the index of an array whereas, in the case of a for-each 
loop, the loop variable refers to the values of the array.

Irrespective of the values stored in the array, the loop variable must be of type int in case of for loop. 
The reason for this is, here the loop variable is referring to the index position of the array. Coming to the 
for-each loop, the data type of the loop variable must be the same as the type of the values stored in the array. 
For example, if you have a string array then the loop variable must be of type string in case of the for-each 
loop and int in case of a for loop in C#.

```C#
using System;

namespace Arrays
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string[] students = new string[5];
            students[0] = "John";
            students[1] = "Ruth";
            students[2] = "Jane";
            students[3] = "Kane";
            students[4] = "June";
            Console.WriteLine(students.Length);

            for (int i = 0; i < students.Length; i++)
            {
                Console.WriteLine($"students[{i}] is {students[i]}");
            }

            foreach(string student in students)
            {
                Console.WriteLine(student);
            }
        }
    }
}
```

The for loop in C# can be used both for accessing values from an array as well as assigning values to an array 
whereas the for-each loop in C# can only be used for accessing the values from an array but not for assigning 
values into an array.

## Array Class in C#
The Array class in C# is a predefined class that is defined inside the System namespaces.

This class is working as the base class for all the Arrays in C#.

The Array class provides a set of members (methods and properties) to work with the arrays such as creating, 
manipulating, searching, reversing, and sorting the elements of an array, etc.

The array class provides the following properties and methods:
- `Sorty(array)`: sorting the array elements.
- `Revers(array)`: reversing the array elements.
- `Copy(source, destination, number_of_elements)`: Copying some of the elements or all elements from an old array to 
a new array
- `GetLength(int32)`: A 32-bit integer that represents the number of elements in the specified dimension.
- `Length`: It Returns the total number of elements in all the dimensions of the Array; zero if there are no elements
in the array.

```C#
using System;

namespace Arrays
{
    internal class ArrayMethodsAndProperties
    {
        static void Main(string[] args)
        {
            int[] Numbers = { 17, 23, 4, 59, 27, 36, 96, 9, 1, 3 };
            
            // Number of elements in an array
            Console.WriteLine(Numbers.Length); // 10

            // Printing original array elements using a for loop
            Console.WriteLine("Array elements before sorting");
            for (int i = 0; i <  Numbers.Length; i++)
            {
                Console.WriteLine(Numbers[i]);
            }

            // Sorting Array Elements
            Array.Sort(Numbers);
            // Printing array elements using the for each loop
            Console.WriteLine("\nSorted array elementts");
            foreach(int number in Numbers)
            {
                Console.WriteLine(number);
            }

            // Reversing array elements
            Array.Reverse(Numbers);
            Console.WriteLine("\nReversed Array elements");
            foreach(int number in Numbers)
            {
                Console.WriteLine(number);
            }

            // COPYING ARRAY ELEMENTS
            // ======================
            // Copying some elements from the old array to a new array
            // We will declare the array with size 10 but we will only copy 5 elements
            // The rest 5 elements in the new array will take a default value, 0 for the case of integers
            int[] NewNumbers = new int[10];
            Array.Copy(Numbers, NewNumbers, 5);
            Console.WriteLine("\nNew array elements");
            foreach(int number in NewNumbers)
            {
                Console.WriteLine(number);
            }

            Console.WriteLine($"\nLength of the new array using Length property: {NewNumbers.Length}");
            Console.WriteLine($"Length of the new array using the GetLength property: {NewNumbers.GetLength(0)}");
        }
    }
}
```

## Implicitly Typed Arrays
When we declare an array using the `var` keyword, then such an array is called an **implicitly typed array**:

```C#
using System;

namespace Arrays
{
    internal class Program
    {
        static void Main(string[] args)
        {
            var Numbers = new[] { 10, 20, 30, 40, 50 };
            foreach(var number in Numbers)
            {
                Console.WriteLine(number);
            }
        }
    }
}
```