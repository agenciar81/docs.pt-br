---
title: Serviço de roteador de descoberta
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 09309b23d2a3cc672811c2f617e6fb81a2b4e021
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74712284"
---
# <a name="discovery-router-service"></a>Serviço de roteador de descoberta
Este exemplo demonstra como encaminhar mensagens de descoberta para outro ponto de extremidade.  
  
## <a name="demonstrates"></a>Demonstra  
 Roteamento de descoberta  
  
## <a name="discussion"></a>Discussão  
 O roteamento de descoberta é útil em um cenário no qual um cliente está procurando um serviço usando um proxy e o proxy não está ciente desse serviço, mas sabe de outro proxy. Esse proxy pode encaminhar o pacote de descoberta deste cliente para o segundo proxy. O segundo proxy pode procurar o serviço e retornar as respostas para o cliente original.  
  
 Neste exemplo, um cliente envia uma mensagem para um componente de roteamento de descoberta. Essa mensagem é enviada para um ponto de extremidade específico no roteador de descoberta. Em seguida, o roteador encaminha a mensagem para um ponto de extremidade de multicast UDP. A mensagem de investigação sai para o ponto de extremidade de multicast e um serviço que escuta em um endereço de multicast UDP responde a esse roteador de descoberta. O roteador de descoberta coleta as respostas e as envia de volta para o cliente.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Compile o exemplo.  
  
2. Execute o executável DiscoveryRouter.  
  
3. Execute o executável do serviço no diretório de compilação.  
  
4. Execute o executável do cliente. Observe que o cliente localiza o serviço.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
