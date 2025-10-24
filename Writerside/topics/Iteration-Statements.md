# Iteration Statements

Also called repeating statements or iterative statements or loops.

Looping in programming languages is a feature that facilitates the execution of a set of instructions repeatedly 
while some condition evaluates to true.

The process of repeatedly executing a statement or group of statements until the condition is satisfied is called 
looping. In this case, when the condition becomes false the execution of the loops terminates.

Loops can be categorized into two:
- Counter loops: are the loops, which execute a specific set of instructions a certain number of known times.
- Conditional loops: are the loops, which execute a specific task until a certain condition is true.


There are 4 looping statements in C# and they are as follows:
- for loop
- for each loop
- while loop
- do while loop

The general flowchart for loops is something like this:

## while Loop
A while loop is used for executing a statement repeatedly until a given condition returns false.

The while loop keeps iterating while a certain condition is true.

![While loop syntax](control-flow-while-loop-syntax.png)

Following is the flowchart for a while loop:

![While loop flowchart](control-flow-while-loop-flowchart.png)

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int x = 1;
            while (x <= 5)
            {
                Console.WriteLine($"The value of x is {x}");
                x++;
            }
        }
    }
}
```

## do while loop
We use the do while loop when we need to execute the body of the loop at least once.

The loop is created by using the do keyword followed by open and close curly braces. In between the open and close 
curly braces, you can write the statements which you want to execute at least once. And after the close curly braces, 
you need to write the while condition. Please note that the while condition statement ends with a semicolon. The 
condition expression must be a boolean expression.

![do while loop syntax](control-flow-do-while-syntax.png)

Following is a flowchart for the do while loop

![do while loop flowchart](control-flow-do-while-flowchart.png)

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int val = 1;
            do
            {
                Console.WriteLine($"Value: {val}");
                val++;
            } while (val <= 10);
        }
    }
}
```

## for loop
We use the for loop when we know the number of times we want to execute  some set of statements or instructions.

![for loop syntax](control-flow-for-loop-syntax.png)

A for loop has the following four staages:
- **initialization**: this is where we initialize the counter variable.
- **condition**: Conditions in for loop are executed for each iteration and if the condition is true, it executes the
C# instruction and if the condition is false then it comes out of the loop.
- **instruction**: Once the condition is evaluated, and if the condition is true, then the control comes to
the loop body i.e. the loop body is going to be executed.
- **increment/decrement**:  After executing the loop body, the increment/decrement part of the for loop will be 
executed, and once it executes the increment decrement part i.e. once it increments and decrements the counter 
variable, again it will go to the condition evaluation stage.

Following is a flowchart for the for loop:

![for loop flowchart](control-flow-for-loop-flowchart.png)

The example below prints all numbers from 1 to 100:

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            for (int num = 1; num <= 100; num++)
            {
                Console.WriteLine($"Current number {num}");
            }
        }
    }
}
```