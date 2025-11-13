# Events, Delegates and Lambda Expressions

## What is an event
An event in C# is like a "notification system", it's a way for one part of your program (the broadcaster) to notify
other parts of the program (the listeners/subscribers) when something happens.

In other words, an event is a mechanism that allows a class to notify other classes or objects when something happens.

An example of an event would be something like: "file has finished downloading", "button has been clicked", "user has
successfully registered"

We will talk about events in details later.

## What is an Event Handler
These are parts of our program that respond when an event is fired.

- Event: File has finished downloading
    - Event handler: Notify the user (show download complete notification)
    - Event handler: Move the file to the downloads directory/folder
- Event: Button has been clicked
    - Event handler: Navigate to another page
    - Event handler: Change the color of a certain UI component
- Event: User has successfully registered
    - Event handler: Send a welcome email
    - Event handler: Send a welcome message

We will discuss this in details later.

## What are EventArgs
Refers to the data that travels with the event/notification.
- Event: File has finished downloading
    - EventArgs: File name, file path, file size e.t.c.
- Event: Button has been clicked
    - EventArgs: ButtonId, current page, time clicked e.t.c.
- Event: User has successfully registered
    - EventArgs: User id, username, email address, phone number e.t.c.

We will learn more about this later.

## What are Delegates
In C#, a delegate is a type-safe function pointer.

It is a type that can hold a reference to a method with a specific signature and return type.

A delegate is a blueprint for a method as a class is a blueprint for an object.

The only difference is that a delegate defines what a method should look like i.e., return type and parameters 
and not its implementation.

Delegates can be used to define the shape/signature of the event handler, meaning:
- What parameters it must take
- What return type it must have

We will learn more about delegates later, for now, consider the following examples:

### Event: File has finished downloading
This is what the delegate would look like:
```C#
public delegate void FileDownloadedHandler(string fileName, string filePath, double fileSize);
```
Since delegates define the signature of event handlers, example event handlers could look like this:

```C#
void ShowDownloadNotification(string fileName, string filePath, double fileSize)
{
    Console.WriteLine($"File '{fileName}' downloaded ({fileSize} MB).");
}

void MoveFileToDownloadsFolder(string fileName, string filePath, double fileSize)
{
    Console.WriteLine($"Moving '{fileName}' from {filePath} to Downloads folder...");
}
```

### Event: Button has been clicked
This is what an example delegate for this event would look like:
```C#
public delegate void ButtonClickedHandler(string buttonId, DateTime clickedAt);
```
Since delegates define the signature of event handlers, example event handlers could look like this:
```C#
void NavigateToDashboard(string buttonId, DateTime clickedAt)
{
    Console.WriteLine($"[{clickedAt}] Button '{buttonId}' clicked — navigating to dashboard...");
}

void ChangeButtonColor(string buttonId, DateTime clickedAt)
{
    Console.WriteLine($"[{clickedAt}] Changing color of '{buttonId}' button...");
}
```

### Event: User has successfully registered
This is what an example delegate for this event would look like:
```C#
public delegate void UserRegisteredHandler(string userName, string email, string phoneNumber);
```
Since delegates define the signature of event handlers, example event handlers could look like this:
```C#
void SendWelcomeEmail(string userName, string email, string phoneNumber)
{
    Console.WriteLine($"Welcome {userName}! Email sent to {email}.");
}

void SendWelcomeSms(string userName, string email, string phoneNumber)
{
    Console.WriteLine($"Welcome {userName}! Text sent to {phoneNumber}.");
}
```