---
title: 'Como: recuperar metadados através de uma associação não MEX'
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 3721657eb72663450261b4bc8627b250b1a4a14e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856036"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>Como: recuperar metadados através de uma associação não MEX
Este tópico descreve como recuperar metadados de um ponto de extremidade MEX em uma associação não MEX. O código neste exemplo é baseado no exemplo de [ponto de extremidade de metadados seguro personalizado](../samples/custom-secure-metadata-endpoint.md) .  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>Para recuperar metadados em uma associação não-MEX  
  
1. Determine a associação usada pelo ponto de extremidade MEX. Para serviços de Windows Communication Foundation (WCF), você pode determinar a associação MEX acessando o arquivo de configuração do serviço. Nesse caso, a associação MEX é definida na configuração de serviço a seguir.  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2. No arquivo de configuração do cliente, configure a mesma associação personalizada. Aqui, o cliente também define `clientCredentials` um comportamento para fornecer um certificado a ser usado para autenticar o serviço ao solicitar metadados do ponto de extremidade MEX. Ao usar svcutil. exe para solicitar metadados em uma associação personalizada, você deve adicionar a configuração do ponto de extremidade MEX ao arquivo de configuração para SvcUtil. exe (svcutil. exe. config) e o nome da configuração do ponto de extremidade deve corresponder ao esquema de URI do endereço de o ponto de extremidade MEX, conforme mostrado no código a seguir.  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>    
    </system.serviceModel>  
    ```  
  
3. Crie uma `MetadataExchangeClient` chamada `GetMetadata`e. Há duas maneiras de fazer isso: você pode especificar a associação personalizada na configuração ou pode especificar a associação personalizada no código, conforme mostrado no exemplo a seguir.  
  
    ```csharp
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. Crie um `WsdlImporter` e chame `ImportAllEndpoints`, conforme mostrado no código a seguir.  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. Neste ponto, você tem uma coleção de pontos de extremidade de serviço. Para obter mais informações sobre como importar metadados [, consulte Como: Importe metadados em pontos de extremidade](../feature-details/how-to-import-metadata-into-service-endpoints.md)de serviço.  
  
## <a name="see-also"></a>Consulte também

- [Metadados](../feature-details/metadata.md)
