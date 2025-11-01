# Encapsulation

Encapsulation Hides the internal state and functionality of an object and only allows access through a public 
set of functions.

The process of binding or grouping the State (i.e., Data Members) and Behaviour (i.e., Member Functions) together into
a single unit (i.e., class, interface, struct, etc.) is called Encapsulation.

<note>
The encapsulation principle ensures that state and behavior of a unit cannot be accessed directly from other units.
</note>

## A Basic Example Of Encapsulation
```C#
using System;

namespace Encapsulation
{
    class Bank
    {
        public long AccountNumber;
        public string Name;
        public int Balance;

        public void GetBalance()
        {
            // Get Account Balance
        }
        public void WithdrawAmount()
        {
            // Withdraw Amount
        }
        public void Depost()
        {
            // Deposit Amount
        }
    }
}
```

Here, the class Bank is an example of Encapsulation.

The variables(AccountNumber, Name, and Balance) and methods(GetBalance, WithdrawAmount, and Deposit) of the class
are bound in a single unit, which is the Bank class.

<note>
The biggest advantage of encapsulation is <strong>Data Hiding</strong> which helps us to prevent 'data misuse'.
</note>

## What is Data Hiding
Data hiding or Information Hiding is a Process in which we hide internal data from outside the world.

The purpose of data hiding is to protect the data from misuse by the outside world.

Without encapsulation, we cannot achieve data hiding.

**In simple words, we can also say that the process of defining a class by hiding its internal data members from 
outside the class and accessing those internal data members only through publicly exposed methods 
(setter and getter methods) or properties with proper validations is called Encapsulation.**

Data Encapsulation is also called Data Hiding because by using this principle, we can hide the internal data 
from outside the class.

### How can we implement data hiding or encapsulation in C#
In C#, encapsulation/data hiding is implemented by:
1. By declaring the variables as private (to restrict their direct access from outside the class)
2. By defining one pair of public setter and getter methods or properties to access private variables from outside 
the class.

We declare variables as private to stop accessing them directly from outside the class. The public setter and getter 
methods or public properties are used to access the private variables from outside the class with proper validations.

## Implementing data hiding/encapsulation using getters and setters methods
In the following example, we declare the balance variable as private in the Bank class, and hence, it can not be 
accessed directly from outside the Bank class.

To access the private balance variable from outside the Bank class, we have exposed two public methods, i.e., 
GetBalance and SetBalance. The GetBalance method (which is also called getter) is used to fetch the value stored 
in the private balance variable, and the SetBalance method (which is also called Setter) is used to set the value 
in the private balance variable from outside the bank class.

Within the Bank class, you can access the private variables directly, but you cannot access them directly from 
outside the Bank class.
```C#
using System;

namespace Encapsulation
{
    class Bank
    {
        // Hiding data by declaring the variable as private
        private double balance;

        // Getter method
        // This method returns the data stored in balance variable
        public double GetBalance()
        {
            return balance;
        }

        // Setter method
        // This method is used to store data in the balance variable
        public void SetBalance(double val)
        {
            balance = val;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Bank bank = new Bank();
            //Console.WriteLine(bank.balance); // Compile Time Error
            
            // You need to access the balance using provided getters and setters
            bank.GetBalance();
            bank.SetBalance(9000);
            Console.WriteLine(bank.GetBalance());
        }
    }
}
```

The advantage of the above set up where we are working with getters and setters is that we can validate the user-given
data before storing the value in the variable.

In the above program, for example, if you don’t want to store negative values in the balance variable, you can check and
validate the value before storing it in the variable.

```C#
using System;

namespace Encapsulation
{
    class Bank
    {
        // Hiding data by declaring the variable as private
        private double balance;

        // Getter method
        // This method returns the data stored in balance variable
        public double GetBalance()
        {
            return balance;
        }

        // Setter method
        // This method is used to store data in the balance variable
        public void SetBalance(double val)
        {
            if (val < 0)
            {
                Console.WriteLine("Invalid Amount"); ;
                return;
            }
            balance = val;
        }
    }
    internal class Program
    {
        static void Main(string[] args)
        {
            Bank bank = new Bank();
            //Console.WriteLine(bank.balance); // Compile Time Error
            
            // You need to access the balance using provided getters and setters
            bank.GetBalance();
            bank.SetBalance(9000);
            Console.WriteLine(bank.GetBalance());
            bank.SetBalance(-5000); // Invalid Amount
            Console.WriteLine(bank.GetBalance()); // Still 9000
        }
    }
}
```

## Implementing data hiding/encapsulation using C# properties
Properties in C# help in protecting a field or variable of a class by reading and writing the values to it.

The first approach, i.e., setter and getter itself, is good, but Data Encapsulation in C# can be accomplished much 
smoother with properties which are getters and setters in their own way.

In the below example, inside the Bank class, we marked the _Amount variable as private to restrict direct access 
from outside the Bank class. We have exposed the Amount property to access the _Amount variable by declaring it as 
public. Now, from outside the Bank class, we can access the _Amount private variable through the public exposed 
Amount property.

```C#
// Implementing Encapsulation Through Properties
using System;


namespace EncapsulationUsingProperties
{
    class Bank
    {
        private double _Amount;
        public double Amount
        {
            get
            {
                return _Amount;
            }

            set
            {
                if (value < 0)
                {
                    Console.WriteLine("Invalid Amount");
                    return;
                }
                _Amount = value;
            }
        }
    }
    internal class EncapsulationUsingProperties
    {
        public static void Main(string[] args)
        {
            Bank b = new Bank();
            Console.WriteLine(b.Amount);
            b.Amount = 9000;
            Console.WriteLine(b.Amount); // 9000
            b.Amount = -5000; // Invalid Amount
            Console.WriteLine(b.Amount); // 9000
        }
    }
}
```

