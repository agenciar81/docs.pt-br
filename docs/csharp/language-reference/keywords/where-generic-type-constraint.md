---
title: where (restrição de tipo genérico) – Referência de C#
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: d236420c5019f7529b729155b13df50807dc1dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626705"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (restrição de tipo genérico) (Referência de C#)

A cláusula `where` em uma definição genérica especifica restrições sobre os tipos que são usados como argumentos para parâmetros de tipo em um tipo genérico, método, delegado ou função local. As restrições podem especificar interfaces, classes básicas ou exigir que um tipo genérico seja um tipo de referência, valor ou não gerenciado. Elas declaram funcionalidades que o argumento de tipo deve ter.

Por exemplo, você pode declarar uma classe genérica, `MyGenericClass`, de modo que o parâmetro de tipo `T` implementa a interface <xref:System.IComparable%601>:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> Para obter mais informações sobre a cláusula where em uma expressão de consulta, consulte [Cláusula where](where-clause.md).

A cláusula `where` também pode incluir uma restrição de classe base. A restrição de classe base declara que um tipo a ser usado como um argumento de tipo para aquele tipo genérico tem a classe especificada como uma classe base (ou é que a classe base) a ser usada como um argumento de tipo para aquele tipo genérico. Se a restrição de classe base for usada, ela deverá aparecer antes de qualquer outra restrição nesse parâmetro de tipo. Alguns tipos não têm permissão como uma restrição de classe base: <xref:System.Object>, <xref:System.Array> e <xref:System.ValueType>. Antes do C# 7.3, <xref:System.Enum>, <xref:System.Delegate> e <xref:System.MulticastDelegate> também não tinham permissão como restrições de classe base. O exemplo a seguir mostra os tipos que agora podem ser especificados como classe base:

[!code-csharp[using an interface constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

A cláusula `where` pode especificar que o tipo é um `class` ou um `struct`. A restrição `struct` elimina a necessidade de especificar uma restrição de classe base de `System.ValueType`. O tipo `System.ValueType` não pode ser usado como uma restrição de classe base. O exemplo a seguir mostra as restrições `class` e `struct`:

[!code-csharp[using the class and struct constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

A `where` cláusula pode `notnull` incluir a restrição. A `notnull` restrição limita o parâmetro de tipo a tipos não anulados. Esse tipo pode ser um [tipo de valor](../builtin-types/value-types.md) ou um tipo de referência não anulado. A `notnull` restrição está disponível a partir de C# [ `nullable enable` ](../../nullable-references.md#nullable-contexts)8.0 para código compilado em um contexto . Ao contrário de outras restrições, se um argumento de tipo violar a `notnull` restrição, o compilador gera um aviso em vez de um erro. Os avisos só `nullable enable` são gerados em um contexto.

> [!IMPORTANT]
> Declarações genéricas `notnull` que incluem a restrição podem ser usadas em um contexto alheio nulo, mas o compilador não impõe a restrição.

[!code-csharp[using the nonnull constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#NotNull)]

A cláusula `where` também pode incluir uma restrição `unmanaged`. A restrição `unmanaged` limita o parâmetro de tipo a tipos conhecidos como [tipos não gerenciados](../builtin-types/unmanaged-types.md). Usando a restrição `unmanaged`, é mais fácil escrever o código de interoperabilidade de nível baixo em C#. Essa restrição habilita rotinas reutilizáveis em todos os tipos não gerenciados. A restrição `unmanaged` não pode ser combinada à restrição `class` ou `struct`. A restrição `unmanaged` impõe que o tipo deve ser um `struct`:

[!code-csharp[using the unmanaged constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

A cláusula `where` também pode incluir uma restrição de construtor, `new()`. Essa restrição torna possível criar uma instância de um parâmetro de tipo usando o operador `new`. A [nova () Restrição](new-constraint.md) permite ao compilador saber que qualquer argumento de tipo fornecido deve ter um construtor sem parâmetros acessível. Por exemplo: 

[!code-csharp[using the new constraint](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

A restrição `new()` aparece por último na cláusula `where`. A restrição `new()` não pode ser combinada às restrições `struct` ou `unmanaged`. Todos os tipos que satisfazem as restrições devem ter um construtor sem parâmetros acessível, tornando a restrição `new()` redundante.

Com vários parâmetros de tipo, use uma cláusula `where` para cada parâmetro de tipo, por exemplo:

[!code-csharp[using multiple where constraints](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

Você também pode anexar restrições a parâmetros de tipo de métodos genéricos, como mostrado no exemplo a seguir:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

Observe que a sintaxe para descrever as restrições de parâmetro de tipo em delegados é a mesma que a dos métodos:

[!code-csharp[where constraints with generic methods](~/samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

Para obter informações sobre delegados genéricos, consulte [Delegados genéricos](../../programming-guide/generics/generic-delegates.md).

Para obter detalhes sobre a sintaxe e o uso de restrições, consulte [Restrições a parâmetros de tipo](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [Introdução aos genéricos](../../programming-guide/generics/index.md)
- [nova Restrição](./new-constraint.md)
- [Restrições a parâmetros de tipo](../../programming-guide/generics/constraints-on-type-parameters.md)
