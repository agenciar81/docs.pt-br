---
title: DiscoveryClient e DynamicEndpoint
ms.date: 03/30/2017
ms.assetid: 7cd418f0-0eab-48d1-a493-7eb907867ec3
ms.openlocfilehash: 455ccc7f09c13a33b4034099b16b116fd3a8dbdf
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895303"
---
# <a name="discoveryclient-and-dynamicendpoint"></a>DiscoveryClient e DynamicEndpoint
<xref:System.ServiceModel.Discovery.DiscoveryClient>e <xref:System.ServiceModel.Discovery.DynamicEndpoint> são duas classes usadas no lado do cliente para procurar serviços. <xref:System.ServiceModel.Discovery.DiscoveryClient>fornece uma lista de serviços que correspondem a um conjunto específico de critérios e permite que você se conecte aos serviços. <xref:System.ServiceModel.Discovery.DynamicEndpoint>executa a mesma operação e, além disso, conecta-se automaticamente a um dos serviços que foi encontrado. Qualquer ponto de extremidade pode ser feito <xref:System.ServiceModel.Discovery.DynamicEndpoint>em um, os critérios de pesquisa também podem ser adicionados na <xref:System.ServiceModel.Discovery.DynamicEndpoint> configuração, portanto, é útil quando você precisa de descoberta em sua solução, mas não deseja modificar a lógica do cliente – você só precisa modificar os pontos de extremidade. <xref:System.ServiceModel.Discovery.DiscoveryClient>por outro lado, pode ser usado para obter um controle mais preciso sobre a operação de pesquisa. Os usos e benefícios de cada um são elaborados abaixo.  
  
## <a name="discoveryclient"></a>DiscoveryClient  
 O <xref:System.ServiceModel.Discovery.DiscoveryClient> define métodos <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> e<xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> eventos de localização síncrona e assíncrona.  Ele também define métodos de resolução síncrono e assíncrono e <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveCompleted> um evento. Use os <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> métodos <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> ou para procurar serviços. Ambos os métodos usam uma <xref:System.ServiceModel.Discovery.FindCriteria> instância que permite especificar nomes de tipo de contrato, escopos, número máximo de resultados solicitados e regras de correspondência de escopo. Os <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> eventos <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> e podem ser usados ao chamar o <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> método. <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged>é acionado sempre <xref:System.ServiceModel.Discovery.DiscoveryClient> que o recebe uma resposta de um serviço. Ele pode ser usado para exibir uma barra de progresso que mostra o progresso da operação de localização. Ele também pode ser usado para agir em busca de respostas à medida que elas são recebidas. O <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> evento é acionado quando a operação Localizar é concluída. Isso pode acontecer porque o número máximo de respostas foi recebido ou se o <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> foi decorrido. Quando a operação Localizar é concluída, os resultados são retornados em <xref:System.ServiceModel.Discovery.FindResponse> uma instância. O <xref:System.ServiceModel.Discovery.FindResponse> contém uma coleção de <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> que contém os endereços, os nomes de tipo de contrato, as extensões, os URIs de escuta e os escopos dos serviços correspondentes. Você pode usar essas informações para se conectar e chamar um dos serviços correspondentes. O exemplo a seguir mostra como chamar o método System. ServiceModel. Discovery. DiscoveryClient. Localize (System. ServiceModel. Discovery. FindCriteria) e usar os metadados retornados para chamar o serviço encontrado. Um benefício do uso <xref:System.ServiceModel.Discovery.DiscoveryClient.Find(System.ServiceModel.Discovery.FindCriteria)> do é que você pode armazenar em cache a lista de pontos de extremidade que você encontrou e usá-los em um momento posterior. Com esse cache, você pode criar uma lógica personalizada para lidar com várias condições de falha.  
  
```csharp
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
FindCriteria criteria = new FindCriteria(typeof(ICalculatorService));  
FindResponse fr = dc.Find(criteria);  
  
if (fr.Endpoints.Count > 0)  
{  
   EndpointAddress ep = fr.Endpoints[0].Address;  
   CalculatorServiceClient client = new CalculatorServiceClient();  
  
    // Connect to the discovered service endpoint  
   client.Endpoint.Address = endpointAddress;  
   Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
   double value1 = 100.00D;  
   double value2 = 15.99D;  
  
   // Call the Add service operation.  
   double result = client.Add(value1, value2);  
   Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
}  
else  
   Console.WriteLine("No matching endpoints found");  
```  
  
 O exemplo a seguir mostra como executar uma operação Localizar de forma assíncrona.  
  
