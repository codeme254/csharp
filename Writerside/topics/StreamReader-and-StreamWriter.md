# StreamReader and StreamWriter

## StreamWriter
The StreamWriter Class in C# is more popular in File Handling and it is very helpful in writing text data into a file.

It is easy to use and provides a complete set of constructors and methods to work on it.

If you go to the definition of StreamWriter class then you will see the following. The StreamWriter Class in C# 
belongs to the System.IO namespace and implements the abstract TextWriter class.

![StreamWriter Class Definition](file-handling-streamwriter-class-definition.png)

### Important Methods in the StreamWriter Class
- **Close()**; this method closes the current StreamWriter object and the underlying stream.
- **Flush()**: Forces any data that was waiting in memory to be immediately written into the file.
- **Write()**: Writes text to the file exactly as it is, without adding anything extra.
- **WriteLine()**: Same as `Write()`, but it also moves to a new line after writing.
- **Dispose()**: Cleans up and releases all the resources the writer was using. This happens automatically when you use
the `using` block.

### Example to Write Into a File Using the StreamWriter Class
In the below example, we are using the StreamWriter constructor (public StreamWriter(string path);) which takes the 
string path as an argument to create an instance of StreamWriter Class. This StreamWriter instance will create a 
file with the name MyFile.txt at the specified location.

When we call the Write method using the StreamWriter object by passing the string data, it will write the string 
data into the stream i.e. into the text file. Finally, we call the Flush and Close method to clear all the 
buffers as well as close the stream.

```C#
using System;
using System.IO;

namespace StreamWriterExample
{
    internal class Program
    {
        static void Main(string[] args)
        {
            StreamWriter sr = new StreamWriter(@"C:\Users\otwom\Desktop\example\MyFile.txt");
            sr.Write("Hello world, C# is an Object Oriented Programming Language");
            sr.Flush();
            sr.Close();
        }
    }
}
```

A better way is to use the `using` block, with this block, the stream writer will be closed and flushed automatically.
This is possible because the StreamWriter class implements `IDisposable`.

```C#
using System;
using System.IO;

namespace StreamWriterExample
{
    internal class Program
    {
        static void Main(string[] args)
        {
            using(StreamWriter sr = new StreamWriter(@"C:\Users\otwom\Desktop\example\MyFile.txt"))
            {
                sr.Write("Hello World, C# is an object oriented programming language");
            }
        }
    }
}
```

`Write()` and `WriteLine()` overwrite the content of a file, sometimes, you want to append content to the file instead.

If you want to do so, then you need to use the overloaded version of the StreamWriter constructor which takes the
boolean append parameter and pass the value true.

```C#
using System;
using System.IO;

namespace StreamWriterExample
{
    internal class Program
    {
        static void Main(string[] args)
        {
            using(StreamWriter sr = new StreamWriter(@"C:\Users\otwom\Desktop\example\numbers.txt", true))
            {
                for (int i = 0; i < 1_000; i++)
                {
                    sr.Write($"{i}, ");
                }
            }
        }
    }
}
```

## StreamReader Class in C#
The StreamReader class in C# allows us to read text files. Its implementation is easy and it is widely popular
among developers.

While working with C# StreamReader Class, you need to remember the following points.

- Implements TextReader that reads characters from a byte stream in a particular encoding.
- StreamReader class uses UTF-8 Encoding by default.
- StreamReader class is designed for character input in a particular encoding.
- Use this class for reading a standard text file.
- By default, it is not thread-safe.

If you go to the definition of StreamReader class then you will see the following. The StreamReader
class belongs to the System.IO namespace and implements the abstract TextReader class. The StreamReader 
class in C# is used for reading characters from the stream in a particular format.

![StreamReader class definition](file-handling-streamreader-class-definition.png)

### Important Methods in the StreamReader Class
- **Close()**: The Close method Closes the StreamReader object and the underlying stream, and releases any system 
resources associated with the reader. You don’t need to call this manually when using a `using` block.
- **Peek()**: Looks at the next character in the file without actually reading it. It returns a number representing 
that character, or -1 if there’s nothing left to read.
- **Read()**: This method reads the next character from the input stream and advances the character’s position 
by one character. The next character from the input stream is represented as an int, or -1 if no more 
characters are available.
- **ReadLine()**: Reads one line of text from the file and gives it back as a string. Returns `null` if 
there’s no more text to read.
- **Seek()**: Moves the reading/writing position in the file to a specific spot so you can read or write there.

### Example to Understand the StreamReader Class

```C#
using System;
using System.IO;

namespace StreamReaderExample
{
    internal class StreamReaderExample
    {
        static void Main(string[] args)
        {
            StreamReader sr = new StreamReader(@"C:\Users\otwom\Desktop\example\MyFile.txt");

            string data = sr.ReadLine();
            while (data != null)
            {
                Console.WriteLine(data);
                data = sr.ReadLine();
            }

            sr.Close();
        }
    }
}
```

Instead of the `ReadLine()` method, we can use `ReadToEnd()` method to read all the contents of a text file.

```C#
using System;
using System.IO;

namespace StreamReaderExample
{
    internal class StreamReaderExample
    {
        static void Main(string[] args)
        {
            StreamReader sr = new StreamReader(@"C:\Users\otwom\Desktop\example\MyFile.txt");

            string data = sr.ReadToEnd();
            Console.WriteLine(data);

            sr.Close();
        }
    }
}
```

In the example below, we are using the `using` block.

```C#
using System;
using System.IO;

namespace StreamReaderExample
{
    internal class StreamReaderExample
    {
        static void Main(string[] args)
        {
            using(StreamReader reader = new StreamReader(@"C:\Users\otwom\Desktop\example\MyFile.txt"))
            {
                string content = reader.ReadToEnd();
                Console.WriteLine(content);
            }
        }
    }
}
```