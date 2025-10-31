# Access Specifiers

Access specifiers are used to define the scope of a type (Class, Interface, Structs, Delegate, Enum, etc.)  and 
its members.

Scope means accessibility or visibility, that is, who can and cannot access them.

C# supports 6 types of access specifiers:
- Private
- Public
- Protected
- Internal
- Protected Internal
- Private Protected (C# Version 7.2 onwards)

Members that are defined in a type with any scope or specifiers are always accessible within that type; restriction 
comes into the picture only when we try to access them outside the type.

In general classes, structs, enums, interfaces, and delegates are called types, and variables, properties, 
constructors, methods, etc. that normally reside within a type are called type members.

<note>
The type members can have all 6 access specifiers whereas types can have only 2 (internal, public) Access Modifiers.

By default, if we have not specified any type, then for the types **internal** access specifier is used as the default
and for the type members, **private** is used as default.
</note>

## Setup
Create a new console application. Once you create a console application, one assembly is created with the extension EXE.

To understand Access Specifiers in C#, we at least need two assemblies. So, let us add a class library project to our
solution which will create another assembly with a DLL extension.

We need to follow the below steps to add the class library project.

1. Right-click on the Solution Explorer and then select **Add -> New Project** option from the context menu as shown
in the below image.

![Right click on the solution explorer](class-project-1.png)

![Add -> New Project](class-project-2.png)

2. Once you click on the New Project, it will open the following Add New Project Dialog Box. Here, first, 
search for the `class library` in the search window and then select **Class Library (.NET Framework)** using 
the C# language project template and then click on the Next button as shown in the below image.

![class library](class-project-3.png)

3. Once you click on the Next button, it will open the Configure Your New Project window. Provide the Project 
name as **AssemblyOne** (or your preference) and select 4.8 as the Dot Net Framework and then click on 
the Create button as shown in the below image.

![Configure project](class-project-4.png)

4. Once you click on the Create button, it will add the Class Library Project with the name AssemblyOne to our solution.
If you have followed the steps correctly, now you should have two projects in the solution explorer as shown 
in the below image.

![class library project](class-project-5.png)

Now build the solution, and you will see that 2 assemblies are generated. One DLL (for the Class Library Project with 
the name AssemblyOne.DLL) and one EXE (for the Console Application)

## What are assemblies in .NET Framework
Assembly refers to precompiled .NET code that can be run by the CLR (Common Language Runtime).

For a console application, the assembly is EXE and for the class library project, the assembly is DLL.

We cannot run a DLL directly but we can run an EXE directly.

More about assemblies in .NET framework later.

First, we will discuss access specifiers with type members then we will discuss access specifiers with types.

## Access Specifiers With Type Members
Access specifiers are used to define the scope of type members, that is, from where we can access them and from where
we cannot.

The different scope for the type members is as follows:
- With the class
- Derived class (child class) in same assembly
- Non-derived class in same assembly
- Derived class (child class) in other assemblies
- Non-derived class in other assemblies

### Private Access Specifier
When we declare a type member (variable, property, method, constructor, etc) as private, then we can access that 
member with the class only. From outside the class, we cannot access them.

Go to the class library project and modify class1.cs class file as follows.

As you can see, here we have created three classes and in the AssemblyOneClass1 we have created one private variable 
and then tried to access the private variable within the same class (AssemblyOneClass1), from the derived class 
(AssemblyOneClass2), and from the non-derived class (AssemblyOneClass3). And all these classes are within the same 
assembly only.

```C#
using System;

namespace AssemblyOne
{
    public class AssemblyOneClass1
    {
        private int Id;
        public void Display1()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass2: AssemblyOneClass1
    {
        public void Display2()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass3
    {
        public void Display3()
        {
            Console.WriteLine(Id);
        }
    }
}
```

When you try to build the above code, you will get some compilation errors as shown in the below image.

![output](access-specifiers-private-type-members-error.png)

Let's try to access the same class members from a different assembly. In our example, this is going to be the console
application.

Modify the program in `Program.cs` as follows:

```C#
namespace AccessSpecifiers
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }

    public class AnotherAssemblyClass1 : AssemblyOneClass1
    {
        public void Display4()
        {
            Console.WriteLine(Id);
        }
    }

    public class AnotherAssemblyClass2
    {
        public void Display5()
        {
            AnotherAssemblyClass1 obj = new AnotherAssemblyClass1();
            Console.WriteLine(obj.Id);
        }
    }
}
```
When we run the above program we get the following error:

![output](access-specifiers-private-type-members-error-2.png)

The above error is because of the AssemblyOneClass1 class file. We cannot access this class file directly from a 
different assembly.

If you want to consume the members of this assembly, then first, you need to include or you need to add a reference 
to that assembly from the project where you want to access the members of this assembly. We want to consume our class 
library assembly in our console application, so, we need to add a reference to the class library project from 
our console application.

To add assembly reference, please follow the below steps.
- Expand the References folder under the console project from the solution explorer.
- Right click references folder and select **Add Reference**.
- From the Add Reference dialog box, select the **Projects tab**
- From the list, select the AssemblyOne project and click on the OK button
- Once you click on the OK button, you will see that AssemblyOne dll should be added to the references folder.

With the above changes in place, now include the namespace where the AssemblyOneClass1 is present.

Modify program.cs file as shown below to include AssemblyOne namespace

```C#
using AssemblyOne;
using System;

namespace AccessSpecifiers
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }

    public class AnotherAssemblyClass1 : AssemblyOneClass1
    {
        public void Display4()
        {
            Console.WriteLine(Id);
        }
    }

    public class AnotherAssemblyClass2
    {
        public void Display5()
        {
            AnotherAssemblyClass1 obj = new AnotherAssemblyClass1();
            Console.WriteLine(obj.Id);
        }
    }
}
```
With the above changes in place, now again build the project and this time you will get the following errors.

![Output](access-specifiers-private-type-members-error-3.png)

These errors make sense that you cannot access the private members from derived and non-derived classes from
different assemblies also.

The scope of private members in C#.NET is as follows:
- **Within the same class**: **YES**
- **Derived class in the same assembly**: **NO**
- **Non-derived class in the same assembly**: **NO**
- **Derived class in other assembly**: **NO**
- **Non-derived class in another assembly**: **NO**

### Public Access Specifiers
When we declare a type member (variable, property, method, constructor, etc) as public, then we can access that member 
from anywhere.

Modify the code in AssemblyOne class1.cs file as follows, the code will work perfect:

```C#
using System;

namespace AssemblyOne
{
    public class AssemblyOneClass1
    {
        public int Id;
        public void Display1()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass2 : AssemblyOneClass1
    {
        public void Display2()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass3
    {
        public void Display3()
        {
            AssemblyOneClass1 obj = new AssemblyOneClass1();
            Console.WriteLine(obj.Id);
        }
    }
}
```

In console application program.cs file, the code will also work fine:

```C#
using AssemblyOne;
using System;

namespace AccessSpecifiers
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }

    public class AnotherAssemblyClass1 : AssemblyOneClass1
    {
        public void Display4()
        {
            Console.WriteLine(Id);
        }
    }

    public class AnotherAssemblyClass2
    {
        public void Display5()
        {
            AnotherAssemblyClass1 obj = new AnotherAssemblyClass1();
            Console.WriteLine(obj.Id);
        }
    }
}
```

The scope of public members is as follows:
- **With the Class**: **YES**
- **Derived Class in Same Assembly**: **YES**
- **Non-Derived Class in Same Assembly**: **YES**
- **Derived Class in Other Assemblies**: **YES**
- **Non-Derived Class in Other Assemblies**: **YES**

### Protected Access Specifier
Protected Members in C# are available within the containing type as well as to the types that are derived from the 
containing type.

That means protected members are available within the parent class (i.e. the containing type) as well as to the 
child/derived classes (classes derived from the containing type).

Modify class1.cs file in AssemblyOne as follows:

```C#
using System;

namespace AssemblyOne
{
    public class AssemblyOneClass1
    {
        protected int Id;
        public void Display1()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass2 : AssemblyOneClass1
    {
        public void Display2()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass3
    {
        public void Display3()
        {
            AssemblyOneClass1 obj = new AssemblyOneClass1();
            Console.WriteLine(obj.Id); // Compile-time error
        }
    }
}
```

Here, you can observe while accessing the protected member from the containing type and derived classes, we are
not getting any errors. But we are getting compilation errors when we are trying to access the protected member 
from the non-derived class within the same assembly.

Now let's try to use protected members from a different assembly.

Modify program.cs in the console project as shown below:

```C#
using AssemblyOne;
using System;

namespace AccessSpecifiers
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }

    public class AnotherAssemblyClass1 : AssemblyOneClass1
    {
        public void Display4()
        {
            Console.WriteLine(Id);
        }
    }

    public class AnotherAssemblyClass2
    {
        public void Display5()
        {
            AnotherAssemblyClass1 obj = new AnotherAssemblyClass1();
            Console.WriteLine(obj.Id); // Error
        }
    }
}
```

You will notice that, from the other assembly, you can access protected member from the derived class but you cannot
access it from the non-derived class.

So, the scope of the protected members in C#.NET is as follows:
- **With the Class**: **YES**
- **Derived Class in Same Assembly**: **YES**
- **Non-Derived Class in Same Assembly**: **NO**
- **Derived Class in Other Assemblies**: **YES**
- **Non-Derived Class in Other Assemblies**: **NO**


### Internal access specifier
Whenever a member is declared with Internal Access Specifier in C#, then it is available anywhere within the containing 
assembly. 

It’s a compile-time error to access an internal member from outside the containing assembly.

Modify class1.cs in AssemblyOne as shown below:

```C#
using System;

namespace AssemblyOne
{
    public class AssemblyOneClass1
    {
        internal int Id;
        public void Display1()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass2 : AssemblyOneClass1
    {
        public void Display2()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass3
    {
        public void Display3()
        {
            AssemblyOneClass1 obj = new AssemblyOneClass1();
            Console.WriteLine(obj.Id);
        }
    }
}
```
The code above works fine, you can observe while accessing the internal specified member from the containing 
type, derived classes, and non-derived classes within the same assembly, we are not getting any errors.

Now, let us try to access the internal members from a different assembly. Modify the Program.cs class file as follows.

From the other assembly, you cannot access the internal member either from the derived classes or from the non-derived 
classes.

```C#
using AssemblyOne;
using System;

namespace AccessSpecifiers
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }

    public class AnotherAssemblyClass1 : AssemblyOneClass1
    {
        public void Display4()
        {
            Console.WriteLine(Id); // Error
        }
    }

    public class AnotherAssemblyClass2
    {
        public void Display5()
        {
            AnotherAssemblyClass1 obj = new AnotherAssemblyClass1();
            Console.WriteLine(obj.Id); // Error
        }
    }
}
```
So, the scope of the internal members in C#.NET is as follows:

- **With the Class**: **YES**
- **Derived Class in Same Assembly**: **YES**
- **Non-Derived Class in Same Assembly**: **YES**
- **Derived Class in Other Assemblies**: **NO**
- **Non-Derived Class in Other Assemblies**: **NO**

### Protected Internal Access Specifier
Protected Internal Members in C# can be accessed anywhere within the same assembly i.e. in which it is declared or
from within a derived class from another assembly.

So, we can think, it is a combination of Protected and Internal access specifiers.

Now, modify class1.cs class file in AssemblyOne as follows:

```C#
using System;

namespace AssemblyOne
{
    public class AssemblyOneClass1
    {
        protected internal int Id;
        public void Display1()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass2 : AssemblyOneClass1
    {
        public void Display2()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass3
    {
        public void Display3()
        {
            AssemblyOneClass1 obj = new AssemblyOneClass1();
            Console.WriteLine(obj.Id);
        }
    }
}
```

you can observe while accessing the protected internal member from the containing type, from the derived classes, 
and from the non-derived class within the same assembly, we are not getting any compilation error.

Now, let us try to access the protected internal members from a different assembly. Modify the Program.cs class file
in the console project as follows.

```C#
using AssemblyOne;
using System;

namespace AccessSpecifiers
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }

    public class AnotherAssemblyClass1 : AssemblyOneClass1
    {
        public void Display4()
        {
            Console.WriteLine(Id);
        }
    }

    public class AnotherAssemblyClass2
    {
        public void Display5()
        {
            AnotherAssemblyClass1 obj = new AnotherAssemblyClass1();
            Console.WriteLine(obj.Id); // Error
        }
    }
}
```

You will notice that from other assemblies, you can access the protected internal member from the derived classes, 
but you cannot access from the non-derived classes.

So, the scope of the protected internal members in C#.NET is as follows:

- **With the Class**: **YES**
- **Derived Class in Same Assembly**: **YES**
- **Non-Derived Class in Same Assembly**: **YES**
- **Derived Class in Other Assemblies**: **YES**
- **Non-Derived Class in Other Assemblies**: **NO**

### Private Protected

The private protected members are accessible within the class and within the derived class of the same assembly but 
cannot be accessed from another assembly.

modify class1.cs class file in AssemblyOne as follows:

```C#
using System;

namespace AssemblyOne
{
    public class AssemblyOneClass1
    {
        private protected int Id;
        public void Display1()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass2 : AssemblyOneClass1
    {
        public void Display2()
        {
            Console.WriteLine(Id);
        }
    }

    public class AssemblyOneClass3
    {
        public void Display3()
        {
            AssemblyOneClass1 obj = new AssemblyOneClass1();
            Console.WriteLine(obj.Id); // Error
        }
    }
}
```

you can observe while accessing the protected internal member from the containing type, and from the derived classes
within the same assembly, we are not getting any compilation error. But we are getting compilation errors while 
trying to access the private protected members from the non-derived classes of the same assembly.

Now, let us try to access the private protected members from a different assembly. Modify the Program.cs class 
file in the console project as follows.

```C#
using AssemblyOne;
using System;

namespace AccessSpecifiers
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }

    public class AnotherAssemblyClass1 : AssemblyOneClass1
    {
        public void Display4()
        {
            Console.WriteLine(Id); // Error
        }
    }

    public class AnotherAssemblyClass2
    {
        public void Display5()
        {
            AnotherAssemblyClass1 obj = new AnotherAssemblyClass1();
            Console.WriteLine(obj.Id); // Error
        }
    }
}
```

From other assemblies, you cannot access the private protected members either from the derived classes or from the 
non-derived classes.

So, the scope of the private protected members in C#.NET is as follows:
- **With the Class**: **YES**
- **Derived Class in Same Assembly**: **YES**
- **Non-Derived Class in Same Assembly**: **NO**
- **Derived Class in Other Assemblies**: **NO**
- **Non-Derived Class in Other Assemblies**: **NO**

The following table shows the summary of all the access specifiers with the type members.

![Summary](access-specifiers-with-type-members-summary.png)

## Access Specifiers With Types
We can use all 6 access specifiers with type members in C# but type allows only two access specifiers i.e.
**Internal** and **Public**.

It is a compile-time error to use private, protected, protected internal, and private protected access specifiers 
with types.

If we have not specified any access specifier, then by default it is going to be internal.

<note>
Types specified with internal specifier can only be accessed from the same assembly, and nowhere else.

Types specified with the public specifier can be accessed from the same assembly as well as other assemblies.
</note>

<note>
If we don’t specify an access specifier in C# then for Class, the default access specifier is internal and for 
class members it is private.
</note>