---
title: 'Como: ler caracteres de uma cadeia de caracteres'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
ms.openlocfilehash: ed267ad62e46f6216c94906df1bcefb0684ab51b
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155757"
---
# <a name="how-to-read-characters-from-a-string"></a>Como: ler caracteres de uma cadeia de caracteres
Os exemplos de código a seguir mostram como ler caracteres de forma síncrona ou assíncrona de uma cadeia de caracteres.  
  
## <a name="example-read-characters-synchronously"></a>Exemplo: ler caracteres de forma síncrona
 Este exemplo lê 13 caracteres de forma síncrona de uma cadeia de caracteres, armazena-os em uma matriz e exibe-os. Em seguida, o exemplo lê os caracteres restantes na cadeia de caracteres, armazena-os na matriz começando pelo sexto elemento e exibe o conteúdo da matriz.  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>Exemplo: ler caracteres de forma assíncrona  
 O próximo exemplo é o código por trás de um aplicativo WPF. Na carga de janela, o exemplo lê todos os caracteres de forma assíncrona de um controle <xref:System.Windows.Controls.TextBox> e os armazena em uma matriz. Em seguida, ele grava cada letra ou caractere de espaço em branco de forma assíncrona em uma linha separada de um controle <xref:System.Windows.Controls.TextBlock>.  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>Confira também

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [E/S assíncrona de arquivo](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [Como: criar uma listagem de diretório](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))  
- [Como: ler e gravar em um arquivo de dados recém-criado](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Como: abrir e anexar a um arquivo de log](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [Como: ler texto de um arquivo](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Como: gravar texto em um arquivo](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Como: gravar caracteres em uma cadeia de caracteres](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [E/S de arquivo e de fluxo](../../../docs/standard/io/index.md)
