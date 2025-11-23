# 2D Arrays

The arrays which store the elements in the form of rows and columns are called Two-Dimensional Array in C#.

The two-dimensional array which is also called a multidimensional array is of two types in C#.

They are as follows:
- **Rectangular array**: The array whose columns are equal from row to row.
- **Jagged array**: The array whose rows and columns are not equal is called a jagged array

## Rectangular Array
A two-dimensional array is an array in which each element is referred to by two indexes.

Element in the 2D array is stored in the matrix form. The first index shows the row of the matrix and the second
index shows the column of the matrix.

A 2D array is created as follows:
```C#
int[,] A = new int[3, 4];
```

If we created it like this, then the 2D array is created with 3 rows and 4 columns where the name of the array is A.

A 2D array can be initialized as follows:
```C#
int[,] A = {{2, 5, 9}, {6, 9, 15}};
```

This is the declaration + initialization of a 2 Dimensional array in C#. Here 2,5,9 is the 1st row and 6,9,15 is 
the 2nd row.

You will also see the following convention from time to time which is similar to what we have above:

```C#
int[,] A = new int[2,3]
{
       {2, 5, 9},{6, 9, 15}
};
```

For accessing all the elements of the rectangle 2D Array in C#, we require a nested for loop, one for loop 
for accessing the rows, and another for loop for accessing the columns.

## Example to understand 2D Rectangular array
In the below example, we are creating a two-dimensional integer array with 4 Rows and 5 Columns. Then we are 
printing the values of the 2D Array using a for each loop to see what default it stores.

Using nested for loop, we are assigning the values to the 2D Array.

Note: **GetLength(int dimension)** is used to get the number of elements in a specific dimension of an array. In the
example below, when we pass 0 to the method, it gets the length of the rows and when we pass 1 it gets the length
of the columns.

```C#
using System;

namespace Rectangular2DArray
{
    internal class Rectangular2DArray
    {
        static void Main(string[] args)
        {
            int[,] RectangleArray = new int[4, 5];
            // Printing the values of 2D array using a foreach loop
            // It will print the defaultt values as we have not yet assigned
            // any values to the array
            foreach(int i in RectangleArray)
            {
                Console.WriteLine(i);
            }

            // Assigning values to the 2D array using nestetd for loop
            // GetLength(0): returns the size of the row
            // GetLength(1): returns the length of the column
            int a = 0;
            for (int i = 0; i < RectangleArray.GetLength(0); i++)
            {
                for (int j = 0;  j < RectangleArray.GetLength(1); j++)
                {
                    a += 5;
                    RectangleArray[i, j] = a;
                }
            }

            foreach (int i in RectangleArray)
            {
                Console.WriteLine(i);
            }
        }
    }
}
```

In the example below, we are declaring and initializing a 2D rectangular array in the same line.

```C#
using System;

namespace Rectangular2DArray
{
    internal class Rectangular2DArray
    {
        static void Main(string[] args)
        {
            int[,] NumbersArray = { { 11, 12, 13, 14 }, { 21, 22, 23, 24 }, { 31, 32, 33, 34 } };

            for (int i = 0; i <  NumbersArray.GetLength(0); i++)
            {
                for (int j = 0; j < NumbersArray.GetLength(1); j++)
                {
                    Console.WriteLine(NumbersArray[i, j]);
                }
            }
        }
    }
}
```

## Jagged Array in C#
These are also two-dimensional arrays that will also store the data in the forms of rows and columns. But here 
in the jagged array, the column size will differ from row to row.

That means if the first row contains 5 columns, then the second row may contain 4 columns while the third row 
may contain 10 columns.

The point that you need to remember is if the column size varies from row to row then it is a jagged array. If 
the column size remains the same for all the rows, then it is a rectangular two-dimensional array.

The jagged array in C# is also called the array of arrays. This is because in the case of the jagged array each 
row is a single-dimensional array. So, a combination of multiple single-dimensional arrays with different column
sizes forms a jagged array in C#.

To declare a jagged array in C#, at the time of its declaration, you only need to specify the number of rows 
that you want in the array.

The general syntax for creating a jagged array in C# is:

```
<type> [][] <name> = new <type> [rows][];
```

Example:
```C#
int[][] arr = new int[3][];
```
or
```C#
int [][] arr = {list of values};
```


This being your jagged array:
```C#
int[][] arr = new int[3][];
```

Once you specify the number of rows that you want in the array, then you need to initialize each row with the number
of columns by using a single-dimensional array as shown below.

```C#
arr[0] = new int[5]; // we want five columns in the first row
arr[1] = new int[6]; // we want six columns in the first row
arr[2] = new int[4]; // we want four columns in the first row
arr[3] = new int[5]; // we want five columns in the first row
```

### Example to understand Jagged arrays
In the below example, we created one jagged array with 4 Rows and then we initialize each row of the Jagged 
Array with different 1-Dimensional Arrays. Then we print the default values of jagged array using the nested 
for loop, and then we initialize the jagged array using the nested for loop. And finally, once we initialized 
the jagged array, then we print the elements of the jagged array using a for loop and for each loop.
```C#
using System;

namespace JaggedArray
{
    internal class JaggedArray
    {
        static void Main(string[] args)
        {
            int[][] arr = new int[4][];
            arr[0] = new int[5];
            arr[1] = new int[6];
            arr[2] = new int[4];
            arr[3] = new int[5];

            Console.WriteLine("Default values of the Jagged array");
            for (int i = 0; i < arr.Length; i++)
            {
                for (int j = 0 ; j < arr[i].Length; j++)
                {
                    Console.WriteLine(arr[i][j]);
                }
            }

            // Dynamically assinging values to the jagged array using a nested for loop
            for (int i = 0; i < arr.GetLength(0); i++)
            {
                int num = 10;
                for (int j = 0; j < arr[i].Length; j++)
                {
                    num++;
                    arr[i][j] = num;
                }
            }

            // Printing the values of the jagged array by using a foreach loop within a for loop
            for (int i = 0; i < arr.Length; i++)
            {
                foreach(int x in  arr[i])
                {
                    Console.Write($"{x} ");
                }
                Console.Write("\n");
            }
        }
    }
}
```