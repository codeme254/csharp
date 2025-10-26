# Overriding the Equals Method in C#

The Equals is a virtual method defined in the `Object` class and this method is available to all the .NET Types as
`Object` is the superclass of all .NET Types.

![object class](object-equals-method.png)

As Equals is a virtual method, we can also override this method under our classes.

Following is the signature of this method:

- `public virtual bool Equals(object obj)`: This method is used to determine whether the specified object is 
equal to the current object. Here, the parameter obj specifies the object to compare with the current object. 
It returns true if the specified object is equal to the current object; otherwise, false.

Before understanding how to override and when to override, let us first understand what is the difference between 
the `==` Operator and `Equals` method in C#.

## Difference Between the “==” Operator and the Equals() Method in C#
As we already discussed every type in .NET, directly or indirectly inherits from the Object class.

So, the `Equals()` virtual method, which has a default implementation within the Object class is also available in 
every .NET (Primitive as well as Reference) type via inheritance.

In the following example, the variables Number1 and Number2 are integers. So, both the == and Equals() method 
returns true, since Number1 and Number2, both variables have the same value i.e. 10.

Integers are value types and they hold the value directly, and hence we get the result true in this case.

```C#
namespace ObjectClassMethods
{
    internal class ObjectClassMethods
    {
        static void Main(string[] args)
        {
            int Number1 = 10;
            int Number2 = 10;
            Console.WriteLine($"Number1 == Number2: {Number1 == Number2}");
            Console.WriteLine($"Number1.Equals(Number2): {Number1.Equals(Number2)}");
        }
    }
}
```
The output for the above program will be:
```Plain Text
Number1 == Number2: True
Number1.Equals(Number2): True
```

## Equals method and == Operator with Reference Type in C#
If the type is a reference type, then by default both the == operator and Equals method check for reference equality 
whereas we can change this default behavior of the Equals() method by overriding it to check for value equality.

In the following example, E1 and E2 are different object reference variables of the Employee class, but both are 
pointing to the same object.

Since E1 and E2 both refer to the same object, the reference equality, and the value equality is true.

Value equality means that two objects contain the same values.

```C#
namespace ObjectClassMethods
{
    public class Employee
    {
        public string FirstName { get; set; }
        public string LastName { get; set; }

        public override string ToString()
        {
            return $"Employee({FirstName} {LastName})";
        }
    }
    internal class ObjectClassMethods
    {
        static void Main(string[] args)
        {
            Employee E1 = new Employee();
            E1.FirstName = "John";
            E1.LastName = "Doe";

            Employee E2 = new Employee();
            E2 = E1;

            Console.WriteLine($"E1 == E2: {E1 == E2}");
            Console.WriteLine($"E1.Equals(E2): {E1.Equals(E2)}");
        }
    }
}

```

The output for the code above will be:
```Plain Text
E1 == E2: True
E1.Equals(E2): True
```

If two objects have reference equality, then they also have value equality, but value equality does not guarantee 
reference equality.

In the following example, the == operator returns False. This makes sense because E1 and E2 are referring 
to different objects. 

However, the Equals() method also returns false, in spite of the values across E1 and E2 being the same and this 
is because by default Equals method checks the reference equality.

```C#
namespace ObjectClassMethods
{
    public class Employee
    {
        public string FirstName { get; set; }
        public string LastName { get; set; }

        public override string ToString()
        {
            return $"Employee({FirstName} {LastName})";
        }
    }
    internal class ObjectClassMethods
    {
        static void Main(string[] args)
        {
            Employee E1 = new Employee();
            E1.FirstName = "John";
            E1.LastName = "Doe";

            Employee E2 = new Employee();
            E2.FirstName = "John";
            E2.LastName = "Doe";

            Console.WriteLine($"E1 == E2: {E1 == E2}");
            Console.WriteLine($"E1.Equals(E2): {E1.Equals(E2)}");
        }
    }
}
```


The output for the above program will be:

```Plain Text
E1 == E2: False
E1.Equals(E2): False
```

## Overriding the Equals Method of the Object Class in C#
In the following example, we override the Equals() method of the Object class inside the Customer class.

When overriding the Equals() method, make sure the passed object is not null and can be cast to the type you are 
comparing. When overriding Equals(), you also need to override GetHashCode(), otherwise you will get a compiler warning.

```C#
namespace ObjectClassMethods
{
    public class Employee
    {
        public string FirstName { get; set; }
        public string LastName { get; set; }

        public override string ToString()
        {
            return $"Employee({FirstName} {LastName})";
        }

        public override bool Equals(object obj)
        {
            if (obj == null) return false;
            if(obj is not Employee) return false;
            return FirstName == ((Employee) obj).FirstName && 
                LastName == ((Employee) obj).LastName;
        }
    }
    internal class ObjectClassMethods
    {
        static void Main(string[] args)
        {
            Employee E1 = new Employee();
            E1.FirstName = "John";
            E1.LastName = "Doe";

            Employee E2 = new Employee();
            E2.FirstName = "John";
            E2.LastName = "Doe";

            Console.WriteLine($"E1 == E2: {E1 == E2}");
            Console.WriteLine($"E1.Equals(E2): {E1.Equals(E2)}");
        }
    }
}
```
The output for the above code will be:
```C#
E1 == E2: False
E1.Equals(E2): True
```

Now, the Equals method will not check the reference address instead it will check the First Name and Last Name 
of both the objects and if it is found to be the same, then it will return TRUE else it will return FALSE.

The above code is working but currently, we are getting the warning stating: `'Employee' overrides 
Object.Equals(object o) but does not override Object.GetHashCode()`

It is not mandatory to override the GetHashCode method, but it is recommended to override the GetHashCode method 
if you are overriding the Equals method in C#.