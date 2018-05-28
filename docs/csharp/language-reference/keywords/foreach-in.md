---
title: "foreach, in (C# Reference)"
ms.date: 05/24/2018
f1_keywords: 
  - "foreach"
  - "foreach_CSharpKeyword"
helpviewer_keywords: 
  - "foreach keyword [C#]"
  - "foreach statement [C#]"
  - "in keyword [C#]"
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
---
# foreach, in (C# Reference)

The `foreach` statement executes a statement or a block of statements for each element in an instance of the type that implements the <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> interface. The `foreach` statement is not limited to those types and can be applied to an instance of any type that satisfies the following conditions:

- has the public parameterless `GetEnumerator` method whose return type is either class, struct, or interface type,
- the return type of the `GetEnumerator` method has the public `Current` property and the public parameterless `MoveNext` method whose return type is <xref:System.Boolean>.

At any point within the `foreach` statement block, you can break out of the loop by using the [break](break.md) keyword, or step to the next iteration in the loop by using the [continue](continue.md) keyword. You also can exit a `foreach` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.

## Examples

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

The following example shows usage of the `foreach` statement with an instance of the <xref:System.Collections.Generic.List%601> type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

The next example uses the `foreach` statement with an instance of the <xref:System.Span%601?displayProperty=nameWithType> type, which doesn't implement any interfaces:

[!code-csharp-interactive[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

## C# Language Specification

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## See also

[The foreach statement (C# language specification)](/dotnet/csharp/language-reference/language-specification/statements#the-foreach-statement)  
[Using foreach with Arrays](../../programming-guide/arrays/using-foreach-with-arrays.md)  
[for](for.md)  
[Iteration Statements](iteration-statements.md)  
[C# Keywords](index.md)  
[C# Reference](../index.md)  
[C# Programming Guide](../../programming-guide/index.md)  