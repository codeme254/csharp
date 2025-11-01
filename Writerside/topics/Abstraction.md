# Abstraction

> Exposing only what is necessary and hiding the rest

The process of representing the essential features without including the background details is called Abstraction.

Abstraction means exposing only what is necessary and compulsory and hiding unnecessary details from the outside world.

Abstraction lets you focus more on what an object does rather than how it does. That means deciding what services in a
class we want to expose instead of exposing how these services are implemented.

To take a real-time example, when we log in to any social networking site like Facebook, Twitter, LinkedIn, 
etc., we enter our user ID and password, and then we get logged in. Here, we don’t know how they are processing 
the data or what logic or algorithm they are using for login. This information is abstracted/hidden from us since 
they are not essential to us. This is basically what abstraction is.

## How to implement Abstraction in C#
In C#, we can implement the abstraction OOPs principle in two ways. 

They are as follows:
- Using interfaces
- Using abstract classes and abstract methods

We will discuss interfaces and abstract classes later.

for now, you just need to understand one thing: both interface and abstract classes and abstract methods provide 
some mechanism to hide the implementation details by only exposing the services. The user only knows what are 
services or methods available, but the user will not know how these services or methods are implemented. 

## Implementing Abstraction Using an Interface
In the example below, we are using an interface to achieve the abstraction principle in C#.

Using the interface, we can achieve 100% abstraction.

The user will only know the services that are defined in the interface, but how these services are implemented
will be abstracted away from them.

```C#
using System;

namespace AbstractionWithInterface
{
    interface IBank
    {
        void ValidateCard();
        void WithdrawCash();
        void CheckBalance();
        void BankTransfer();
        void MiniStatement();
    }

    class Bank: IBank
    {
        public void ValidateCard()
        {
            Console.WriteLine("Card vaildation");
        }
        public void WithdrawCash()
        {
            Console.WriteLine("Withdraw cash");
        }

        public void CheckBalance()
        {
            Console.WriteLine("Check balance");
        }

        public void BankTransfer()
        {
            Console.WriteLine("Bank transfer");
        }

        public void MiniStatement()
        {
            Console.WriteLine("Mini Statement");
        }
    }
    internal class AbstractionWithInterface
    {
        public static void Main(string[] args)
        {
            IBank b = new Bank();
            b.BankTransfer();
            b.ValidateCard();
        }
    }
}
```

Abstraction doesn’t mean physically hiding code from you, it means hiding the implementation details from 
the user of the class or interface at the level of interaction.

So when we write:
```C#
IBank b = new Bank();
b.BankTransfer();
b.ValidateCard();
```
From the perspective of the user of `IBank`, you:
- Don't know how `BankTransfer()` works internally.
- Don't need to know, you just know that calling it will perform a bank transfer.

You’re only exposed to the services (method signatures) defined by the interface:
```C#
void ValidateCard();
void WithdrawCash();
void CheckBalance();
void BankTransfer();
void MiniStatement();
```

The variable b only knows about the methods defined in IBank, not any other internal details of the Bank class. `b` can
only access the methods declared in the interface and not the extra methods the Bank class might have and this is
abstraction.

```C#
using System;

namespace AbstractionWithInterface
{
    interface IBank
    {
        void ValidateCard();
        void WithdrawCash();
        void CheckBalance();
        void BankTransfer();
        void MiniStatement();
    }

    class Bank: IBank
    {
        public void ValidateCard()
        {
            Console.WriteLine("Card vaildation");
        }
        public void WithdrawCash()
        {
            Console.WriteLine("Withdraw cash");
        }

        public void CheckBalance()
        {
            Console.WriteLine("Check balance");
        }

        public void BankTransfer()
        {
            Console.WriteLine("Bank transfer");
        }

        public void MiniStatement()
        {
            Console.WriteLine("Mini Statement");
        }

        public void AnotherBankMethod()
        {
            Console.WriteLine("Another bank method");
        }
    }
    internal class AbstractionWithInterface
    {
        public static void Main(string[] args)
        {
            IBank b = new Bank();
            b.BankTransfer();
            b.ValidateCard();
            //b.AnotherBankMethod(); // Error
        }
    }
}
```

## Implementing Abstraction Using Abstract Classes
We can also achieve abstraction using abstract classes and methods.

```C#
using System;

namespace AbstractionWithAbstractClasses
{
    abstract class IBank
    {
        public abstract void WithdrawMoney();
        public abstract void CheckBalance();
    }

    class Bank : IBank
    {
        public override void WithdrawMoney()
        {
            Console.WriteLine("Withraw cash");
        }

        public override void CheckBalance()
        {
            Console.WriteLine("Check balance");
        }

        public void AnotherBankMethod()
        {
            Console.WriteLine("Another bank method");
        }
    }
    internal class AbstractionWithAbstractClasses
    {
        public static void Main(string[] args)
        {
            IBank b = new Bank();
            b.CheckBalance();
            b.CheckBalance();
            //b.AnotherBankMethod(); // Error
        }
    }
}
```