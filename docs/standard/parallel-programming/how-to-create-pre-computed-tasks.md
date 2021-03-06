---
title: 'Como: Criar tarefas pré-computadas'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
ms.openlocfilehash: f5d2a70685fe0401d0219b99ada6936ac04691f2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123132"
---
# <a name="how-to-create-pre-computed-tasks"></a>Como: Criar tarefas pré-computadas
Esse documento descreve como usar o método <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> para recuperar os resultados das operações de download assíncronas armazenados em um cache. O método <xref:System.Threading.Tasks.Task.FromResult%2A> retorna um objeto <xref:System.Threading.Tasks.Task%601> que contém o valor fornecido como sua propriedade <xref:System.Threading.Tasks.Task%601.Result%2A>. Este método é útil quando você executa uma operação assíncrona que retorna um objeto <xref:System.Threading.Tasks.Task%601> e o resultado do objeto <xref:System.Threading.Tasks.Task%601> já está calculado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir faz o download de cadeias de caracteres da Web. Ele define o método `DownloadStringAsync`. Esse método faz o download das cadeias de caracteres da Web de forma assíncrona. Este exemplo também usa um objeto <xref:System.Collections.Concurrent.ConcurrentDictionary%602> para armazenar em cache os resultados de operações anteriores. Se o endereço de entrada for mantido no cache, o `DownloadStringAsync` usará o método <xref:System.Threading.Tasks.Task.FromResult%2A> para produzir um objeto <xref:System.Threading.Tasks.Task%601> que manterá o conteúdo nesse endereço. Caso contrário, o `DownloadStringAsync` baixará o arquivo da Web e adicionará o resultado ao cache.  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 Esse exemplo calcula o tempo necessário para baixar várias cadeias de caracteres duas vezes. O segundo conjunto de operações de download deve levar menos tempo do que o primeiro conjunto porque os resultados são mantidos no cache. O método <xref:System.Threading.Tasks.Task.FromResult%2A> permite que o método `DownloadStringAsync` crie objetos <xref:System.Threading.Tasks.Task%601> que contêm esses resultados pré-computados.  
  
## <a name="see-also"></a>Consulte também

- [Programação assíncrona baseada em tarefa](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
