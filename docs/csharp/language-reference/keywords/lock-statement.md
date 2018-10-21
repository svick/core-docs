---
title: "lock statement (C# Reference)"
description: "Use the C# lock statement to synchronize thread access to a shared resource"
ms.date: 10/01/2018
f1_keywords: 
  - "lock_CSharpKeyword"
  - "lock"
helpviewer_keywords: 
  - "lock keyword [C#]"
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
---
# lock statement (C# Reference)

The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock. While a lock is held, the thread that holds the lock can again acquire and release the lock. Any other thread is blocked from acquiring the lock and waits until the lock is released.

The `lock` statement is of the form

```csharp
lock (x)
{
    // Your code...
}
```

where `x` is an expression of a [reference type](reference-types.md). It's precisely equivalent to

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.

You can't use the [await](await.md) keyword in the body of a `lock` statement.

## Remarks

When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code. Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention. In particular, avoid using the following as lock objects:

- `this`, as it might be used by the callers as a lock.
- <xref:System.Type> instances, as those might be obtained by the [typeof](typeof.md) operator or reflection.
- string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).

## Example

The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance. Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## C# language specification

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## See also

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [C# Reference](../index.md)
- [C# Keywords](index.md)
- [Statement Keywords](statement-keywords.md)
- [Interlocked operations](../../../standard/threading/interlocked-operations.md)
- [Overview of synchronization primitives](../../../standard/threading/overview-of-synchronization-primitives.md)