```csharp
static void FindServiceAsync()  
{  
   DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());   
   dc.FindCompleted += new EventHandler<FindCompletedEventArgs>( discoveryClient_FindCompleted);  
   dc.FindProgressChanged += new EventHandler<FindProgressChangedEventArgs>(discoveryClient_FindProgressChanged);  
   dc.FindAsync(new FindCriteria(typeof(ICalculatorService)));   
}   
static void discoveryClient_FindProgressChanged(object sender, FindProgressChangedEventArgs e)  
{  
   Console.WriteLine("Found service at: " + e.EndpointDiscoveryMetadata.Address  
}   
  
static void discoveryClient_FindCompleted(object sender, FindCompletedEventArgs e)  
{    
      if (e.Result.Endpoints.Count > 0)  
            {  
                EndpointAddress ep = e.Result.Endpoints[0].Address;  
                CalculatorServiceClient client = new CalculatorServiceClient();  
  
                // Connect to the discovered service endpoint  
                client.Endpoint.Address = ep;  
                Console.WriteLine("Invoking CalculatorService at {0}", ep);  
  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
            }  
            else  
                Console.WriteLine("No matching endpoints found");  
  
        }  
```
  
 Use os <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> métodos <xref:System.ServiceModel.Discovery.DiscoveryClient.ResolveAsync%28System.ServiceModel.Discovery.ResolveCriteria%29> e para localizar um serviço com base em seu endereço de ponto de extremidade. Isso é útil quando o endereço do ponto de extremidade não é endereçável de rede. Os métodos de resolução tomam uma instância <xref:System.ServiceModel.Discovery.ResolveCriteria> do que permite especificar o endereço do ponto de extremidade do serviço que você está resolvendo, a duração máxima da operação de resolução e um conjunto de extensões. O exemplo a seguir mostra como usar o <xref:System.ServiceModel.Discovery.DiscoveryClient.Resolve%2A> método para resolver um serviço.  
  
```csharp  
DiscoveryClient dc = new DiscoveryClient(new UdpDiscoveryEndpoint());  
ResolveCriteria criteria = new ResolveCriteria(endpointAddress);  
ResolveResponse response = dc.Resolve(criteria);  
EndpointAddress newEp = response.EndpointDiscoveryMetadata.Address;  
```  
  
## <a name="dynamicendpoint"></a>DynamicEndpoint  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>é um ponto de extremidade padrão (para obter mais informações, consulte [pontos de extremidades padrão](../../../../docs/framework/wcf/feature-details/standard-endpoints.md)) que executa a descoberta e seleciona automaticamente um serviço correspondente. Basta criar uma <xref:System.ServiceModel.Discovery.DynamicEndpoint> passagem no contrato para pesquisar e a associação a ser usada e passar a <xref:System.ServiceModel.Discovery.DynamicEndpoint> instância para o cliente WCF. O exemplo a seguir mostra como criar e usar um <xref:System.ServiceModel.Discovery.DynamicEndpoint> para chamar o serviço de calculadora. A descoberta é executada toda vez que o cliente é aberto. Qualquer ponto de extremidade definido na configuração também pode ser convertido <xref:System.ServiceModel.Discovery.DynamicEndpoint> em um adicionando `kind ="dynamicEndpoint"` o atributo ao elemento de configuração do ponto de extremidade.  
  
```csharp  
DynamicEndpoint dynamicEndpoint = new DynamicEndpoint(ContractDescription.GetContract(typeof(ICalculatorService)), new WSHttpBinding());  
CalculatorServiceClient client = new CalculatorServiceClient(dynamicEndpoint);  
  
Console.WriteLine("Invoking CalculatorService");  
Console.WriteLine();  
  
double value1 = 100.00D;  
double value2 = 15.99D;  
  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
## <a name="see-also"></a>Consulte também

- [Descoberta com escopos](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)
- [Básico](../../../../docs/framework/wcf/samples/basic-sample.md)
