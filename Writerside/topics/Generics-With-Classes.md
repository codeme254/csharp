# Generics With Classes

Let us create a generic class with a generic constructor, generic member variable, generic property, and a 
generic method.

```C#
using System;

namespace Generics
{
    // Generic Class
    // T specifies the data type of the class members
    class MyGenericClass<T>
    {
        // Generic variable
        private T GenericMemberVariable;

        // Generic property
        public T GenericProperty { get; set; }

        // Generic constructor
        public MyGenericClass(T value)
        {
            GenericMemberVariable = value;
        }

        // Generic Method
        public T GenericMethod(T GenericParameter)
        {
            Console.WriteLine($"Parameter type: {typeof(T)}");
            Console.WriteLine($"Return type: {typeof(T)}");
            return GenericMemberVariable;
        }
    }
}
```
In the above example, we created the class MyGenericClass with parameter <T>. The angular brackets (<T>) indicate
that MyGenericClass is a generic class and the type for this <T> is going to be defined later. Later we need to 
specify the T while creating an instance of the MyGenericClass class. You can specify the T data type as primitive 
types such as int, float, long, etc., or reference types such as String, Object, Customer, Employee, etc.


So, while creating the instance of this MyGenericClass class, we need to specify the type and the compiler 
will assign that type to T. In the following example, we use int as the data type. Once we create an instance 
of the MyGenericClass, then we are invoking the GenericMethod method. As we have specified the T as int while 
creating the instance, we do not need to specify the same while invoking the class members.
```C#
using System;

namespace Generics
{
    class MainCls
    {
        static void Main(string[] args)
        {
            MyGenericClass<int> intGenericClass = new MyGenericClass<int>(10);
            Console.WriteLine(intGenericClass.GenericMethod(200));
        }
    }
}
```