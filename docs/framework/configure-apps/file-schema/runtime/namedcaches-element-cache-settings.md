---
title: Elemento <namedCaches> (Configurações de cache)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 4587234ad91fa3b1abbb376bd7ae517d5abea6c3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252458"
---
# <a name="namedcaches-element-cache-settings"></a>\<Elemento de > namedCaches (configurações de cache)
Especifica uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas. A <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Propriedade faz referência à coleção de definições de configuração de um `namedCaches` ou mais elementos do arquivo de configuração.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<sistema. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> memoryCache**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> namedCaches**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a>Tipo  
 `None`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|Um valor inteiro que especifica o tamanho máximo permitido, em megabytes, que uma instância de um <xref:System.Runtime.Caching.MemoryCache> pode aumentar para. O valor padrão é 0, o que significa que a heurística de dimensionamento automático <xref:System.Runtime.Caching.MemoryCache> da classe é usada por padrão.|  
|`name`|O nome do cache.|  
|`physicalMemoryLimitPercentage`|Um valor inteiro entre 0 e 100 que especifica a porcentagem máxima de memória do computador fisicamente instalada que pode ser consumida pelo cache. O valor padrão é 0, o que significa que a heurística de dimensionamento automático <xref:System.Runtime.Caching.MemoryCache> da classe é usada por padrão.|  
|`pollingInterval`|Um valor que indica o intervalo de tempo após o qual a implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em percentual que são definidos para a instância de cache. Esse valor é inserido no formato "HH: MM: SS".|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|Adiciona um cache nomeado à coleção de `namedCaches` para um cache de memória.|  
|[\<clear>](clear-element-for-namedcaches.md)|Limpa a coleção `namedCaches` de um cache de memória.|  
|[\<remove>](remove-element-for-namedcaches.md)|Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|Especifica o elemento raiz em cada arquivo de configuração que é usado pelo Common Language Runtime e .NET Framework aplicativos.|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|Define um elemento usado para configurar um cache baseado na classe <xref:System.Runtime.Caching.MemoryCache>.|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Contém tipos que permitem implementar o cache de saída em aplicativos que são criados no .NET Framework.|  
  
## <a name="remarks"></a>Comentários  
 A seção de configuração de cache de memória do arquivo Web. config `add`pode `remove`conter atributos `clear` , e para `namedCaches` a coleção. Cada `namedCaches` entrada é identificada exclusivamente `name` pelo atributo.  
  
 Você pode recuperar instâncias de entradas de cache de memória referenciando as informações nos arquivos de configuração do aplicativo. Por padrão, somente a instância de cache padrão tem uma entrada no arquivo de configuração. A instância de cache padrão é a instância que é retornada da <xref:System.Runtime.Caching.MemoryCache.Default%2A> propriedade.  
  
 Se você definir o atributo Name como "default", o elemento usará a instância de cache de memória padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como definir o nome do cache para o nome de entrada de cache padrão, definindo `name` o atributo como "default".  
  
 O `cacheMemoryLimitMegabytes` atributo e o `physicalMemoryPercentage` atributo são definidos como zero. Definir esses atributos como zero significa que a heurística de dimensionamento automático da <xref:System.Runtime.Caching.MemoryCache> classe é usada. A implementação de cache compara a carga de memória atual com os limites de memória absolutos e baseados em porcentagem a cada dois minutos.  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [\<Elemento de > memoryCache (configurações de cache)](memorycache-element-cache-settings.md)
