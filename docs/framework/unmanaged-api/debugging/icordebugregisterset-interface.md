---
title: Interface ICorDebugRegisterSet
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet
helpviewer_keywords:
- ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: d3d9676d-0b87-4bc3-b679-7bbc7a186c88
topic_type:
- apiref
ms.openlocfilehash: f435db28d5c85d576f69e7612841fc46ae142332
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792078"
---
# <a name="icordebugregisterset-interface"></a>Interface ICorDebugRegisterSet
Representa o conjunto de registros disponíveis no computador que está executando o código no momento.  
  
## <a name="methods"></a>{1&gt;Métodos&lt;1}  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetRegisters](icordebugregisterset-getregisters-method.md)|Obtém o valor de cada registro (no computador que está executando o código) que é especificado pela máscara de bits.|  
|[Método GetRegistersAvailable](icordebugregisterset-getregistersavailable-method.md)|Obtém uma máscara de bits que indica quais registros neste `ICorDebugRegisterSet` estão disponíveis no momento.|  
|[Método GetThreadContext](icordebugregisterset-getthreadcontext-method.md)|Obtém o contexto do thread atual.|  
|[Método SetRegisters](icordebugregisterset-setregisters-method.md)|Não implementado para a versão de .NET Framework 2,0.|  
|[Método SetThreadContext](icordebugregisterset-setthreadcontext-method.md)|Não implementado para o .NET Framework 2,0.|  
  
## <a name="remarks"></a>Comentários  
 A interface `ICorDebugRegisterSet` dá suporte apenas a registros de 32 bits. Use a interface [ICorDebugRegisterSet2](icordebugregisterset2-interface.md) em plataformas como IA-64 que exigem registros adicionais.  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Depurando interfaces](debugging-interfaces.md)
- [Interface ICorDebugRegisterSet2](icordebugregisterset2-interface.md)
