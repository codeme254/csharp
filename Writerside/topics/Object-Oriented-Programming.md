# Object Oriented Programming

Object-Oriented Programming, commonly known as OOPs, is a technique, not a technology. It means it doesn’t provide 
any syntaxes or APIs; instead, it provides suggestions on how to approach programming.

Object-Oriented Programming is a strategy that provides some principles for developing applications or software.

Like Object-Oriented Programming, other methodologies exist, and these include:
- Structured programming
- Procedural programming/Modular programming
However, one of the well-known and famous styles/approach today is Object Oriented Programming.

In Object-Oriented Programming, we think in terms of real world objects.

Object-Oriented Programming (OOP) is a programming paradigm (style or approach) that organizes software design 
around objects rather than functions or logic.

An object is a self-contained unit that bundles together data (called fields or attributes) and behavior 
(called methods or functions).

Instead of writing code as a list of instructions or procedures, OOP models programs as a collection of interacting
objects, much like real-world entities.

For example:
- A `Car` object might have data like `color`, `model`, and `speed`.
- And behaviors like `start()`, `accelerate()`, and `stop()`.

## Principles of Object-Oriented Programming
OOPs provide 4 principles. They are:
- Encapsulation
- Inheritance
- Polymorphism
- Abstraction


### Abstraction and Encapsulation
The process of representing the essential features without including the background details is called Abstraction. 
In simple words, we can say that it is a process of defining a class by providing necessary details to the external 
world, which are required by hiding or removing unnecessary things.

The process of binding the data and functions together into a single unit (i.e., class) is called Encapsulation. In 
simple words, we can say that it is a process of defining a class by hiding its internal data members from outside 
the class and accessing those internal data members only through publicly exposed methods or properties.

Data encapsulation is also called data hiding because, using this principle, we can hide the internal data from 
outside the class.

Suppose you want to design one class for providing the register functionality of a user. For that, what you need to 
do is first you need to get the data and validate the data, then you need to get the connection string for the 
database, and finally, you need to save the data in the database. And for this, you have three methods, i.e.,
`Validate`, `GetConnectionString`, and `SaveUser`. If you provide access to these three methods to the users 
of this class, then he may end up calling these methods in the wrong order, or it may be possible that 
he may forget to call any of these methods.

So, here, you need to create one method called Register, and as part of that method, you need to call all these 
methods (Validate, GetConnectionString, and SaveUser) in a proper sequence. Finally, you need to give access to the 
Register method instead of the Validate, GetConnectionString, and SaveUser methods.

This is **abstraction** and it is achieved through **encapsulation**!

![abstraction](oop-abstraction.png)

### Inheritance
The process by which the members of one class are transferred to another class is called inheritance.

The class from which the members are transferred is called the Parent/Base/Superclass, and the class that inherits 
the Parent/Base/Superclass members is called the Derived/Child/Subclass.

### Polymorphism
Refers to the ability of something to exist in more than one form.

There are two types of polymorphism in C#:
- Static polymorphism/compile-time polymorphism/early binding
- Dynamic polymorphism/Run time polymorphism/Late binding

Static polymorphism is achieved by function overloading and operator overloading, whereas dynamic polymorphism is 
achieved by function overriding.