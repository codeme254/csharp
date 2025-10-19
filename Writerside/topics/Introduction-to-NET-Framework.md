# Introduction to .NET Framework

Before the .NET framework, there was **COM**, let's understand what **COM** is and what problems we face in **COM**.

## What is COM
COM stands for **Component Object Model**.

It is one of the Microsoft Frameworks.

Using this Framework, we can develop Windows Applications (Desktop or Standalone Applications for Windows OS) 
as well as Web Applications.

In earlier versions of COM, **Visual Basic** was the programming language that was used to implement windows
applications **ASP** was the technology used to implement web applications.

[You can learn more about COM here](https://en.wikipedia.org/wiki/Component_Object_Model)

### Disadvantages of COM
- Incomplete Object-Oriented programming meaning it does not support all the features of OOPs.
- Platform dependent - COM applications can only run on windows OS.

To overcome the above problems, microsoft introduced the **.NET Framework**.

## What is .NET
**NET** stands for **Network Enabled Technology** (Internet).

In .NET, dot (.) refers to Object-Oriented, and NET refers to the internet.

So, the complete .NET means through Object-Oriented we can implement internet-based applications.

<note>
.NET is a Free, Cross-Platform, Open-Source <strong>developer platform</strong> for building many different 
types of applications.
</note>

With .NET, we can use multiple languages (C#, VB, F#, etc.), Editors (Visual Studio, Visual Studio Code, 
Visual Studio for Mac, OmniSharp, JetBrains Rider, etc), and Libraries to build for Web, Mobile, Desktop,
Games, IoT, and more.

**.NET is Cross Platform**: Whether you are working in C#, F#, or Visual Basic, your code will run on any compatible
operating system. You can build many types of apps with .NET. Some are Cross-Platform, and some target a specific set 
of operating systems and devices.

.NET is a framework tool that supports many programming languages and many technologies. .NET support 60+ 
programming languages. Of 60+ programming languages, 9 are designed by Microsoft and the remaining are 
designed by non-Microsoft.

Microsoft-designed programming languages in dotnet are as follows:
- VB.NET
- C#.NET
- VC++.NET
- J#.NET
- F#.NET
- Jscript.NET
- WindowsPowerShell
- Iron phyton
- Iron Ruby

The technologies supported in .NET are as follows:
- **ASP.NET** (Active Server Pages.NET) – MVC, Web API, Core MVC, Core Web API, Core Blazor, etc.
- **ADO.NET** (Active Data Object.NET)
- **WCF** (Windows Communication Foundation)
- **WPF** (Windows Presentation Foundation)
- **WWF** (Windows Workflow Foundation)
- **AJAX** (Asynchronous JavaScript and XML)
- **LINQ** (Language Integrated Query)
- **Entity Framework**

## What is a Framework
A framework is a collection of many small technologies integrated together to develop applications that 
can be executed anywhere.

The .NET Framework provides two things:
- **BCL**: (Base Class Libraries)
- **CLR**: (Common Language Runtime)

### BCL
BCL is the basic building block of .NET programs.

BCL contains pre-defined classes and these classes are used for the purpose of application development.

These are installed when we install the .NET framework.

Base Class Libraries (BCL) are designed by Microsoft.

Without BCL we can’t write any code in .NET.

### CLR
CLR stands for Common Language Runtime and it is the core component under the .NET framework which is 
responsible for converting the **MSIL (Microsoft Intermediate Language)** - (more about this later) code into 
native code (code specific to the Operating System).

![CLR](clr.png)

In the .NET Framework, code is compiled twice:
- In the 1<sup>st</sup> compilation, the source code is compiled by the respective language compiler 
and generates the intermediate code which is known as **MSIL (Microsoft Intermediate Language)** or 
**IL (Intermediate language code)**, or **Managed Code**.
- In the 2nd compilation, **MSIL** is converted into Native code (native code means code specific to the 
Operating system so that the code is executed by the Operating System) and this is done by **CLR**.

### What is JIT
JIT stands for the **Just-in-Time** compiler.   
It is the component of CLR that is responsible for converting MSIL code into Native Code.  
Native code is code that is directly understandable by the operating system.

## Different Types of .NET Framework
- **.NET Framework**: .NET Framework is the original implementation of .NET. It supports running websites, 
services, desktop applications, and more on Windows OS Only (NOT CROSS-PLATFORM).
- **.NET**: .NET is a cross-platform implementation for running websites, services, and console applications 
on Windows, Linux, and macOS. .NET is open source on GitHub and .NET was previously called **.NET Core**.
- **Xamarin/Mono**: Xamarin/Mono is a .NET implementation for running apps on all the major mobile operating 
systems, including iOS and Android.

Note: **.NET Framework** is **Platform-Dependent** while **.NET** or **.NET Core** is **Platform Independent**.

[Official GitHub Repository for .NET](https://github.com/dotnet/runtime)