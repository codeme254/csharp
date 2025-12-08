# File Handling

## What is a File
A file is a collection of data stored on a disk with a specific name, extension, and directory path.

When you open File using C# for reading and writing purposes it becomes **Stream**.

## What is a Stream
A stream is a sequence of bytes travelling from a source to a destination over a communication path.

There are two main streams: the **Input Stream** and the **Output Stream**. The input stream is used for 
reading data from the file (read operation) and the output stream is used for writing into the file (write operation).

- **Input Stream**: This Stream is used to read data from a file, which is known as a read operation.
- **Output Stream**: This Stream is used to write data into a file, which is known as a write operation.

## Why We Need to Learn File Handling
As a C# Programmer, we need to save information on a disk. We will not get a database everywhere to save the 
information and our project may require saving information in a TEXT file, DOC file, XLS file, PDF file, or any 
other file type. So, we must know the concept of saving data in a file i.e. How to Handle Files in C#.

## File Handling in C#
The term File Handling in C# refers to the various operations that we can perform on a file such as creating a file,
reading data from the file, writing data into the file, appending the file, etc.

Generally, we mostly perform three basic operations on a file: reading data from a file, writing data to a 
file and appending data to a file.
- **Reading**: This operation is the basic read operation where the data is going to be read from a file.
- **Writing**: This operation is the basic write operation where the data is going to be written to a file. By
default, all existing contents are removed from the file, and new content is written in the file.
- **Appending**: This operation is the same as the write operation where the data is going to be written to a file. 
The only difference between Write and Append is that the existing data in the file will not be overwritten. With 
Append, the new data is going to be added at the end of the file.

<note>
A file becomes a stream when we open the file either for writing or for reading.
</note>

## System.IO Namespace
In C#, The System.IO namespace contains the required classes used to handle the input and output streams and
provide information about file and directory structure.

The parent class of file processing is a class called **Stream**.

The following table describes commonly used classes in the System.IO namespace.

![Most used classes in System.IO namespace](file-handling-most-used-classes.png)
