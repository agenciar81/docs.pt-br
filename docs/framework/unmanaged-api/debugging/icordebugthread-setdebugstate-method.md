---
title: Método ICorDebugThread::SetDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
ms.openlocfilehash: b7678c64a085a0d4951d398595b9be89af8eeb6b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791433"
---
# <a name="icordebugthreadsetdebugstate-method"></a>Método ICorDebugThread::SetDebugState
Define sinalizadores que descrevem o estado de depuração deste ICorDebugThread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `state`  
 no Uma combinação de bits e valores de enumeração de CorDebugThreadState que especificam o estado de depuração desse thread.  
  
## <a name="remarks"></a>Comentários  
 `SetDebugState` define o estado de depuração atual do thread. (O "estado de depuração atual" representa o estado de depuração se o processo deveria ser continuado, não o estado atual real.) O valor normal para isso é THREAD_RUN. Somente o depurador pode afetar o estado de depuração de um thread. Os Estados de depuração fazem a última vez em continuar, portanto, se você quiser manter um thread THREAD_SUSPENDed em várias vezes, poderá defini-lo uma vez e depois não precisará se preocupar com ele. Suspender threads e retomar o processo pode causar deadlocks, embora normalmente seja improvável. Essa é uma qualidade intrínseca de threads e processos e é por design. Um depurador pode interromper e retomar de forma assíncrona os threads para interromper o deadlock. Se o estado do usuário do thread incluir USER_UNSAFE_POINT, o thread poderá bloquear uma coleta de lixo (GC). Isso significa que o thread suspenso tem uma chance muito maior de causar um deadlock. Isso pode não afetar os eventos de depuração já enfileirados. Portanto, um depurador deve drenar toda a fila de eventos (chamando [ICorDebugController:: HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) antes de suspender ou retomar os threads. Caso contrário, ele pode receber eventos em um thread que ele acredita que já foi suspenso.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
