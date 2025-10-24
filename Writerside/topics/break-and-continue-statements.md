# jumping statements

The Jump Statements in C# are used to transfer control from one point or location or statement to another point
or location or statement in the program due to some specified condition while executing the program.

The Jump Statements allow us to exit a loop, and start the next iteration, or explicitly transfer the program 
control to a specified location in your program.

C# supports the following jumping statements:
- break
- continue
- goto
- return
- throw

Here, we are going to discuss break, continue and goto statements.

## break Statement
By using the break statement, we can terminate either the loop body or the switch body.

The use of a break statement is optional but if you want to use then the break statement should be placed either
within the loop body or switch body.

We use the break statement when we know the maximum number of repetitions of a loop but there is a condition in which
we need to terminate the loop body.

The break statement is almost always used with the if…else statement inside the loop body.

![break statement flowchart](control-flow-break-statements.png)

In the example below, the loop terminates when it encounters number 5:

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            for (int num = 1; num <= 100; num++)
            {
                if (num == 5)
                {
                    break;
                }
                Console.WriteLine($"Number: {num}");
            }
        }
    }
}
```

## continue statement
By using the continue keyword, we can skip the statement execution from a loop body.

Like the break statement, the use of the continue statement is also optional but if you want to use then you can 
use it only within a loop body.

We use the continue statement when we know the maximum number of repetitions but we have some conditions and when the
condition is satisfied we need to skip the statement execution from the loop body and we need to continue the loop 
execution in the next iteration.

**The BREAK statement terminates the loop, whereas the CONTINUE statement skips only the current loop iteration, 
and allows the next loop iteration to proceed.**

The continue statement is almost always used with the if…else statement.

![continue statement flowchart](control-flow-continue-statement-flowchart.png)

The following program prints all the numbers between 1 and 100 except the ones that are divisible by 5:

```C#
namespace ControlFlow
{
    internal class Program
    {
        static void Main(string[] args)
        {
            for (int num = 1; num <= 100; num++)
            {
                if (num % 5 == 0)
                {
                    continue;
                }
                Console.WriteLine($"Number: {num}");
            }
        }
    }
}
```