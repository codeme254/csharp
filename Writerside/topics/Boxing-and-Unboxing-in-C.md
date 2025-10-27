# Boxing and Unboxing in C#

Boxing and Unboxing are two fundamental concepts in C# that deal with converting between value and reference types.

**Boxing** is the process of converting a value type (like int, double, struct) to a reference type (object). 
When a value type is boxed, a new object is allocated to the heap, and the value is copied into it.

**Unboxing** is the reverse process of boxing, where a value is extracted from an object. It involves explicitly 
converting a reference type (object) into a value type. This operation also involves a copy operation, where 
the value is copied from the heap into the stack.

Look at the following example to understand boxing and unboxing:

![Example](boxing-and-unboxing-1.png)

The above method contains three lines of code. Now, let us understand what happens when executing each code line.

**Line 1: int x = 10;**

When this statement is executed, an integer variable x will be created in the Stack memory with a value of 10.

![Line 1](boxing-and-unboxing-line-1.png)

**Line 2: object y = x;**

When executing this statement, we move the x value, i.e., 10, to an object data type. If you remember, the object is
the parent class for all classes in the .NET Framework. When we move a value type to a reference type, it is 
called Boxing.

So, here we are moving value type integer x to reference type object y, so we are performing boxing here.

![Line 2](boxing-and-unboxing-line-2.png)

**Line 3: int x = (int)y;**

When executing this statement, we move the object value to an integer data type by doing type casting.

When we move a reference type to a value type, it is called Unboxing. So, we are moving the reference type value, 
i.e., y, to an integer type, i.e., z, so we are performing Unboxing here.

![Line 3](boxing-and-unboxing-line-3.png)

## Example to Understand Boxing and Unboxing

```C#
namespace BoxingAndUnboxing
{
    internal class BoxingAndUnboxing
    {
        static void Main()
        {
            int x = 10;
            object y = x; // boxing
            int z = (int)y; // unboxing
            Console.WriteLine($"x:{x}, y:{y}, z:{z}");
        }
    }
}
```

<note>
We should always avoid Boxing and Unboxing in C# due to performance degradation in application development.
</note>