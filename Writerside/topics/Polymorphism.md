# Polymorphism

Polymorphism is one of the fundamental OOP concepts and is a term used to describe situations where 
something takes various roles or forms.

It is the ability of something to exist in more than one form.

In the programming world, these things can be operators or functions.

## Types of Polymorphism in C#
There are two types of polymorphism in C# and they are as follows:
- Static Polymorphism / Compile-Time Polymorphism / Early Binding
- Dynamic Polymorphism / Run-Time Polymorphism / Late Binding

In C#, polymorphism is implemented in the following ways:
- Method overloading
- Operator overloading
- Method overriding
- Method hiding

![Types of polymorphism](polymorphism-types.png)

**Note**:  
While working with Polymorphism in C#, we need to understand two things:
- what happens at the time of compilation for a given method call: here, the compiler tries to figure out which method
you are calling. This is called **binding**.
-  what happens at the time of execution for a given method call: the program executes the actual method, and
sometimes, that method might come from a different class than what the compiler expected.

Is the method going to be executed from the same class at run-time, which is bounded to the class at the compile time,
or is the method going to be executed from a different class at run-time rather than the class bounded at compile time?

## Dynamic Polymorphism / Run-Time Polymorphism / Late Binding
Dynamic polymorphism means the method to run is decided while the program is running, not during compilation.

It happens when a child class overrides a method from its parent class, using the keywords virtual and override.

Here, the compiler only knows that a method exists, but it waits until the program is running to see which
version (parent’s or child’s) should actually run.

That’s why it’s called run-time polymorphism or late binding; the binding (link between the method call
and method body) happens later, at run time.

It is achieved through:
- Method overriding

### Method Overriding
The process of re-implementing the superclass non-static, non-private, and non-sealed method in the subclass
with the same signature is called Method Overriding in C#.

The same signature means the name and the parameters (type, number, and order of the parameters) should be the same.

#### How to Override a Parent Class Method Under Child Class
If you want to override the Parent class method in its Child classes, first the method in the parent class must be
declared as virtual by using the **virtual** keyword, then only the child classes get permission for
overriding that method.

If the child class wants to override the parent class virtual method, then the child class can override it with
the help of the **override** modifier.

The syntax is shown below:

![Method overriding](polymorphism-method-overriding-example.png)

#### Example of Method Overriding

```C#
using System;

namespace MethodOverriding
{
    class Class1
    {
        public virtual void Show()
        {
            Console.WriteLine("Show method in the parent");
        }
    }

    class Class2 : Class1
    {
        public override void Show()
        {
            Console.WriteLine("Show method in the child");
        }
    }
    internal class MethodOverriding
    {
        static void Main(string[] args)
        {
            Class1 c1 = new Class1();
            c1.Show();

            Class2 c2 = new Class2();
            c2.Show();
        }
    }
}
```

## Static Polymorphism / Compile-Time Polymorphism / Early Binding
Static polymorphism means that the compiler already knows which method to run before the program starts.

It is achieved through:
- Method overloading
- Operator overloading
- Method hiding

### Method overloading
This is where we define multiple methods with the same name but different parameters.

Method Overloading in C# allows a class to have multiple methods with the same name but with a different signature.

#### Example of method overloading
```C#
using System;

namespace MethodOverloading
{
    class AddNumbers
    {
        public void Add(int num1, int num2)
        {
            Console.WriteLine(num1 + num2);
        }

        public void Add(int num1, int num2, int num3)
        {
            Console.WriteLine(num1 + num2 + num3);
        }

        public void Add(float num1, float num2) 
        { 
            Console.WriteLine(num1 + num2); 
        }

        public void Add(float num1, float num2, float num3)
        {
            Console.WriteLine(num1 + num2 + num3);
        }
    }

    internal class MethodOverloading
    {
        static void Main(string[] args)
        {
            AddNumbers a = new AddNumbers();
            a.Add(5, 5);
            a.Add(3.5f, 2.2f);
            a.Add(10, 20, 30);
            a.Add(55.6f, 2.3f, 9.9f);
        }
    }
}
```
Another perfect example of method overloading is the "WriteLine()" method we have been using. It is an overloaded 
method.

