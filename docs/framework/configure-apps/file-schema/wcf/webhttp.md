---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399162"
---
# <a name="webhttp"></a>\<> Webhttp
Esse elemento Especifica o <xref:System.ServiceModel.Description.WebHttpBehavior> em um ponto de extremidade por meio da configuração. Esse comportamento, quando usado em conjunto com o [ \<WebHttpBinding >](webhttpbinding.md) associação padrão, habilita o modelo de programação da Web para um serviço do Windows Communication Foundation (WCF).  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Webhttp**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Quando essa propriedade é definida como `true`, a infraestrutura do WCF determina o melhor formato a ser usado. A seleção automática de formato é desabilitada por padrão para compatibilidade com versões anteriores. A seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.|  
|DefaultBodyStyle|Especifica o estilo de corpo padrão de mensagens retornadas. Para obter mais informações, <xref:System.ServiceModel.Web.WebMessageBodyStyle> consulte e [formatação de http Web WCF](../../../wcf/feature-details/wcf-web-http-formatting.md).|  
|defaultOutgoingResponseFormat|Especifica o formato de resposta de saída padrão para mensagens. Para obter mais informações, consulte [formatação de http do WCF Web](../../../wcf/feature-details/wcf-web-http-formatting.md).|  
|faultExceptionEnabled|Obtém ou define o sinalizador que especifica se uma FaultException é gerada quando ocorre um erro de servidor interno (código de status HTTP: 500).|  
|helpEnabled|Obtém ou define um valor que determina se a página de ajuda está habilitada.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<> de comportamento](behavior-of-endpointbehaviors.md)|Especifica o conjunto de comportamentos de ponto de extremidade.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [Integração AJAX e suporte para JSON](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
