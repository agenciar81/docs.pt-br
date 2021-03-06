---
title: Host de serviço do Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: ab1effe93a1572f5d4ce5296bba99dad24f9cbca
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094781"
---
# <a name="windows-service-host"></a>Host de serviço do Windows
Este exemplo demonstra um serviço de Windows Communication Foundation (WCF) hospedado em um serviço gerenciado do Windows. Os serviços do Windows são controlados usando o applet Serviços no **painel de controle** e podem ser configurados para serem iniciados automaticamente após a reinicialização do sistema. O exemplo consiste em um programa cliente e um programa de serviço do Windows. O serviço é implementado como um programa. exe e contém seu próprio código de hospedagem. Em outros ambientes de hospedagem, como WAS (serviços de ativação de processos do Windows) ou Serviços de Informações da Internet (IIS), não é necessário escrever código de hospedagem.

> [!NOTE]
> Os procedimentos de instalação e as instruções de compilação para esse exemplo estão localizadas no final deste tópico.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Depois de criar esse serviço, ele deve ser instalado com o utilitário InstallUtil. exe como qualquer outro serviço do Windows. Se você pretende fazer alterações no serviço, primeiro você deve desinstalá-lo com `installutil /u`. Os arquivos Setup. bat e Cleanup. bat incluídos neste exemplo são os comandos para instalar e iniciar o serviço do Windows e para desligar e desinstalar o serviço do Windows. O serviço WCF só poderá responder a clientes se o serviço do Windows estiver em execução. Se você parar o serviço do Windows usando o applet de serviços do **painel de controle** e executar o cliente, uma exceção <xref:System.ServiceModel.EndpointNotFoundException> ocorrerá quando um cliente tentar acessar o serviço. Se você reiniciar o serviço do Windows e executar novamente o cliente, a comunicação será realizada com sucesso.  
  
 O código de serviço inclui uma classe de instalador, uma classe de implementação de serviço WCF que implementa o contrato ICalculator e uma classe de serviço do Windows que atua como o host de tempo de execução. A classe Installer, que herda de <xref:System.Configuration.Install.Installer>, permite que o programa seja instalado como um serviço NT pela ferramenta InstallUtil. exe. A classe de implementação de serviço, `WcfCalculatorService`, é um serviço WCF que implementa um contrato de serviço básico. Esse serviço WCF é hospedado dentro de uma classe de serviço do Windows chamada `WindowsCalculatorService`. Para se qualificar como um serviço do Windows, a classe herda de <xref:System.ServiceProcess.ServiceBase> e implementa os métodos <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> e <xref:System.ServiceProcess.ServiceBase.OnStop>. No <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, um objeto <xref:System.ServiceModel.ServiceHost> é criado para o tipo de `WcfCalculatorService` e aberto. Em <xref:System.ServiceProcess.ServiceBase.OnStop>, o ServiceHost é fechado chamando o método <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> do objeto <xref:System.ServiceModel.ServiceHost>. O endereço base do host é configurado usando o elemento [\<add >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) , que é um filho de [\<baseaddresss >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), que é um filho do elemento\<do [host](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) >, que é um filho do elemento\<do [serviço](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) >.  
  
 O ponto de extremidade definido usa o endereço base e um [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). O exemplo a seguir mostra a configuração do endereço base, bem como o ponto de extremidade que expõe o CalculatorService.  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 Quando você executa o exemplo, as solicitações e respostas da operação são exibidas nas janelas do console do cliente e do serviço. Pressione ENTER em cada janela do console para desligar o serviço e o cliente.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Depois que a solução tiver sido criada, execute Setup. bat em um prompt de comando do Visual Studio 2012 elevado para instalar o serviço do Windows usando a ferramenta InstallUtil. exe. O serviço deve aparecer em serviços.  
  
4. Para executar o exemplo em uma configuração de computador único ou entre computadores, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Confira também

- [Exemplos de persistência e de hospedagem do AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
