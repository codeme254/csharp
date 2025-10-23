# Operators

Operators are symbols used to perform operations on operands.

For example, consider the expression 2 + 3 = 5, here 2 and 3 are operands, and + and = are called operators.

The Operators are classified based on the type of operations they perform on operands in C# language.  
They are as follows:
- Arithmetic Operators
- Relational Operators
- Logical Operators
- Bitwise Operators
- Assignment Operators
- Unary Operators or
- Ternary Operator or Conditional Operator

Operators can also be categorized based on the Number of Operands:
- **Unary Operators**: The Operator that requires one operand (variable or value) to perform the operation is 
called Unary Operator.
- **Binary Operator**: The Operator that requires two operands (variables or values) to perform the operation 
is called Binary Operator.
- **Ternary Operator**: The Operator that requires three operands (variables or values) to perform the operation 
is called Ternary Operator. The Ternary Operator is also called Conditional Operator.

![Operators](operators.png)

## Arithmetic Operators
The Arithmetic Operators in C# are used to perform arithmetic/mathematical operations like addition, subtraction, 
multiplication, division, etc. on operands.

The following Operators are falling into this category. 

They are as follows:

### Addition Operator (+)
The + operator adds two operands. As this operator works with two operands, so, this + (plus) operator belongs to 
the category of the binary operator. The + Operator adds the left-hand side operand value with the right-hand 
side operand value and returns the result.

### Subtraction Operator (-)
The – operator subtracts two operands. As this operator works with two operands, so, this – (minus) operator belongs
to the category of the binary operator. The Minus Operator substracts the left-hand side operand value from the 
right-hand side operand value and returns the result.

### Multiplication Operator (*)
The * (Multiply) operator multiplies two operands. As this operator works with two operands, so, this * (Multiply) 
operator belongs to the category of the binary operator. The Multiply Operator multiplies the left-hand side operand
value with the right-hand side operand value and returns the result.

### Division Operator (/)
The / (Division) operator divides two operands. As this operator works with two operands, so, this / (Division) 
operator belongs to the category of the binary operator. The Division Operator divides the left-hand side operand 
value with the right-hand side operand value and returns the result.

### Modulus Operator (%)
The % (Modulos) operator returns the remainder when the first operand is divided by the second. As this operator 
works with two operands, so, this % (Modulos) operator belongs to the category of the binary operator.

```C#
namespace Operators
{
    internal class Opeartors
    {

        static void Main()
        {
            int a = 10;
            int b = 5;
            // Addition
            Console.WriteLine(a + b);
            // Subtraction
            Console.WriteLine(a - b);
            // Multiplication
            Console.WriteLine(a * b);
            // Divison
            Console.WriteLine(a / b);
            // Modulos
            Console.WriteLine(a % b);
        }
    }
}
```

## Assignment Operators
The Assignment Operators in C# are used to assign a value to a variable.

The left-hand side operand of the assignment operator is a variable and the right-hand side operand of the assignment 
operator can be a value or an expression that must return some value and that value is going to assign to the left-hand 
side variable.

The value on the right-hand side must be of the same data type as the variable on the left-hand side else you will 
get a compile-time error.

The different Types of Assignment Operators supported in the C# language are as follows:

### Simple Assignment (=)
This operator is used to assign the value of the right-hand side operand to the left-hand side operand i.e. 
to a variable. 

### Addition Assigment (+=)
This operator is the combination of + and = operators. It is used to add the left-hand side operand value with the
right-hand side operand value and then assign the result to the left-hand side variable.

### Subtraction Assignment (-=)
This operator is the combination of – and = operators. It is used to subtract the right-hand side operand value from 
the left-hand side operand value and then assign the result to the left-hand side variable.

### Multiplication Assignment (*=)
This operator is the combination of * and = operators. It is used to multiply the left-hand side operand value with
the right-hand side operand value and then assign the result to the left-hand side variable.

### Division Assignment (/=)
This operator is the combination of / and = operators. It is used to divide the left-hand side operand value with the
right-hand side operand value and then assign the result to the left-hand side variable.

### Modulus Assignment (%=)
This operator is the combination of % and = operators. It is used to divide the left-hand side operand value with the 
right-hand side operand value and then assigns the remainder of this division to the left-hand side variable.

```C#
namespace Operators
{
    internal class Opeartors
    {

        static void Main()
        {
            /// Assignment Operators
            //Simple Assignment Operator
            int x = 10;
            Console.WriteLine(x); // 10
            // Addition Assignment
            int aa = 10;
            aa += 20;
            Console.WriteLine(aa); // 30
            // Subtraction Assignment
            int sa = 20;
            sa -= 15;
            Console.WriteLine(sa); // 5
            // Multiplication Assignment
            int ma = 10;
            ma *= 50;
            Console.WriteLine(ma); // 500
            // Division Assignment
            int da = 50;
            da /= 10;
            Console.WriteLine(da); // 5
            // Modulus Assignment
            int mas = 50;
            mas %= 3;
            Console.WriteLine(mas); // 2
        }
    }
}
```

## Relational Operators
The Relational Operators in C# are also known as Comparison Operators.

They are used to determine relationship between two operators and return boolean result i.e true or false.

The different types of relational operators in C# are:

### Equal to (==)
This Operator is used to return true if the left-hand side operand value is equal to the right-hand side operand value.
Otherwise, it returns false.

