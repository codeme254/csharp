# Creating Your First Console Application in Visual Studio

A console application is an application that can be run in the command prompt in Windows.

For any beginner on .Net, building a console application is ideally the first step to learning the C# Language.

Please follow the steps below to create a console application in visual studio:

## Step 1
The first step involves the creation of a new project in Visual Studio. For that, open Visual Studio 2022 
(the latest version at this point in time) and then click on the Create a New Project option as shown in the 
below image.

![Console app Step 1](console-app-step-1.png)

## Step 2
The next step is to choose the project type as a Console application.

Type Console in the search bar and you can see different types of console applications using C#, VB, and F# 
languages using both .NET Framework and Core Framework.

Select Console App (.NET Framework) using C# language and then clicking on the Next button as shown in the below image.

![Console app Step 2](console-app-step-2.png)

## Step 3
The next step is to configure the new project.

Here, you need to provide the project name and solution name.

You can also give the same name to both project and solution but it is not mandatory.

You need to provide the location where you need to create the project.

Here, you also need to provide the .NET Framework version you want to use. The latest version of the 
.NET Framework is 4.8 so select 4.8 here and click on the create button as shown in the image below.

![Console app Step 3](console-app-step-3.png)

Your project will be created.

This project will contain all the necessary required files to run the Console application. The Main program called 
Program.cs is the default code file that is created when a new console application is created in Visual Studio. 
This Program.cs class will contain the necessary code for our console application.

If you look at Program.cs class file, you will see the following code:

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Day_0
{
    internal class Program
    {
        static void Main(string[] args)
        {
        }
    }
}
```

## Step 4: Hello World
Now let’s write our code which will be used to display the message “Hello, World!” in the console application.

To do so, modify the Main method of the Program class as shown in the below code, we will learn this in details later.

You can also copy the code below and replace all the code in Program.cs with this one:

```C#
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Day_0
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello, World!");
        }
    }
}
```

## Step 5
The next step is to run the .Net program. To run any program in Visual Studio, you need to click the Start button as
shown in the below image.

![Console app Step 4](console-app-step-4.png)

Once you click on the Start, you should get the following console window showing the message.

![Console app Step 5](console-app-step-5.png)