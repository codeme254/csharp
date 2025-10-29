# Constructors in C#

A constructor is a special method present inside a class responsible for initializing the variables of that class.

The name of the constructor method is always the same as the name of the class that the constructor is present in. If
your class name is Employee, then the name of the constructor method is going to be Employee, and if your class 
name is Student, then the constrictor name is also going to be Student.

The constructor method does not return any value. That means, it is a non-value returning method.

## Example to understand constructors
Each and every class requires a constructor if we want to create the instance of that class.

If we don't have a constructor, then we cannot create an instance of that class.

<note>
It is your responsibility as a programmer to define a constructor under a class, if you don't define a constructor,
an implicit one will be defined by the compiler.
</note>

![constructors](constructors-example.png)

You can see here that after compilation, the compiler adds the public constructor to the class and initializes the 
variable and this is the responsibility of a constructor i.e. initializing the variables of that class.

**The following side note is important**:  
Every variable we declared inside a class and every field we declared inside a class has a default value. All numeric 
types are initialized with 0, Boolean types initialized with false, and string and object types initialized with null.

![Default values](constructors-default-values.png)

```C#
namespace Constructors
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Test t = new Test();
            Console.WriteLine($"i = {t.i}");
            Console.WriteLine($"j = {t.j}");
            Console.WriteLine($"k = {t.k}");
        }
    }

    class Test
    {
        public int i;
        public bool j;
        public string k;
    }
}
```

## How to create a constructor in C#
We can also create our own constructors in C#, the following is the syntax to do this:

![constructors syntax](constructors-syntax.png)

Whenever we create an instance of that class, the constructor is always executed first.

```C#
namespace Constructors
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Test t = new Test();
            Console.WriteLine($"i = {t.i}");
            Console.WriteLine($"j = {t.j}");
            Console.WriteLine($"k = {t.k}");
        }
    }

    class Test
    {
        public int i;
        public bool j;
        public string k;

        public Test()
        {
            Console.WriteLine("Constructor has been executed");
            i = 25;
            j = true;
            k = "Hello World!";
        }
    }
}
```