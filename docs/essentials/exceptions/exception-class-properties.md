# Exception Class and Properties

The [Exception](https://msdn.microsoft.com/library/system.exception) class is the base class from which exceptions inherit. Exception objects are instances of **Exception** or some derived class of **Exception**.

The **Exception** class has several properties that make understanding an exception easier. These properties include:

- The [StackTrace](https://msdn.microsoft.com/library/system.exception.stacktrace) property.

  This property contains a stack trace that can be used to determine where an error occurred. The stack trace includes the source file name and program line number if debugging information is available.

- The [InnerException](https://msdn.microsoft.com/library/system.exception.innerexception) property.

  This property can be used to create and preserve a series of exceptions during exception handling. You can use this property to create a new exception that contains previously caught exceptions. The original exception can be captured by the second exception in the **InnerException** property, allowing code that handles the second exception to examine the additional information.

  For example, suppose you have a method that reads a file and formats the data. The code tries to read from the file, but a FileException is thrown. The method catches the FileException and throws a BadFormatException. In this case, the FileException can be saved in the **InnerException** property of the BadFormatException.

  To improve the caller's ability to determine the reason an exception is thrown, it is sometimes desirable for a method to catch an exception thrown by a helper routine and then throw an exception more indicative of the error that has occurred. A new and more meaningful exception can be created, where the inner exception reference can be set to the original exception. This more meaningful exception can then be thrown to the caller. Note that with this functionality, you can create a series of linked exceptions that ends with the exception that was thrown first.

- The [Message](https://msdn.microsoft.com/library/system.exception.message) property.

  This property provides details about the cause of an exception.

- The [HelpLink](https://msdn.microsoft.com/library/system.exception.helplink) property.

  This property can hold a URL to a help file that provides extensive information about the cause of an exception.

- The [Data](https://msdn.microsoft.com/library/system.exception.data) property

  This property is an IDictionary that can hold arbitrary data in key-value pairs.

Most of the classes that inherit from **Exception** do not implement additional members or provide additional functionality; they simply inherit from **Exception**. Therefore, the most important information for an exception can be found in the hierarchy of exceptions, the exception name, and the information contained in the exception.
