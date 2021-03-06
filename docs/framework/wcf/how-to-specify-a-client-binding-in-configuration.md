---
title: Como especificar uma associação de cliente em configuração
ms.date: 03/30/2017
ms.assetid: 4a7c79aa-50ee-4991-891e-adc0599323a7
ms.openlocfilehash: b16f4b062f7f97a5855b06bdcf348911ee0497d2
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320858"
---
# <a name="how-to-specify-a-client-binding-in-configuration"></a>Como especificar uma associação de cliente em configuração
Neste exemplo, um aplicativo de console do cliente é criado para usar um serviço de calculadora e a associação para esse cliente é especificada declarativamente na configuração. O cliente acessa o `CalculatorService`, que implementa a interface `ICalculator`, e o serviço e o cliente usam a classe <xref:System.ServiceModel.BasicHttpBinding>.  
  
 O procedimento descrito pressupõe que o serviço de calculadora está em execução. Para obter informações sobre como criar o serviço, consulte [como especificar uma associação de serviço na configuração](how-to-specify-a-service-binding-in-configuration.md). Ele também usa a [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) que o Windows Communication Foundation (WCF) fornece para gerar automaticamente os componentes do cliente. A ferramenta gera o código do cliente e a configuração para acessar o serviço.  
  
 O cliente é criado em duas partes. Svcutil. exe gera o `ClientCalculator` que implementa a interface `ICalculator`. Esse aplicativo cliente é então construído pela construção de uma instância do `ClientCalculator`.  
  
 Geralmente, é a prática recomendada especificar a associação e as informações de endereço de forma declarativa na configuração, em vez de imperativa no código. A definição de pontos de extremidade no código geralmente não é prática porque as associações e os endereços para um serviço implantado são normalmente diferentes daqueles usados enquanto o serviço está sendo desenvolvido. Em geral, manter as informações de vinculação e endereçamento do código permite que elas sejam alteradas sem a necessidade de recompilar ou reimplantar o aplicativo.  
  
 Você pode executar todas as etapas de configuração a seguir usando a [ferramenta do editor de configuração (SvcConfigEditor. exe)](configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Para a cópia de origem deste exemplo, consulte o exemplo de [BasicBinding](./samples/basicbinding.md) .  
  
### <a name="specifying-a-client-binding-in-configuration"></a>Especificando uma associação de cliente na configuração  
  
1. Use svcutil. exe da linha de comando para gerar código de metadados de serviço.  
  
    ```console  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2. O cliente gerado contém a interface `ICalculator` que define o contrato de serviço que a implementação do cliente deve satisfazer.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#1)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#1)]  
  
3. O cliente gerado também contém a implementação do `ClientCalculator`.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/generatedclient.cs#2)]
     [!code-csharp[C_HowTo_ConfigureClientBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/source.cs#2)]  
  
4. Svcutil. exe também gera a configuração para o cliente que usa a classe <xref:System.ServiceModel.BasicHttpBinding>. Ao usar o Visual Studio, nomeie esse arquivo app. config. Observe que as informações de endereço e de associação não são especificadas em nenhum lugar dentro da implementação do serviço. Além disso, o código não precisa ser escrito para recuperar essas informações do arquivo de configuração.  
  
     [!code-xml[C_HowTo_ConfigureClientBinding#100](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/common/client.exe.config#100)]   
            
5. Crie uma instância do `ClientCalculator` em um aplicativo e, em seguida, chame as operações de serviço.  
  
     [!code-csharp[C_HowTo_ConfigureClientBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_configureclientbinding/cs/client.cs#3)]  
  
6. Compile e execute o cliente.  
  
## <a name="see-also"></a>Consulte também

- [Usando associações para configurar serviços e clientes](using-bindings-to-configure-services-and-clients.md)
