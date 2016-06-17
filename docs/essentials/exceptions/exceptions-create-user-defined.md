# How to create user-defined exceptions

If you want users to be able to programmatically distinguish between some error conditions, you can create your own user-defined exceptions. .NET provides a hierarchy of exception classes ultimately derived from the base class [Exception](https://msdn.microsoft.com/library/system.exception). Each of these classes defines a specific exception, so in many cases you only have to catch the exception. You can also create your own exception classes by deriving from the **Exception** class.

When creating your own exceptions, it is good coding practice to end the class name of the user-defined exception with the word "Exception." It is also good practice to implement the three recommended common constructors, as shown in the following example.

In the following example, a new exception class, `EmployeeListNotFoundException`, is derived from **Exception**. Three constructors are defined in the class, each taking different parameters.

## Example

C#
```
using System;

public class EmployeeListNotFoundException: Exception
{
    public EmployeeListNotFoundException()
    {
    }

    public EmployeeListNotFoundException(string message)
        : base(message)
    {
    }

    public EmployeeListNotFoundException(string message, Exception inner)
        : base(message, inner)
    {
    }
}
```

Visual Basic
```
Imports System

Public Class EmployeeListNotFoundException
    Inherits Exception

    Public Sub New()
    End Sub

    Public Sub New(message As String)
        MyBase.New(message)
    End Sub

    Public Sub New(message As String, inner As Exception)
        MyBase.New(message, inner)
    End Sub
End Class
```
