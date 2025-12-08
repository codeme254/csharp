# File Class

The File Class in C# Provides some static methods to perform most file operations, such as Creating a File, 
Copying and Moving a File, Deleting Files, and working with FileStream to read and write streams.

The File class is defined in the System.IO namespace. There can be situations where you want to work with 
files directly.

The File class in C# exposes many static methods for moving, copying, reading, writing, and deleting files among other
things.

## Important Methods in the File Class
The following are commonly used methods of the File Class in C#:
- **Copy**: This method is used to Copy an existing file to a new file. Overwriting a file of the same name is
not allowed.
- **Create**: creates or overwrites in the path specified.
- **Decrypt**: This method is used to Decrypt a file encrypted by the current account using the 
System.IO.File.Encrypt(System.String) method.
- **Delete**: This method is used to delete the specified file.
- **Encrypt**: This method is used to encrypt a file so that only the account used to encrypt the file can decrypt it.
- **Open**: This method is used to Open a System.IO.FileStream on the specified path, having the specified 
mode with reading, write, or read/write access and the specified sharing option.
- **Move**: This method is used to Move a specified file to a new location, providing the option to specify a new file 
name.
- **Exists**: This method is used to determine whether the specified file exists.
- **OpenRead**: This method is used to open an existing file for reading.
- **OpenText**: This method opens an existing UTF-8 encoded text file for reading.
- **OpenWrite**: This method is used to open an existing file or create a new file for writing.
- **ReadAllBytes**: This method is used to open a binary file, read the file’s contents into a byte array, and 
then close the file.
- **ReadAllLines**: This method is used to Open a file, read all lines of the file with the specified encoding, and 
then close the file.
- **ReadAllText**: This method is used to Open a text file, read all the text in the file, and then close the file.
- **ReadAllLines**: This method is used to read the lines of a file.
- **Replace**: This method is used to replace a specified file’s contents with another file’s contents, delete the 
original file, and create a backup of the replaced file.
- **WriteAllBytes**: This method is used to create a new file, write the specified byte array to the file, and then
close the file. If the target file already exists, it is overwritten.
- **WriteAllLines**: This method is used to create a new file, write the specified string array to the file, and 
then close the file.
- **WriteAllText**: This method is used to create a new file, write the specified string to the file, and then 
close the file. If the target file already exists, it is overwritten.

## Exists Method
The Exists Method of File Class in C# is used to check whether a particular file exists. This method will return true
if the caller has the required permissions and the path contains the name of an existing file; otherwise, 
it will return false.

This method also returns false if the Path is null, an Invalid Path, or a Zero-Length string. If the caller has 
insufficient permissions to read the specified file, no exception is thrown, and the method returns false 
regardless of the path’s existence.

```C#
using System;
using System.IO;

namespace FileClass
{
    internal class FileClass
    {
        static void Main(string[] args)
        {
            string filePath = @"C:\Users\otwom\Desktop\example\MyFile.txt";
            string wrongFilePath = @"C:\Users\otwom\Desktop\example\MyFile.tx";
            string wrongFilePath2 = @"C:\Users\otwom\Desktop\wrong\path\MyFile.txt";

            Console.WriteLine(File.Exists(filePath)); // True
            Console.WriteLine(File.Exists(wrongFilePath)); // False
            Console.WriteLine(File.Exists(wrongFilePath2)); // False
        }
    }
}
```

## ReadAllLines Method
The ReadAllLines Static Method of File Class in C# is used to open a file, read all the lines one by one from the 
file, and then close the file.

The lines are stored in a string array variable.

```C#
using System;
using System.IO;

namespace FileClass
{
    internal class FileClass
    {
        static void Main(string[] args)
        {
            string filePath = @"C:\Users\otwom\Desktop\example\MyFile.txt";
            string[] lines = File.ReadAllLines(filePath);
            foreach (string line in lines)
            {
                Console.WriteLine(line);
            }
        }
    }
}
```

## ReadAllText Method
The ReadAllText Method of File Class in C# is used to open a text file, read all the text in the file, and then
close the file. In this case, it will read all the text from the file simultaneously. The text is then stored 
in a string variable.

```C#
using System;
using System.IO;

namespace FileClass
{
    internal class FileClass
    {
        static void Main(string[] args)
        {
            string filePath = @"C:\Users\otwom\Desktop\example\MyFile.txt";

            string text = File.ReadAllText(filePath);
            Console.WriteLine(text);
        }
    }
}
```

## Copy Method
The static Copy Method of File Class in C# is used to make a copy of an existing file.

The most important point you need to remember is that overwriting a file of the same name is not allowed when
using the Copy method of the File class, you need to give a different name for the destination file. 

The Copy method takes two 
parameters. The first parameter is the sourceFileName, i.e., the file to copy, and the second parameter is 
the destFileName, i.e., the name of the destination file, and the destination file cannot be a directory or 
an existing file.

```C#
using System;
using System.IO;

namespace FileClass
{
    internal class FileClass
    {
        static void Main(string[] args)
        {
            string filePath = @"C:\Users\otwom\Desktop\example\MyFile.txt";
            string destPath = @"C:\Users\otwom\Desktop\example\MyFile-Copy.txt";

            File.Copy(filePath, destPath );
        }
    }
}
```

## Delete Method
The static Delete method of the File Class in C# is used to delete an existing file. The Delete method takes one 
parameter, which is the path of the file to be deleted.

```C#
using System;
using System.IO;

namespace FileClass
{
    internal class FileClass
    {
        static void Main(string[] args)
        {
            string filePath = @"C:\Users\otwom\Desktop\example\MyFile.txt";

            File.Delete(filePath);
        }
    }
}
```