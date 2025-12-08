# FileStream Class

The FileStream Class in C# provides a stream for file operations. It can be used to perform both 
Synchronous and Asynchronous Read and Write operations. 

With the help of FileStream Class, we can easily read and write data into files.

## How to Use the FileStream Class
To use FileStream Class in C#, first of all, we need to include the System.IO namespace, and then we need to 
create an instance of the FileStream class either to create a new file or to open an existing file.

If you go to the definition of FileStream class, then you will see that there are many overloaded versions of 
Constructors available as shown in the below image.

![FileStream constructors](file-handling-filestream-constructors.png)

The simplest way to create an instance of FileStream Class is to use the following overloaded version of the 
Constructors:

### public FileStream(string path, FileMode mode)
This Constructor Initializes a new instance of the FileStream class with the specified path and creation mode.

Here:
- **path**: A relative or absolute path for the file
- **mode**: a constant that determines how to open or create a file

### public FileStream(string path, FileMode mode, FileAccess access)
This overloaded version initializes a new instance of the FileStream class with the specified path, creation mode, 
and read/write permission.

Here:
- **path**: a relative or absolute path to the file.
- **mode**: a constant that determines how to open or create the file.
- **access**: Tells FileStream what kind of operations are allowed (read, write, or both).

### public FileStream(string path, FileMode mode, FileAccess access, FileShare share)
This overloaded version Initializes a new instance of the System.IO.FileStream class with the specified path, 
creation mode, read/write permission, and sharing permission.

- **path**: a relative or absolute path to the file.
- **mode**: a constant that determines how to open or create the file.
- **access**: Tells FileStream what kind of operations are allowed (read, write, or both).
- **share**: a constant that specifies what other processes are allowed to do with the file whil it's open.

## FileMode
The FileMode specifies how the operating system should open a file.

If you go to the definition of FileMode, then you will see it is an enum with the following structure:

![FileMode enum](file-handling-filemode-enum.png)

1. **CreateNew**: specifies that the operating system should create a new file, if the file already exists an 
exception is thrown.
2. **Create**: It specifies that the operating system should create a new file like the CreateNew constant. But
in this case, if the file already exists, it will be overwritten instead of throwing an Exception.
3. **Open**; specifies that the operating system should open an existing file. An exception is thrown if the file does
not exist.
4. **OpenOrCreate**: It specifies that the operating system should open a file if it exists; otherwise, a 
new file should be created.
5. **Truncate**: It specifies that the Operating System should open an existing file, when the file is opened, it should
truncated so that its size is zero bytes.
6. **Append**: It opens the file if it exists and then adds the content at the end of the file, or creates a new file.

## FileAccess
It permits file for read, write, or read/write access. If you go to the definition of FileAccess, then you will see 
that it is an Enum with the following structure.

![File Access Enum](file-handling-fileaccess-enum.png)

- **Read** – It gives read access to the file. Data can be read from the file. Combine with Write for 
read/write access.
- **Write** – It gives Write access to the file. Data can be written to the file. Combine with Read for 
read/write access.
- **ReadWrite** – It gives read and writes access to the file. Data can be written to and read from the file.

## FileShare
It contains constants for controlling the kind of access other FileStream objects can have to the same file. For 
example, if one file is accessed by one FileStream object and a second FileStream object wants to access the file 
then what will happen?

That means it opens a file with share permission. If you go to the definition of FileShare, you will see that it is 
an Enum with the following structure:

![File Share Enum](file-handling-fileshare-enum.png)

- **None**: no other process can touch the file until the current process is done.
- **Read**: others can open it to read.
- **Write**: others can open it to write.
- **ReadWrite**: others can open it to read or write.
- **Delete**: others can delete it while it's open.
- **Inheritable**: lets child processes reuse the same handle.

## Example to Understand the FileStream Class
Let us understand how to perform Read and Write Operations on a File using FileStream Class in C# with Examples.

### Creating a file
In the below example, we will create a new file called “MyFile.txt” and saves it on the Disk. And then we will
open this file save some text in it and then close the file.

In the below example, we have done three things:
1. We have set the file path where we want to create the file.
2. We have created an instance of the `FileStream` class by specifying the file path and the file mode as **Create** as
we are going to create a new file.
3. Finally, we close the FileStream object.

```C#
using System;
using System.IO;

namespace FileHandling
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string filePath = @"C:\Users\otwom\Desktop\example\MyFile.txt";

            FileStream fileStream = new FileStream(filePath, FileMode.Create);
            fileStream.Close();
            Console.WriteLine("File successfully created");
        }
    }
}
```

The MyFile.txt file is created.

Now we’ll open this file and write some text to it. 

### Writing Into a File
In the example below:
- `string filePath = @"C:\Users\otwom\Desktop\example\MyFile.txt";`: Stores the full path of the file we want to
write to.
- `FileStream fileStream = new FileStream(filePath, FileMode.Append);`: Opens the file using `FileMode.Append`, 
meaning data will always be written at the end of the file. If the file doesn’t exist, it will be created.
- `byte[] bytedata = Encoding.Default.GetBytes("C# is an object oriented programming language");`: Converts the text 
string into a sequence of bytes using the system’s default encoding and stores it in a byte array. **computer don't
store text directly, they store bytes, this line simply turns the text into bytes so it can be written to the file**
- `fileStream.Write(bytedata, 0, bytedata.Length);`: Writes the entire byte array to the file, starting at 
index 0 and writing all bytes up to the array’s length.
- `fileStream.Close();`: Closes the stream so the file is no longer locked and resources are released.

```C#
using System;
using System.IO;
using System.Text;

namespace FileHandling
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string filePath = @"C:\Users\otwom\Desktop\example\MyFile.txt";
            FileStream fileStream = new FileStream (filePath, FileMode.Append);
            byte[] bytedata = Encoding.Default.GetBytes("C# is an object oriented programming language");
            fileStream.Write(bytedata, 0, bytedata.Length);
            fileStream.Close();
            Console.WriteLine("Successfully saved data into file");
        }
    }
}
```

### Reading From a File
We have already created one MyFile.txt, and we have also written some data into it. Now, we will see, how to
read the data from the MyFile.txt file. In the below example:
- `string filePath = @"C:\Users\otwom\Desktop\example\MyFile.txt";`: holds the full path to the file you want to read
from.
- `string data;`: declares a variable that will eventually store the text you read from the file.

```C#
using (StreamReader sr = new StreamReader(filePath))
{
    data = sr.ReadToEnd();
}
```

- Opens the file for reading using StreamReader.
- Reads all the text from the file and stores it in the data variable.
- Automatically closes the file when the using block ends, ensuring the file is released properly.

<strong>
`using` is a _resource-cleanup block_, Its whole job is to automatically close and clean up something when you’re 
done with it.
Some objects (like StreamReader, FileStream, DB connections, etc.) use system resources that MUST be released.

If you forget to close them manually, the file can stay locked, memory can leak, and things go sideways.

using handles that automatically.
</strong>

```C#
using System;
using System.IO;
using System.Text;

namespace FileHandling
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string filePath = @"C:\Users\otwom\Desktop\example\MyFile.txt";

            // Reading from a file
            string data;
            using(StreamReader sr = new StreamReader(filePath))
            {
               data = sr.ReadToEnd();
            }
            Console.WriteLine(data);
        }
    }
}
```