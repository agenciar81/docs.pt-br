---
title: Instrução foreach do C#
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: 9c1521f39dea72b51801a81b13e8a0203956731c
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422805"
---
# <a name="foreach-in-c-reference"></a>foreach, in (Referência em C#)

A instrução `foreach` executa uma instrução ou um bloco de instruções para cada elemento em uma instância do tipo que implementa a interface <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. A instrução `foreach` não está limitada a esses tipos e pode ser aplicada a uma instância de qualquer tipo que satisfaça as seguintes condições:

- incluir um método `GetEnumerator` público sem parâmetros, cujo tipo de retorno é um tipo de classe, estrutura ou interface,
- o tipo de retorno do método `GetEnumerator` tem a propriedade `Current` pública e o método `MoveNext` público sem parâmetros, cujo tipo de retorno é <xref:System.Boolean>.

A partir do C# 7.3, se a propriedade `Current` do enumerador retornar um [valor retornado da referência](ref.md#reference-return-values) (`ref T`, em que `T` é o tipo do elemento da coleção), será possível declarar a variável de iteração com o modificador `ref` ou `ref readonly`.

Em qualquer ponto dentro do bloco de instrução `foreach`, você pode sair do loop usando a instrução [break](break.md) ou seguir para a próxima iteração no loop usando a instrução [continue](continue.md). Você também pode sair de um loop `foreach` com a instrução [goto](goto.md), [return](return.md) ou [throw](throw.md).

Se a instrução `foreach` for aplicada a `null`, uma <xref:System.NullReferenceException> será gerada. Se a coleção de origem da instrução `foreach` estiver vazia, o corpo do loop `foreach` não será executado e será ignorado.

## <a name="examples"></a>Exemplos

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

O exemplo a seguir mostra o uso da instrução `foreach` com uma instância do tipo <xref:System.Collections.Generic.List%601> que implementa a interface <xref:System.Collections.Generic.IEnumerable%601>:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

O exemplo a seguir usa a instrução `foreach` com uma instância do tipo <xref:System.Span%601?displayProperty=nameWithType>, que não implementa nenhuma interface:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

O exemplo a seguir usa uma variável de iteração `ref` para definir o valor de cada item em uma matriz stackalloc. A versão `ref readonly` itera a coleção para imprimir todos os valores. A declaração `readonly` usa uma declaração de variável local implícita. Declarações de variável implícita podem ser usadas com declarações `ref` ou `ref readonly`, assim como declarações de variável tipadas explicitamente.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira a seção [A instrução foreach](~/_csharplang/spec/statements.md#the-foreach-statement) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Usar foreach com matrizes](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [instrução for](for.md)
