---
title: Interface ICorRuntimeHost
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
ms.openlocfilehash: e66e1468a864ec85d88f759c481c7a9707d37f7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139541"
---
# <a name="icorruntimehost-interface"></a>Interface ICorRuntimeHost
Fornece métodos que permitem ao host iniciar e parar explicitamente o Common Language Runtime (CLR), criar e configurar domínios de aplicativo, acessar o domínio padrão e enumerar todos os domínios em execução no processo.  
  
 Na versão .NET Framework 2,0, essa interface é substituída por [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md).  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método CloseEnum](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|Redefine um enumerador de domínio de volta para o início da lista de domínios.|  
|[Método CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|Cria um domínio de aplicativo. O chamador recebe um ponteiro de interface do tipo <xref:System._AppDomain> para uma instância do tipo <xref:System.AppDomain?displayProperty=nameWithType>.|  
|[Método CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|Cria um domínio de aplicativo. Esse método permite que o chamador passe uma instância de IAppDomainSetup para configurar recursos adicionais da instância de <xref:System._AppDomain> retornada.|  
|[Método CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|Obtém um ponteiro de interface do tipo `IAppDomainSetup` a uma instância de <xref:System.AppDomainSetup>. `IAppDomainSetup` fornece métodos para configurar aspectos de um domínio de aplicativo antes de sua criação.|  
|[Método CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|Obtém um ponteiro de interface do tipo <xref:System.Security.Principal.IIdentity>, que permite ao host criar evidências de segurança para passar para [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) ou [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md).|  
|[Método CreateLogicalThreadState](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|Não use.|  
|[Método CurrentDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|Obtém um ponteiro de interface do tipo <xref:System._AppDomain> que representa o domínio carregado no thread atual.|  
|[Método DeleteLogicalThreadState](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|Não use.|  
|[Método EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|Obtém um enumerador para os domínios no processo atual.|  
|[Método GetConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|Obtém um objeto que permite ao host especificar a configuração de retorno de chamada do CLR.|  
|[Método GetDefaultDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|Obtém um ponteiro de interface do tipo <xref:System._AppDomain> que representa o domínio padrão para o processo atual.|  
|[Método LocksHeldByLogicalThread](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|Não use.|  
|[Método MapFile](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|Mapeia o arquivo especificado na memória. Esse método é obsoleto.|  
|[Método NextDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|Obtém um ponteiro de interface para o próximo domínio na enumeração.|  
|[Método Start](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|Inicia o CLR.|  
|[Método Stop](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|Interrompe a execução do código no tempo de execução para o processo atual.|  
|[Método SwitchInLogicalThreadState](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|Não use.|  
|[Método SwitchOutLogicalThreadState](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|Não use.|  
|[Método UnloadDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|Descarrega o domínio de aplicativo especificado do processo atual.|  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** 1,0, 1,1  
  
## <a name="see-also"></a>Consulte também

- <xref:System.AppDomain>
- [Hospedagem](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [Interface ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [Hosts de Tempo de Execução](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [Hospedagem de Interfaces](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Coclass CorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
