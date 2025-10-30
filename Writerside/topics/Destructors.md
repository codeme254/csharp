# Destructors

Destructors are used to perform any necessary final clean-up when a class instance is being collected by 
the garbage collector.

Destructors are also called **finalizers**.

The Destructor is also a special type of method present in a class, just like a constructor, having the same name 
as the class name but prefixed with **~ tilde**.

The Constructor in C# is Explicitly called when the object of the class is created. On the other hand, the Destructor 
in C# is Implicitly Called when the object of the class is destroyed.

The Constructor and destructor methods will exactly have the same name as the class to which they belong. So, to 
differentiate between these two, a tilde (~) symbol is used just before the destructor method.

![Destructor](destructor-syntax.png)

<note>
The most important point that you need to keep in mind is that a destructor method cannot have any parameters as well
as cannot be applied with any modifiers. As the destructor is not parameterized, so we cannot overload the destructor.
</note>

## When is a destructor method called in C#?
Destructor methods are automatically called by the garbage collector.

A destructor method gets called automatically by the garbage collector when the object of the class is destroyed.

### When does the object of a class get destroyed in C#?
1. At the end of the program execution, each and every object that is associated with the program will be destroyed 
by the garbage collector.
2. The Implicit calling of the garbage collector occurs sometime in the middle of the program execution provided the 
memory is full so the garbage collector will identify unused objects of the program and destroys them.
3. The Explicit calling of the garbage collector can also be done in the middle of program execution by the
programmer with the help of the "Collect()" statement so that if there are any unused objects associated with 
the program will be destroyed in the middle of the program execution.

## Example to understand Destructors in C#
In the below example, we have created one class called DestructorDemo with one constructor and one destructor. Then 
inside the Main method, we have created two instances of the DestructorDemo class and then made the obj1 value null
which is eligible for garbage collection.

```C#
namespace Destructors
{
    internal class DestructorDemo
    {
        public DestructorDemo()
        {
            Console.WriteLine("Constructor object created");
        }

        // Destructor
        ~DestructorDemo()
        {
            Console.WriteLine("Object destroyed");
        }
        static void Main(string[] args)
        {
            DestructorDemo obj1 = new DestructorDemo();
            DestructorDemo obj2 = new DestructorDemo();

            // making obj1 eligible for garbage collection
            obj1 = null;
        }
    }
}
```

The output of the above program will be:
![output](destructors-output-1.png)

You can see the statements written inside the destructor are not printed in the output. Then you might be thinking 
that our destructor is not executed even though we made the obj2 value null.

This is not right. The point that you need to remember is that the destructor method is implicitly called by the 
garbage collector and we cannot predict when it calls the destructor method. And hence you cannot see those print 
statements in the output.

Once, the object is unused i.e. it ready for garbage collection, then it is the responsibility of the garbage 
collector to destroy that unused object and free the memory from the heap.

If you want, then you can also make an explicit call to the garbage collector in the middle of the application 
execution to destroy the unused object. To do so, we need to call the GC.Collect method as shown in the below example.

```C#
namespace Destructors
{
    internal class DestructorDemo
    {
        public DestructorDemo()
        {
            Console.WriteLine("Constructor object created");
        }

        ~DestructorDemo()
        {
            Console.WriteLine("Object destroyed");
        }
        static void Main(string[] args)
        {
            DestructorDemo obj1 = new DestructorDemo();
            DestructorDemo obj2 = new DestructorDemo();

            // making obj1 eligible for garbage collection
            obj1 = null;
            GC.Collect();
        }
    }
}
```

In real-world C# code, you should rarely (almost never) call `GC.Collect()` or rely on destructors for cleanup.

