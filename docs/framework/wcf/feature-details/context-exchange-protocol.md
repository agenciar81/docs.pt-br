---
title: Protocolo de intercâmbio de contexto
ms.date: 03/30/2017
ms.assetid: 3dfd38e0-ae52-491c-94f4-7a862b9843d4
ms.openlocfilehash: 19780cccc74f8c3615dc844e47be7613ca5f8bc1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911199"
---
# <a name="context-exchange-protocol"></a>Protocolo de intercâmbio de contexto
Esta seção descreve o protocolo de troca de contexto apresentado na versão Windows Communication Foundation (WCF) .NET Framework versão 3,5. Esse protocolo permite que o canal do cliente aceite um contexto fornecido por um serviço e aplique-o a todas as solicitações subsequentes para esse serviço enviado pela mesma instância de canal do cliente. A implementação do protocolo de troca de contexto pode usar um dos dois mecanismos a seguir para propagar o contexto entre o servidor e o cliente: Cookies HTTP ou um cabeçalho SOAP.  
  
 O protocolo de troca de contexto é implementado em uma camada de canal personalizada. O canal comunica o contexto de e para a camada de aplicativo usando uma <xref:System.ServiceModel.Channels.ContextMessageProperty> propriedade. Para a transmissão entre os pontos de extremidade, o valor do contexto é serializado como um cabeçalho SOAP na camada de canal, ou convertido de ou para as propriedades de mensagem que representam uma solicitação e resposta HTTP. No último caso, espera-se que uma das camadas de canal subjacentes converta as propriedades da solicitação HTTP e da mensagem de resposta de e para cookies HTTP, respectivamente. A escolha do mecanismo usado para trocar o contexto é feita usando a <xref:System.ServiceModel.Channels.ContextExchangeMechanism> propriedade <xref:System.ServiceModel.Channels.ContextBindingElement>no. Os valores válidos `HttpCookie` são `SoapHeader`ou.  
  
 No cliente, uma instância de um canal pode operar em dois modos com base nas configurações na Propriedade do canal, <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A>.  
  
## <a name="mode-1-channel-context-management"></a>Modo 1: Gerenciamento de contexto do canal  
 Esse é o modo padrão em <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> que é definido `true`como. Nesse modo, o canal de contexto gerencia o contexto e armazena em cache o contexto durante seu tempo de vida. O contexto pode ser recuperado do canal por meio da `IContextManager` Propriedade Channel chamando `GetContext` o método. O canal também pode ser inicializado previamente com contexto específico antes de ser aberto chamando o `SetContext` método na propriedade Channel. Depois que o canal é inicializado com o contexto, ele não pode ser redefinido.  
  
 A seguir está uma lista de invariáveis neste modo:  
  
- Qualquer tentativa de redefinir o contexto usando `SetContext` depois que o canal é aberto gera um <xref:System.InvalidOperationException>.  
  
- Qualquer tentativa de enviar o contexto usando o <xref:System.ServiceModel.Channels.ContextMessageProperty> em uma mensagem de saída gera um <xref:System.InvalidOperationException>.  
  
- Se uma mensagem for recebida do servidor com um contexto específico, quando o canal já tiver sido inicializado com um contexto específico, isso resultará <xref:System.ServiceModel.ProtocolException>em um.  
  
    > [!NOTE]
    > É apropriado receber um contexto inicial do servidor somente se o canal for aberto sem qualquer contexto definido explicitamente.  
  
- O <xref:System.ServiceModel.Channels.ContextMessageProperty> na mensagem de entrada é sempre nulo.  
  
