---
title: 'Método ICorDebugExceptionDebugEvent:: GetNativeIP'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 31af92dae47027b7285b422a05014b081d7e39a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788680"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a>Método ICorDebugExceptionDebugEvent:: GetNativeIP
Obtém o ponteiro de instrução nativa para este evento de depuração de exceção.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pIP`  
 fora Um ponteiro para o ponteiro de instrução deste evento de depuração de exceção. Consulte a seção Comentários para obter mais informações.  
  
## <a name="remarks"></a>Comentários  
 O significado desse ponteiro de instrução depende do tipo de evento, conforme mostrado na tabela a seguir.  
  
|Tipo de evento|Significado do valor de `pStackPointer`|  
|----------------|--------------------------------------|  
|[MANAGED_EXCEPTION_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|O endereço da instrução com falha.|  
|[MANAGED_EXCEPTION_USER_FIRST_CHANCE](cordebugrecordformat-enumeration.md)|O endereço do código no quadro indicado pelo método [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) em que a execução será retomada se nenhuma exceção tivesse sido gerada. A exceção pode ou não causar código diferente, como o bloco catch de uma cláusula `try/catch/finally`, a ser executada nesse quadro.|  
|[MANAGED_EXCEPTION_CATCH_HANDLER_FOUND](cordebugrecordformat-enumeration.md)|O endereço de código em que `catch` execução do manipulador será iniciada no quadro indicado pelo método [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) .|  
|[MANAGED_EXCEPTION_UNHANDLED](cordebugrecordformat-enumeration.md)|`pIP` é 0.|  
  
 O tipo de evento está disponível no método [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugExceptionDebugEvent](icordebugexceptiondebugevent-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
