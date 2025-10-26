# Properties in C#

In order to encapsulate and protect the data members (i.e. fields or variables) of a class, we use properties in C#.

The Properties in C# are used as a mechanism to set and get the values of data members of a class outside of that class.

If a class contains any values in it and if we want to access those values outside of that class, then we can provide
access to those values in 2 different ways:
1. By storing the value under a public variable: gives direct access to the value outside of the class.
2. By storing the value in a private variable: we can also give access to that value outside of the class by
defining a property for that variable.

## What is a property in C#

A Property in C# is a member of a class that is used to set and get the data from a data field (i.e. variable)
of a class.

The most important point that you need to remember is that a property in C# is never used to store any data, it just
acts as an interface or medium to transfer the data.

We use properties as if they are public data members of a class but they are actually special methods called
**accessors**.

## What are accessors in C#?
The Assessors are nothing but special methods which are used to set and get the values from the underlying 
data member (i.e. variable) of a class.

Accessors are of two types:
- **Set accessor**
- **Get accessor**

### Set accessor
The set accessor is used to set the data (i.e. value) into a data field i.e. a variable of a class.

This set accessor contains a fixed variable named **value**.

Whenever we call the property to set the data, whatever data (value) we are supplying will come and store inside the 
variable called **value** by default.

Using a set accessor, we cannot get the data.

Syntax: `set {Data_Field_Name = value; }`

### Get accessor
The get accessor is used to get the data from the data field i.e. variable of a class.

Using the get accessor, we can only get the data, we cannot set the data.

Syntax: `get { return Data_Field_Name; }`

### Example to understand Accessors
Here, we have created two classes i.e. Employee and Program and we want to access the Employee class data members 
inside the Program class.

In the Employee class, we have created two private data members (i.e. _EmpId and _EmpName) to hold the Employee Id and 
Name of the Employee and as we mark these two variables as private, so we cannot access directly these two members 
from outside the Employee class.

We cannot access them directly from the Program class.

Then for these two data members, we have created two public properties i.e. EmpId and EmpName to get and set the 
Employee ID and Name respectively. The point that you need to remember is properties are not going to store the value, 
rather they are just transferring the values. The variables are going to store the data.

<note>
Note: Whenever we create a property for a variable, the data type of the property must be the same as the data type
of the variable. A property can never accept any argument.
</note>
```C#
namespace Properties
{
    public class Employee
    {
        private int _EmpId;
        private string _EmpName;

        // Public property for _EmpId
        public int EmpId
        {
            // Set accessor to set _EmpId private variable/field
            set
            {
                _EmpId = value;
            }

            // Get accessor to return _EmpId private variable value
            get
            {
                return _EmpId;
            }
        }

        // Public property for _EmpName
        public string EmpName
        {
            // Set accessor to set _EmpName private variable/field
            set
            {
                _EmpName = value;
            }

            // Get accessor to return _EmpName private variable value
            get
            {
                return _EmpName;
            }
        }
    }
    internal class Program
    {
        public static void Main(string[] args)
        {
            Employee e = new Employee();
            // We cannot access private data members
            // So we use set accessors to set the values
            e.EmpId = 100;
            e.EmpName = "John";

            // We use get accessors to get the values
            Console.WriteLine(e.EmpId);
            Console.WriteLine(e.EmpName);
        }
    }
}
```

## Different types of properties supported by C#.NET
The C#.NET supports four types of properties. They are as follows:
- Read only property
- Write only property
- Read write property
- Auto implemented property

### Read only property
A property in which we only implement the get accessor is referred to as the read only property.

The Read-Only Property is used to read the data from the data field i.e. read the data of a class.

Using this Read-Only Property, we cannot set the data into the data field.

```C#
        public int EmpId
        {
            get
            {
                return _EmpId;
            }
        }
```

### Write only property
A property in which we only implement the set accessor is referred to as the write only property.

The write only Property is used to write data into the data field i.e. write the data of a class.

Using this Write-Only Property, we cannot read the data from the data field.

```C#
        public int EmpId
        {
            set
            {
                _EmpId = value;
            }
        }
```

### Read Write property
The property in which we implement both the get and set accessor is referred to as the read write property.

It is used for both reading the data from the data field as well as writing the data into the data field of a class.

```C#
        public int EmpId
        {
            // Set accessor to set _EmpId private variable/field
            set
            {
                _EmpId = value;
            }

            // Get accessor to return _EmpId private variable value
            get
            {
                return _EmpId;
            }
        }
```

### Auto Implemented Properties
If you do not have any additional logic while setting and getting the data from a data field i.e. from a variable
of a class, then you can make use of the auto-implemented properties which was introduced as part of C# 3.0.

The Auto-Implemented Property in C# reduces the amount of code that we have to write.

Instead of writing a private field and a full property, you let the compiler generate the field for you 
automatically behind the scenes.

Before auto properties, or if we do it manually, we would have to write something like this:
```C#
class Person
{
    private string _name;  // backing field

    public string Name
    {
        get { return _name; }
        set { _name = value; }
    }
}
```
That works fine, but it’s too verbose when you’re just storing and retrieving data.

Using auto implemented properties, you can write:

```C#
class Person
{
    public string Name { get; set; }
}
```
Here:
- The compiler automatically creates a hidden backing field for Name.
- The property still behaves like the long version above.

## Default Accessibility Specifier of Accessors in C#
The default accessibility specifier of the accessor is the same as the accessibility specifier of the property.

For example:
```C#
public int EmpId
{
     set { _EmpId = value; }
     get {  return _EmpId; }
}
```

In the above example, the property `Empid` is declared as public. So, the set and get accessor will be public. If the
property is private then both set and get accessors will also be private.

## Symmetric and Asymmetric Accessors in C#
If the accessibility specifier of the accessors (both get and set) are the same within a property accessibility 
specifier then the accessors are known as symmetric accessors.

Example:
```C#
public int EmpId
{
     set { _EmpId = value; }
     get {  return _EmpId; }
}
```

On the other hand, if the accessibility specifier of the accessors is not the same as a property accessibility
specifier, then the accessors are known as asymmetric accessors. 

For example:
```C#
public int EmpId
{
      private set { _EmpId = value; }
      get { return _EmpId; }
}
```

In the above property, the set accessor is declared as private while the get accessor is public by default, 
so they are known as asymmetric.

## Advantages of properties
1. Properties will provide the abstraction to the data fields.
2. They also provide security to the data fields.
3. Properties can also validate the data before storing it in the data fields.