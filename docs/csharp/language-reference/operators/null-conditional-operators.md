---
title: "Null-conditional Operators (C# Reference)"
ms.date: 04/03/2015
helpviewer_keywords: 
  - "null-conditional operators [C#]"
  - "?. operator [C#]"
  - "?[] operator [C#]"
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
---
# ?. and ?[] null-conditional Operators (C# and Visual Basic)
Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`. 

These operators help you write less code to handle null checks, especially for descending into data structures.  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
 The null-conditional operators are short-circuiting.  If one operation in a chain of conditional member access and index operations returns null, the rest of the chain’s execution stops.  In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

 Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.  The old way requires code like the following:  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
  
 The new way is much simpler:  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

 The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable. You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.  
  
## Language Specifications  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## See Also

- [?? (null-coalescing operator)](null-coalescing-operator.md)  
- [C# Reference](../../../csharp/language-reference/index.md)  
- [C# Programming Guide](../../../csharp/programming-guide/index.md)  
