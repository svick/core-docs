# Using user-filtered exception handlers

User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception. These handlers use the **Catch** statement with the **When** keyword.

This technique is useful when a particular exception object corresponds to multiple errors. In this case, the object typically has a property that contains the specific error code associated with the error. You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.

The following example illustrates the **Catch/When** statement.

## Example


C#
```c#
try
{
    // try statements
}
catch when (Err == VBErr_ClassLoadException)
{
    // catch statements
}
```

Visual Basic
```
Try
    'Try statements.
Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try
```

The expression of the user-filtered clause is not restricted in any way. If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false. In this case, the Common Language Runtime continues the search for a handler for the current exception.

## Combining the specific exception and the user-filtered clauses

A **Catch** statement can contain both the specific exception and the user-filtered clauses. The runtime tests the specific exception first. If the specific exception succeeds, the runtime executes the user filter. The generic filter can contain a reference to the variable declared in the class filter. Note that the order of the two filter clauses cannot be reversed.

The following example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.

### Example

C#

```c#
try
{
    // try statements
}
catch (ClassLoadException cle) when cle.IsRecoverable()
{
    // catch statements
}
```

Visual Basic

```
Try
    'Try statements.
Catch cle As ClassLoadException When cle.IsRecoverable()
    'Catch statements.
End Try
```
