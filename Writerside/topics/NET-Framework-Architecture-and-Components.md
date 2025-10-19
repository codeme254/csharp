# .NET Framework Architecture and Components

As we have seen so far, the two major components of the .NET framework are CLR and BCL:
- CLR: The Common Language Runtime (CLR) is the execution engine that handles running applications. 
It provides services like thread management, garbage collection, type safety, exception handling, and more. It is also
the part that is responsible for converting MSIL into native code.
- BCL: The Base Class Library provides a set of APIs and types for common functionality. It provides types for 
strings, dates, numbers, etc. The Class Library includes APIs for reading and writing files, connecting to 
databases, drawing, and more.

The .NET applications are written in C#, F#, or VB programming languages among others.

The Source Code is compiled into an intermediate language code called **Intermediate Language (IL)** or 
**Microsoft Intermediate Language (MSIL)** or **Common Intermediate Language (CIL)**. And the Compiled 
code is stored in assemblies with **.DLL** or **.EXE** file extension.

When an application runs, the CLR takes the Assembly (IL Code or MSIL Code, or CIL) and uses the Just-in-Time 
compiler (JIT) to convert the MSIL or IL code into machine code that can execute on the specific architecture 
of the computer it is running on.

![Architecture](architecture-1.png)