# Multicast Delegates

A Multicast Delegate in C# is a delegate that holds the references of more than one handler function.

When we invoke the multicast delegate, then all the functions which are referenced by the delegate are going 
to be invoked.

## Example of Multicast Delegate

In the below example, we have created one delegate whose signature is the same as the two methods i.e. 
`GetArea` and `GetPerimeter`.

Then we created the instance of delegate and bind the two methods using the `+=` operator.

Similarly, you can use the `-=` operator to remove a function from the delegate.

Once we bind the two methods with the delegate instance and when we call the delegate, both methods are going
to be executed.

```C#
using System;

namespace MulticastDelegate
{
    public delegate void RectangleDelegate(double Width, double Height);
    internal class Rectangle
    {
        void GetArea(double Width, double Height)
        {
            Console.WriteLine($"Area of the rectangle is {Width * Height}");
        }

        void GetPerimeter(double Width, double Height)
        {
            Console.WriteLine($"Perimeter of the recangle is {2 * Width + 2 * Height}");
        }
        static void Main(string[] args)
        {
            Rectangle rect = new Rectangle();
            RectangleDelegate rectDelegate = new RectangleDelegate(rect.GetArea);
            // binding more methods to this delegate - thus a multicast delegate
            rectDelegate += rect.GetPerimeter;

            // Invoking the delegate, all the methods bound to this delegate will be executed
            rectDelegate(10, 20);

            // Removing a method from a delegate
            rectDelegate -= rect.GetArea;
            rectDelegate.Invoke(5, 6); // We can also use the Invoke method to call a delegate
        }
    }
}
```

## Multicast Delegates With Returns
When a delegate is multicast and its handler methods return values, only the return value of the last method in the 
invocation list is kept. All earlier return values are ignored.

```C#
using System;

namespace MulticastDelegate2
{
    public delegate int ExampleDelegate();
    internal class Rectangle
    {
        int Method1()
        {
            return 1;
        }

        int Method2()
        {
            return 2;
        }
        static void Main(string[] args)
        {
            Rectangle r = new Rectangle();
            ExampleDelegate del = new ExampleDelegate(r.Method1);
            del += r.Method2;

            Console.WriteLine($"Value returned by delegate {del()}");
            // Output: Value returned by delegate 2
        }
    }
}
```