---
title: Como usar ponteiros para copiar uma matriz de bytes- C# guia de programação
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698450"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Como usar ponteiros para copiar uma matriz de bytes (C# guia de programação)

O exemplo a seguir usa ponteiros para copiar bytes de uma matriz para outra.

Este exemplo usa a palavra-chave [não seguro](../../language-reference/keywords/unsafe.md), que permite que você use ponteiros no método `Copy`. A instrução [fixo](../../language-reference/keywords/fixed-statement.md) é usada para declarar ponteiros para as matrizes de origem e de destino. A instrução `fixed`*fixa* o local das matrizes de origem e de destino na memória para que elas não sejam movidas pela coleta de lixo. Os blocos de memória para as matrizes não serão fixado quando o bloco `fixed` for concluído. Como o método `Copy` neste exemplo usa a palavra-chave `unsafe`, ele precisa ser compilado com a opção do compilador [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).

Este exemplo acessa os elementos das duas matrizes usando índices em vez de um segundo ponteiro não gerenciado. A declaração dos ponteiros `pSource` e `pTarget` fixa as matrizes. Esse recurso está disponível começando com o C# 7.3.

## <a name="example"></a>Exemplo

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
- [Código não seguro e ponteiros](index.md)
- [-unsafe (opções do compilador do C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Coleta de lixo](../../../standard/garbage-collection/index.md)