If you go to the definition of the Console class, then you will see the following overloaded versions of the 
WriteLine method defined inside the Console class.

![Overloaded WriteLine method](polymorphism-writeline-overload.png)

### Operator Overloading
By overloading the operators, we can give additional meaning to the operators like +-*/=.,= etc.

Operator overloading is a type of polymorphism in which an operator is overloaded to give it a user defined meaning.

#### The Syntax for C# Operator Overloading
To overload an operator in C#, we use a special operator function. We define the function inside the class or 
structure whose objects/variables we want the overloaded operator to work with. The Syntax for Operator Overloading
in C# is shown below.

![Operator overloading](polymorphism-operator-overloading-syntax.png)
- return_type: is the return type of the function
- operator: is a keyword
- op: symbol of the operator we want to overload e.g. +, <, e.t.c.
- Type: must be a class or a struct
- The function should be a static function

#### Example of Operator Overloading
In the example below, we are overriding the + and - operator to add two boxes and subtract a box from another
respectively.
```C#
using System;

namespace OperatorOverloading
{
    class Box
    {
        int Length;
        int Width;
        int Height;
        
        public Box(int l, int w, int h)
        {
            Length = l;
            Width = w;
            Height = h;
        }

        // Overiding the + operator to add two boxes
        public static Box operator +(Box b1, Box b2)
        {
            Box final = new Box(
                b1.Length + b2.Length,
                b1.Width + b2.Width,
                b1.Height + b2.Height
             );
            return final;
        }

        // Overiding the - operator to cut out a box from another
        public static Box operator -(Box b1, Box b2)
        {
            Box final = new Box(
                b1.Length - b2.Length,
                b1.Width - b2.Width,
                b1.Height - b2.Height
             );
            return final;
        }

        public void DisplayBox()
        {
            Console.WriteLine($"Length: {Length}");
            Console.WriteLine($"Width: {Width}");
            Console.WriteLine($"Height: {Height}");
        }
    }
    internal class OperatorOverloading
    {
        static void Main( string[] args )
        {
            Box b1 = new Box(10, 20, 30);
            Box b2 = new Box(5, 10, 15);
            Box b3 = b1 + b2; // Using the overloaded + operator
            Box b4 = b1 - b2; // Using the overloaded - operator
            b3.DisplayBox();
            b4.DisplayBox();
        }
    }
}
```

### Method Hiding
Method Hiding/Shadowing is also an approach of re-implementing the parent class methods under the child class 
exactly with the same signature (same name and same parameters).

We can re-implement the parent class methods under the child classes in two different approaches. They are as follows:
- Method Overriding (as in dynamic polymorphism)
- Method hiding

Then what are the differences between them?

In Method Overriding, the child classes re-implement their parent class methods which are declared as virtual. 
That means here, the child classes re-implement the parent class methods with the permission of the parent class 
because here in the parent class the method is declared as virtual giving permission to the child classes for 
overriding the methods using the override modifier.

In Method Hiding/Shadowing, the child classes can re-implement any method of its parent class methods even if they 
are not declared as virtual. That means here the child class re-implements the parent class methods without taking
any permission from its parent.

#### How to Implement Method Hiding
Please have a look at the following image to understand the syntax of Method Hiding/Shadowing in C#. It does not 
matter whether the parent class method is virtual or not. We can hide both virtual and non-virtual methods under 
the child class.

Again, we can hide the method in the child class in two ways i.e. by using the new keyword and also, without 
using the new keyword. If we are not using the new keyword then we will get a warning, always use the **new** keyword
if you intended to do method hiding.

The new keyword explicitly tells us that you are hiding the base class or parent class members inside the child class.

![method hiding](polymorphism-method-hiding.png)

#### Example of Method Hiding
```C#
using System;

namespace MethodHiding
{
    class Class1
    {
        public void Show()
        {
            Console.WriteLine("Show method in the parent");
        }
    }

    class Class2 : Class1
    {
        public new void Show()
        {
            Console.WriteLine("Show method in the child");
        }
    }
    internal class MethodHiding
    {
        static void Main(string[] args)
        {
            Class1 c1 = new Class1();
            c1.Show();

            Class2 c2 = new Class2();
            c2.Show();
        }
    }
}
```