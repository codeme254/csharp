# Selection Statements

Also called decision making statements/branching statements.

In programming, we always face some situations where we want a certain block of code to be executed when some
condition is fulfilled.

The decision-making statements in C# allow us to make a decision, based upon the result of a condition. If the 
condition is satisfying, we may need to execute some piece of code and if the condition is failed, we might need 
to execute some other piece of code.

Selection statements can be divided into the following categories:
- if-else statements
- Switch statements

## if statement
It executes a block of statements (one or more instructions) when the condition in the if block is true and when 
the condition is false, it will skip the execution of the if block.

![if statement](control-flow-if-template.png)

Below is the flow chart for if statement:

![if statement flow chart](control-flow-if-flow-chart.png)

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int johnAge = 28;
            if (johnAge > 18)
            {
                Console.WriteLine("John is an adult");
            }
        }
    }
}
```

If you have a single statement for if block, then you can represent that statement either using curly braces or 
without using curly braces. But if you have more than one statement inside the if block, then it is mandatory
to use curly braces.

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int johnAge = 28;
            if (johnAge > 18)
                Console.WriteLine("John is an adult");
        }
    }
}
```

## if else statement
The If-Else block in C# Language is used to provide some optional information whenever the given condition is FALSE 
in the if block.

That means if the condition is true, then the if block statements will be executed, and if the condition is false, 
then the else block statement will execute.

![if else statement](control-flow-if-else-statement.png)

The following is the flowchart for an if else statement:

![if else flowchart](control-flow-if-else-flowchart.png)

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int johnAge = 8;
            if (johnAge > 18)
            {
                Console.WriteLine("John is an adult");
            }
            else
            {
                Console.WriteLine("John is not yet an adult");
            }
        }
    }
}
```

Note: For every if condition statement, the else block is optional. But for every else block, the if block is 
compulsory.

## Nested if-else statement
When an if-else statement is present inside the body of another if or else then this is called nested if-else.

Nested IF-ELSE statements are used when we want to check for a condition only when the previous dependent condition 
is true or false. 

![nested if else statements](control-flow-nested-if-else-statements.png)

Following is a flowchart for nested if else statements:

![nested if else statements flowchart](control-flow-nested-if-else-flowchart.png)

In the example below, we are finding largest of three numbers using nested if else statement:

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int a = 15, b = 25, c = 10;
            if (a > b)
            {
                if (a > c)
                {
                    Console.WriteLine($"Largest number is {a}");
                }
                else
                {
                    Console.WriteLine($"Largest number is {c}");
                }
            }
            else
            {
                if (b > c)
                {
                    Console.WriteLine($"Largest number is {b}");
                }
                else
                {
                    Console.WriteLine($"Largest number is {c}");
                }
            }
        }
    }
}
```

## if else ladder

In Ladder if-else statements one of the statements will be executed depending upon the truth or false of the 
conditions. If the condition1 is true then Statement 1 will be executed, and if condition2 is true then statement 
2 will be executed, and so on. But if all conditions are false, then the last statement i.e. else block statement 
will be executed.

![if else ladder](control-flow-if-else-ladder.png)

Following is the flowchart for an if else ladder:

![if else ladder flowchart](control-flow-if-else-ladder-flowchart.png)

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int i = 20;
            if (i == 10)
            {
                Console.WriteLine("i is 10");
            }
            else if (i == 15)
            {
                Console.WriteLine("i is 15");
            }
            else if (i == 20)
            {
                Console.WriteLine("i is 20");
            }
            else
            {
                Console.WriteLine("We don't know i");
            }
        }
    }
}
```

## Switch Statement
The switch is a keyword in the C# language, and by using this switch keyword we can create selection statements 
with multiple blocks. And the Multiple blocks can be constructed by using the `case` keyword.

Switch case statements in C# are a substitute for long if else statements that compare a variable or expression 
to several values.

Following is the syntax for switch statement:

![Control flow switch statement](control-flow-switch-statement.png)

The default block in the switch statement is optional. That means you can create the switch statements without
the default block and, it would run without any problem.

We need to use the break statement inside the switch block to terminate the switch statement execution. That means
when the break statement is executed, the switch terminates, and the flow of control jumps to the next line following
the switch statement. The break statement is mandatory.

Nesting of switch statements is allowed, which means you can have switch statements inside another switch. 
However nested switch statements are not recommended by Microsoft. This is because it makes the program 
more complex and less readable.

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int dayNumber = 5;
            switch (dayNumber)
            {
                case 1:
                    Console.WriteLine("Monday");
                    break;
                case 2:
                    Console.WriteLine("Tuesday");
                    break;
                case 3:
                    Console.WriteLine("Wednesday");
                    break;
                case 4:
                    Console.WriteLine("Thursday");
                    break;
                case 5:
                    Console.WriteLine("Friday");
                    break;
                case 6:
                    Console.WriteLine("Saturday");
                    break;
                case 7:
                    Console.WriteLine("Sunday");
                    break;
                default:
                    Console.WriteLine("Unknown day number");
                    break;
            }
        }
    }
}
```

Although the switch statement makes the code look cleaner than the if…else if statement, the switch is restricted 
to work with limited data types.

The switch statement only works with:
- Primitive data types
- Enumerated data types (Enum)
- String class
- Nullable types of the above data types