## <a name="mode-2-application-context-management"></a>Modo 2: Gerenciamento de contexto de aplicativo  
 Esse é o modo quando <xref:System.ServiceModel.Channels.IContextManager.Enabled%2A> é definido como `false`. Nesse modo, o canal de contexto não gerencia o contexto. É responsabilidade do aplicativo recuperar, gerenciar e aplicar o contexto usando o <xref:System.ServiceModel.Channels.ContextMessageProperty>. Qualquer tentativa de chamar `GetContext` ou `SetContext` resultar em um <xref:System.InvalidOperationException>.  
  
 Não importa qual modo é escolhido, a fábrica de canais <xref:System.ServiceModel.Channels.IRequestChannel>do <xref:System.ServiceModel.Channels.IRequestSessionChannel>cliente dá <xref:System.ServiceModel.Channels.IDuplexSessionChannel> suporte a, e a padrões de troca de mensagens.  
  
 No serviço, uma instância do canal é responsável por converter o contexto fornecido pelo cliente em mensagens de entrada para o <xref:System.ServiceModel.Channels.ContextMessageProperty>. A propriedade Message pode ser acessada pela camada do aplicativo ou outros canais mais adiante na pilha de chamadas. Os canais de serviço também permitem que a camada de aplicativo especifique um novo valor de contexto a ser propagado de volta para <xref:System.ServiceModel.Channels.ContextMessageProperty> o cliente, anexando um à mensagem de resposta. Essa propriedade é convertida no cabeçalho SOAP ou no cookie HTTP que contém o contexto, que depende da configuração da associação. O ouvinte do canal <xref:System.ServiceModel.Channels.IReplyChannel>de <xref:System.ServiceModel.Channels.IReplySessionChannel>serviço dá <xref:System.ServiceModel.Channels.IReplySessionChannel> suporte aos padrões de troca de mensagens, e.  
  
 O protocolo de troca de contexto introduz `wsc:Context` um novo cabeçalho SOAP para representar as informações de contexto quando os cookies http não são usados para propagar o contexto. O esquema de cabeçalho de contexto permite qualquer número de elementos filho, cada um com uma chave de cadeia de caracteres e um conteúdo de cadeia de caracteres. Veja a seguir um exemplo de um cabeçalho de contexto.  
  
 `<Context xmlns="http://schemas.microsoft.com/ws/2006/05/context">`  
  
 `<property name="myContext">context-2</property>`  
  
 `</Context>`  
  
 Quando estiver `HttpCookie` no modo, os cookies são definidos `SetCookie` usando o cabeçalho. O nome do cookie `WscContext`é. O valor do cookie é a codificação base64 do `wsc:Context` cabeçalho. Esse valor é colocado entre aspas.  
  
 O valor do contexto deve ser protegido contra modificação enquanto estiver em trânsito pelo mesmo motivo pelo qual os cabeçalhos de WS-Addressing são protegidos – o cabeçalho é usado para determinar para onde distribuir a solicitação no serviço. Portanto `wsc:Context` , o cabeçalho deve ser assinado digitalmente ou assinado e criptografado no nível de transporte ou SOAP quando a associação oferece a capacidade de proteção de mensagem. Quando os cookies HTTP são usados para propagar o contexto, eles devem ser protegidos usando a segurança de transporte.  
  
 Os pontos de extremidade de serviço que exigem suporte para o protocolo de troca de contexto podem torná-lo explícito na política publicada. Duas novas declarações de política foram introduzidas para representar o requisito para o cliente dar suporte ao protocolo de troca de contexto no nível SOAP ou para habilitar o suporte a cookie HTTP. A geração dessas asserções na política no serviço é controlada pelo valor da <xref:System.ServiceModel.Channels.ContextBindingElement.ContextExchangeMechanism%2A> propriedade da seguinte maneira:  
  
- Para <xref:System.ServiceModel.Channels.ContextExchangeMechanism.ContextSoapHeader>, a declaração a seguir é gerada:  
  
    ```xml  
    <IncludeContext   
    xmlns="http://schemas.microsoft.com/ws/2006/05/context"  
    protectionLevel="Sign" />  
    ```  
  
- Para <xref:System.ServiceModel.Channels.ContextExchangeMechanism.HttpCookie>, a declaração a seguir é gerada:  
  
    ```xml  
    <HttpUseCookie xmlns="http://schemas.xmlsoap.org/soap/http"/>  
    ```  
  
## <a name="see-also"></a>Consulte também

- [Guia de interoperabilidade de protocolos de serviços Web](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)
