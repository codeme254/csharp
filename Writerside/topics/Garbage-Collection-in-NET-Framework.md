# Garbage Collection in .NET Framework

When a dot net application runs, lots of objects are created.

At a given point in time, it is possible that the application does not use some of those objects.

The Garbage Collector in the .NET Framework is nothing but a Small Routine or you can say it’s a Background Process
that runs periodically and tries to identify what objects are not being used currently by the application and 
de-allocates the memory of those objects.

So, Garbage Collector is nothing but a feature provided by CLR that helps us clean or destroy unused managed objects. 
Cleaning or destroying those unused managed objects basically reclaims the memory.

Garbage Collection (GC) in the .NET Framework is an automatic memory management system that helps manage the 
allocation and release of memory in your applications.

In .NET, when we create an object using the new keyword, it automatically allocates memory on the managed heap. You 
don’t need to allocate or deallocate memory explicitly as you might have to in languages like C or C++.

<note>
The Garbage Collector will destroy only the unused managed objects. It does not clean unmanaged objects. 
</note>

## Managed and Unmanaged Objects in .NET Framework
Whenever we create any EXE (i.e., Console Application, Windows Application, etc.) or Web Application (i.e., ASP.NET 
MVC, Web API, ASP.NET, Class Library, etc.) in .NET Framework using Visual Studio and using any .NET supported 
programming language such as C#, VB, F#, etc., **these applications run completely under the control of CLR. That means
if your applications have unused objects, then CLR will clean those objects using Garbage Collector**.

Let’s say you have also used other third-party EXE in your .NET application, like Skype, PowerPoint, Microsoft Excel, 
etc., and assume these "EXEs" are not made in dot net, they are made using some other programming languages such as 
C, C++, Java, etc.

When you use these EXEs in your application, then these will not be run by the CLR. Even though you run these EXEs in
.NETT applications, they will run under their own environment. For example, if one EXE is developed using C or C++, 
then that EXE will run under the C or C++ Runtime Environment. In the same line, if the EXE is created using VB6, 
then it will run under the VB6 runtime environment.

The code that runs under the complete control of the CLR is called **managed code**.

CLR will provide all the facilities and features of .NET to the managed code execution like Language Interoperability, 
Automatic Memory Management, Exception Handling Mechanism, Code Access Security, etc.

Code that is not executed under the complete control of the CLR is called **unmanaged code**.

CLR will not provide any facilities and features of .NET to the unmanaged code in C# execution like Language 
Interoperability, Automatic memory management, Exception handling mechanism, code access security, etc.

### Managed Objects
Managed objects are allocated on the managed heap and controlled by the .NET Garbage Collector (GC).

These objects are typically instances of classes and structures defined in .NET.

The GC automatically manages the memory for managed objects. It allocates and releases memory for these objects 
and handles memory optimizations like compacting.

Examples of managed objects are any instance of a class or structure created using the new keyword in C# or VB.NET 
and objects created in .NET languages like arrays, strings, etc.

### Unmanaged Objects
Unmanaged objects are objects whose memory is not managed by the .NET GC.

These are typically objects allocated using native code, like calls to Windows API or using languages such as C or C++.

The developer is responsible for allocating and freeing the memory for unmanaged objects. This is usually done using 
APIs like malloc and free in C or new and delete in C++.

Examples of unmanaged objects are file handles, database connections, COM objects, or any other resources that are 
not managed by the .NET runtime.

## Garbage Collection Generations in .NET Framework
There are three garbage collection generations in .NET:
- Generation 0
- Generation 1
- Generation 2

### Understanding Generations 0, 1, and 2
Let’s say you have a simple application called App1. As soon as the application starts, it creates 5 managed objects.

Whenever any new objects (fresh objects) are created, they are moved into a bucket called **Generation 0**.

For a better understanding, please have a look at the following image.

![Generation 0](garbage-collector-generation-0.png)

Now, we know that the garbage collector runs continuously as a background process to check whether there are any 
unused managed objects so that it reclaims the memory by cleaning those objects.

Now, let’s say the application does not need two objects (Object1 and Object2). So, the Garbage Collector will destroy 
these two objects (Object1 and Object2) and reclaim the memory from the Generation 0 bucket.

But the application still needs the remaining three objects (Object3, Object4, and Object5). So, the Garbage collector 
will not clean those three objects. The Garbage Collector will move those three managed objects (Object3, Object4, 
and Object5) to the Generation 1 bucket, as shown in the image below.

![Generation 1](garbage-collector-generation-1.png)

Let’s say your application creates two more fresh objects (Object6 and Object7). As fresh objects, they should be 
created in the Generation 0 bucket, as shown in the image below.

![New objects added to Generation 0](garbage-collector-generation-0-new.png)

Now, again, the Garbage Collector runs, and it comes to the Generation 0 bucket and checks which objects are used. 
Let’s say both objects (Object6 and Object7) are unused by the application, so it will remove both objects and 
reclaim the memory.

Now, it goes to the Generation 1 bucket and checks which objects are unused. Let’s say the application still needs 
Object4 and Object5 while object3 is not needed. So, what Garbage Collector will do is destroy Object3, reclaim the 
memory, and move Object4 and Object5 to the Generation 2 bucket, as shown in the image below.

![Generation 3](garbage-collector-generation-3.png)

### Why do we need Generations?
Normally, when we are working with big applications, they can create thousands of objects. So, for each of these 
objects, if the garbage collector goes and checks if they are needed it would be a really painful process.

By creating such generations, if an object is in generation 2 for example, the Garbage Collector trusts that the object
will live in the memory longer and thus makes fewer visits to this bucket. This increases the Garbage Collector's
performance.

### Generation 0
1. **Short-Lived Objects**: Generation 0 (Gen 0) contains newly created objects that are short-lived. These are 
typically temporary objects.
2. **Frequent Collection**: Gen 0 is collected more frequently than the other generations. Most objects are reclaimed 
for garbage collection in this generation since they are short-lived.
3. **Efficiency**: The collection process is generally fast because it involves only a small portion of the heap.
4. **Example**: Temporary variables, small objects, and objects that are used briefly in methods.

### Generation 1
1. **Buffer Generation**: Generation 1 (Gen 1) serves as a buffer between short-lived objects in Gen 0 and
long-lived objects in Gen 2.
2. **Promotion**: Objects that survive a Gen 0 GC are promoted to Gen 1. These are typically objects that have 
a longer lifetime than those in Gen 0 but are not permanent.
3. **Intermediate Lifetime**: Gen 1 is collected less frequently than Gen 0. The objects here have 
an intermediate lifetime.
4. **Example**: Objects that survive several GC cycles but are not used throughout the application’s lifetime.

### Generation 2
1. **Long-Lived Objects**: Generation 2 (Gen 2) contains long-lived objects. These are objects that have survived 
multiple rounds of GC in the previous generations.
2. **Least Frequently Collected**: Gen 2 is collected less frequently than Gen 0 and Gen 1. The GC 
process here can be more time-consuming because it involves a larger portion of the heap.
3. **Examples**: Static objects, objects tied to the application’s life, and large objects that 
require significant memory resources.