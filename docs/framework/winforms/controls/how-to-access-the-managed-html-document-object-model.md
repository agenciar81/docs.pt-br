---
title: 'Como: Acessar o Modelo de Objeto do Documento HTML gerenciado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- HTML DOM [Windows Forms], accessing
- managed HTML DOM [Windows Forms], accessing
ms.assetid: 40fa5cd5-1ed8-42f6-a93f-9ac01608bbeb
ms.openlocfilehash: 2a195dc6583d5a0a72bd08b66f8933f4002e879a
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487270"
---
# <a name="how-to-access-the-managed-html-document-object-model"></a>Como: Acessar o Modelo de Objeto do Documento HTML gerenciado
É possível acessar o Document Object Model (DOM) do HTML gerenciado a partir de dois tipos de aplicativos:  
  
- Um aplicativo do Windows Forms (.exe) que hospedou o controle <xref:System.Windows.Forms.WebBrowser> gerenciado. Essas duas tecnologias se complementam entre si, com o controle <xref:System.Windows.Forms.WebBrowser> exibindo a página para o usuário e o DOM do HTML representando a estrutura lógica do documento.  
  
- Um <xref:System.Windows.Forms.UserControl> do Windows Forms hospedado dentro do Internet Explorer. É possível acessar o DOM do HTML que representa a página na qual o <xref:System.Windows.Forms.UserControl> está hospedado para alterar a estrutura do documento ou abrir caixas de diálogo restritas, entre muitas outras possibilidades.  
  
### <a name="to-access-dom-from-a-windows-forms-application"></a>Para acessar o DOM a partir de um aplicativo do Windows Forms  
  
1. Hospede um controle <xref:System.Windows.Forms.WebBrowser> dentro do aplicativo do Windows Forms e monitore pelo evento <xref:System.Windows.Forms.WebBrowser.DocumentCompleted>. Para obter detalhes sobre controles de host e monitoramento de eventos, consulte [Eventos](../../../standard/events/index.md).  
  
2. Recupere o <xref:System.Windows.Forms.HtmlDocument> da página atual acessando a propriedade <xref:System.Windows.Forms.WebBrowser.Document%2A> do controle <xref:System.Windows.Forms.WebBrowser>.  

### <a name="to-access-dom-from-a-usercontrol-hosted-in-internet-explorer"></a>Para acessar o DOM a partir de um UserControl hospedado no Internet Explorer  
  
1. Crie sua própria classe derivada personalizada da classe <xref:System.Windows.Forms.UserControl>. Para obter mais informações, confira [Como: Criar controles de composição](how-to-author-composite-controls.md).  
  
2. Coloque o seguinte código dentro do manipulador de eventos Carregar do <xref:System.Windows.Forms.UserControl>:  
  
 [!code-csharp[AccessHTMLDOMControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/AccessHTMLDOMControl/cs/UserControl1.cs#1)]
 [!code-vb[AccessHTMLDOMControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/AccessHTMLDOMControl/vb/UserControl1.vb#1)]  
  
## <a name="robust-programming"></a>Programação robusta  
  
1. Ao usar o DOM através do controle <xref:System.Windows.Forms.WebBrowser>, é sempre necessário esperar até o evento <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> ocorrer antes de tentar acessar a propriedade <xref:System.Windows.Forms.WebBrowser.Document%2A> do controle <xref:System.Windows.Forms.WebBrowser>. O evento <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> é elevado após o documento inteiro ser carregado, se o DOM for usado antes disso, haverá o risco de causar uma exceção de tempo de execução no aplicativo.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
  
1. O aplicativo ou o <xref:System.Windows.Forms.UserControl> exigirá confiança total para acessar o DOM do HTML gerenciado. Se você estiver implantando um aplicativo do Windows Forms usando o ClickOnce, você pode solicitar confiança total usando implantação de aplicativos confiáveis; ou elevação de permissões ver [Protegendo aplicativos ClickOnce](/visualstudio/deployment/securing-clickonce-applications) para obter detalhes.  
  
## <a name="see-also"></a>Consulte também

- [Usando o Modelo de Objeto do Documento HTML gerenciado](using-the-managed-html-document-object-model.md)
