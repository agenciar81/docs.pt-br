---
title: operador delegate – referência do C#
ms.date: 07/18/2019
helpviewer_keywords:
- delegate [C#]
- anonymous method [C#]
ms.openlocfilehash: 02b0bfaccbd727b1f86a1668012f02b315fd88d1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239294"
---
# <a name="delegate-operator-c-reference"></a>operador delegate (referência do C#)

O operador `delegate` cria um método anônimo que pode ser convertido em um tipo delegado:

[!code-csharp-interactive[anonymous method](~/samples/snippets/csharp/language-reference/operators/DelegateOperator.cs#AnonymousMethod)]

> [!NOTE]
> Começando com C# 3, as expressões lambda fornecem uma maneira mais concisa e expressiva de criar uma função anônima. Use o [operador =>](lambda-operator.md) para construir uma expressão lambda:
>
> [!code-csharp-interactive[lambda expression](~/samples/snippets/csharp/language-reference/operators/DelegateOperator.cs#Lambda)]
>
> Para saber mais sobre recursos de expressões lambda, por exemplo, que capturam variáveis externas, confira [Expressões lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

Você pode omitir a lista de parâmetros quando usa o operador `delegate`. Se você fizer isso, o método anônimo criado poderá ser convertido em um tipo delegado com qualquer lista de parâmetros, como mostra o exemplo a seguir:

[!code-csharp-interactive[no parameter list](~/samples/snippets/csharp/language-reference/operators/DelegateOperator.cs#WithoutParameterList)]

Essa é a única funcionalidade de métodos anônimos que não tem suporte por expressões lambda. Em todos os outros casos, uma expressão lambda é a forma preferida de gravar código embutido.

Você também usa a palavra-chave `delegate` para declarar um [tipo delegado](../builtin-types/reference-types.md#the-delegate-type).

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira a seção [Expressões de função anônima](~/_csharplang/spec/expressions.md#anonymous-function-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [= operador de >](lambda-operator.md)