### Not Equal To (!=)
This Operator is used to return true if the left-hand side operand value is not equal to the right-hand side operand
value. Otherwise, it returns false.

### Less Than (<)
This Operator is used to return true if the left-hand side operand value is less than the right-hand side operand value.
Otherwise, it returns false.

### Less than or equal to (<=)
This Operator is used to return true if the left-hand side operand value is less than or equal to the right-hand 
side operand value. Otherwise, it returns false.

### Greater than (>)
This Operator is used to return true if the left-hand side operand value is greater than the right-hand side operand 
value. Otherwise, it returns false.

### Greater than or equal to (>=)
This Operator is used to return true if the left-hand side operand value is greater than or equal to the right-hand 
side operand value.

```C#
namespace Operators
{
    internal class Opeartors
    {

        static void Main()
        {
            /// Relational Operators
            // Equal to
            Console.WriteLine(10 == 10); // True
            Console.WriteLine(10 == 20); // False
            // Not Equal to
            Console.WriteLine(10 != 20); // True
            Console.WriteLine(10 != 10); // False
            // Less Than
            Console.WriteLine(10 < 20); // True
            Console.WriteLine(10 < 5); // False
            // Less Than or equal to
            Console.WriteLine(10 <= 10); // True
            Console.WriteLine(20 <= 10); // False
            // Greater than
            Console.WriteLine(20 > 10); // True
            Console.WriteLine(10 > 20); // False
            // Greater Than or equal to
            Console.WriteLine(10 >= 10); // True
            Console.WriteLine(10 >= 20); // False
        }
    }
}
```

## Logical Operators
The Logical Operators are mainly used in conditional statements and loops for evaluating a condition.

These operators work with boolean expressions.

The different types of logical operators supported in c# are:

### Logical OR (||)
This operator is used to return true if either of the Boolean expressions is true.

That means the Logical OR (||) operator returns true when one (or both) of the conditions in the expression is 
satisfied. Otherwise, it will return false.

### Logical AND (&&)
This operator is used to return true if all the Boolean Expressions are true. For example, false && true is 
evaluated to be false.

That means the Logical AND (&&) operator returns true when both the conditions in the expression are satisfied. 
Otherwise, it will return false.

### Logical NOT (!)
This operator is used to return true if the condition in the expression is not satisfied. Otherwise, it will 
return false.

In other words, it flips the result of `AND` and `OR` logical operators

```C#
namespace Operators
{
    internal class Opeartors
    {

        static void Main()
        {
            /// Logical Operators
            // Logical OR (||)
            Console.WriteLine(true || false); // True
            Console.WriteLine(false || true); // True
            Console.WriteLine(true || true); // True
            Console.WriteLine(false || false); // False

            // Logical AND (&&)
            Console.WriteLine(true && true); // True
            Console.WriteLine(true && false); // false
            Console.WriteLine(false && true); // false
            Console.WriteLine(false && false); // false

            // Logical NOT (!)
            Console.WriteLine(!true); // False
            Console.WriteLine(!false); // True
        }
    }
}
```

## Unary Operators
Unary operators are operators that need only one operand.

They are used to increment or decrement a value.

There are two types of unary operators:
- Increment Operator (++)
- Decrement Operator (--)

### Increment Operator
Also classified into two:
- Post-increment operator
- Pre-increment operator

#### Post-increment operator (x++)
Increments the value of a variable.

It is placed after the variable for example: `x++;`

**It increments the value after it is used in the expression**

#### Pre-increment Operator (++x)
Also increments the value of a variable.

It is placed before the variable for example: `++x`

**It increments the value before it is used in the expression**

```C#
namespace Operators
{
    internal class Opeartors
    {

        static void Main()
        {
            // Post-increment operator
            int y = 5;
            int z = y++;
            Console.WriteLine(z); // 5
            Console.WriteLine(y); // 6

            // Pre-increment operator
            int j = 5;
            int k = ++j;
            Console.WriteLine(k); // 6
            Console.WriteLine(j); // 6
        }
    }
}
```

### Decrement Operators
Also classified into two:
- Post-decrement operator.
- Pre-decrement operator.

#### Post-decrement operator
Decrements the value of a variable.

It is placed after the variable for example: `x--;`

**It decrements the value after it is used in the expression**

#### Pre-decrement operator
Also decrements the value of a variable.

It is placed before the variable for example: `--x`

**It decrements the value before it is used in the expression**

```C#
namespace Operators
{
    internal class Opeartors
    {

        static void Main()
        {
            // Post-decrement operator
            int c = 5;
            int d = c--;
            Console.WriteLine(d); // 5
            Console.WriteLine(c); // 4

            // Pre-decrement operator
            int h = 5;
            int i = --h;
            Console.WriteLine(i); // 4
            Console.WriteLine(h); // 4
        }
    }
}
```

## Ternary Operator
The Ternary Operator in C# is also known as the Conditional Operator (?:).

It is actually the shorthand of the if-else statement.

It is called ternary because it has three operands or arguments. The first argument is a comparison argument, the 
second is the result of a true comparison, and the third is the result of a false comparison.

Syntax: `Condition? first_expression : second_expression;`

```C#
namespace Operators
{
    internal class Opeartors
    {

        static void Main()
        {
            int age = 25;
            string s = age > 18 ? "Adult" : "Child";
            Console.WriteLine(s); // Adult
        }
    }
}
```