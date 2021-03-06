---
title: Implementando IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: f40fcf7e0724addc478b261dcd36d09e1d8a751a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333694"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a>Instruções passo a passo: implementando IEnumerable(Of T) no Visual Basic
A interface <xref:System.Collections.Generic.IEnumerable%601> é implementada por classes que podem retornar uma sequência de valores de um item por vez. A vantagem de retornar dados de um item por vez é que você não precisa carregar o conjunto completo de dados na memória para trabalhar com ele. Você só precisa usar memória suficiente para carregar um único item dos dados. As classes que implementam a interface `IEnumerable(T)` podem ser usadas com loops `For Each` ou consultas LINQ.  
  
 Por exemplo, considere um aplicativo que deve ler um arquivo de texto grande e retornar cada linha do arquivo que corresponde a critérios de pesquisa específicos. O aplicativo usa uma consulta LINQ para retornar linhas do arquivo que correspondem aos critérios especificados. Para consultar o conteúdo do arquivo usando uma consulta LINQ, o aplicativo pode carregar o conteúdo do arquivo em uma matriz ou em uma coleção. No entanto, carregar o arquivo inteiro em uma matriz ou coleção consumiria muito mais memória do que o necessário. Em vez disso, a consulta LINQ poderia consultar o conteúdo do arquivo usando uma classe enumerável, retornando apenas os valores que correspondem aos critérios de pesquisa. As consultas que retornam apenas alguns valores correspondentes consumirão muito menos memória.  
  
 Você pode criar uma classe que implementa a interface <xref:System.Collections.Generic.IEnumerable%601> para expor dados de origem como dados enumeráveis. Sua classe que implementa a interface `IEnumerable(T)` exigirá outra classe que implementa a interface <xref:System.Collections.Generic.IEnumerator%601> para iterar pelos dados de origem. Essas duas classes permitem que você retorne itens de dados sequencialmente como um tipo específico.  
  
 Neste tutorial, você criará uma classe que implementa a interface `IEnumerable(Of String)` e uma classe que implementa a interface `IEnumerator(Of String)` para ler um arquivo de texto, uma linha por vez.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a>Criando a classe Enumerable  
  
**Criar o projeto de classe enumerável**

1. No Visual Basic, no menu **arquivo** , aponte para **novo** e clique em **projeto**.

1. Na caixa de diálogo **Novo Projeto**, no painel **Tipos de Projetos**, certifique-se de que **Windows** esteja selecionado. Selecione **Biblioteca de Classes** no painel **Modelos**. Na caixa **Nome**, digite `StreamReaderEnumerable` e clique em **OK**. O novo projeto é exibido.

1. Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo Class1. vb e clique em **renomear**. Renomeie o arquivo como `StreamReaderEnumerable.vb` e pressione ENTER. Renomear o arquivo também renomeará a classe para `StreamReaderEnumerable`. Essa classe implementará a interface `IEnumerable(Of String)`.

1. Clique com o botão direito do mouse no projeto StreamReaderEnumerable, aponte para **Adicionar**e clique em **novo item**. Selecione o modelo de **classe** . Na caixa **nome** , digite `StreamReaderEnumerator.vb` e clique em **OK**.

 A primeira classe neste projeto é a classe enumerável e implementará a interface `IEnumerable(Of String)`. Essa interface genérica implementa a interface <xref:System.Collections.IEnumerable> e garante que os consumidores dessa classe possam acessar valores digitados como `String`.  
  
**Adicione o código para implementar IEnumerable**

1. Abra o arquivo StreamReaderEnumerable. vb.

2. Na linha após `Public Class StreamReaderEnumerable`, digite o seguinte e pressione ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   Visual Basic popula automaticamente a classe com os membros exigidos pela interface `IEnumerable(Of String)`.
  
3. Essa classe enumerável lerá linhas de um arquivo de texto, uma linha por vez. Adicione o código a seguir à classe para expor um construtor público que usa um caminho de arquivo como um parâmetro de entrada.

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. Sua implementação do método <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> da interface de `IEnumerable(Of String)` retornará uma nova instância da classe `StreamReaderEnumerator`. A implementação do método de `GetEnumerator` da interface `IEnumerable` pode ser feita `Private`, pois você precisa expor somente os membros da interface `IEnumerable(Of String)`. Substitua o código que Visual Basic gerado para os métodos `GetEnumerator` com o código a seguir.

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
**Adicione o código para implementar IEnumerator**

1. Abra o arquivo StreamReaderEnumerator. vb.

2. Na linha após `Public Class StreamReaderEnumerator`, digite o seguinte e pressione ENTER.

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   Visual Basic popula automaticamente a classe com os membros exigidos pela interface `IEnumerator(Of String)`.

3. A classe Enumerator abre o arquivo de texto e executa a e/s de arquivo para ler as linhas do arquivo. Adicione o código a seguir à classe para expor um construtor público que usa um caminho de arquivo como um parâmetro de entrada e abra o arquivo de texto para leitura.

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. As propriedades `Current` para as interfaces `IEnumerator(Of String)` e `IEnumerator` retornam o item atual do arquivo de texto como um `String`. A implementação da propriedade `Current` da interface `IEnumerator` pode ser feita `Private`, pois você precisa expor somente os membros da interface `IEnumerator(Of String)`. Substitua o código que Visual Basic gerado para as propriedades de `Current` com o código a seguir.

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. O método `MoveNext` da interface `IEnumerator` navega para o próximo item no arquivo de texto e atualiza o valor retornado pela propriedade `Current`. Se não houver mais itens a serem lidos, o método `MoveNext` retornará `False`; caso contrário, o método `MoveNext` retornará `True`. Adicione o seguinte código ao método de `MoveNext` .

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. O método `Reset` da interface `IEnumerator` direciona o iterador para apontar para o início do arquivo de texto e limpa o valor do item atual. Adicione o seguinte código ao método de `Reset` .

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. O método `Dispose` da interface `IEnumerator` garante que todos os recursos não gerenciados sejam liberados antes que o iterador seja destruído. O identificador de arquivo usado pelo objeto `StreamReader` é um recurso não gerenciado e deve ser fechado antes que a instância do iterador seja destruída. Substitua o código que Visual Basic gerado para o método `Dispose` com o código a seguir.

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)] 
  
## <a name="using-the-sample-iterator"></a>Usando o iterador de exemplo

 Você pode usar uma classe enumerável em seu código junto com estruturas de controle que exigem um objeto que implementa `IEnumerable`, como um loop `For Next` ou uma consulta LINQ. O exemplo a seguir mostra o `StreamReaderEnumerable` em uma consulta LINQ.  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a>Consulte também

- [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Fluxo de Controle](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [Estruturas de Loop](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [Instrução For Each...Next](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
