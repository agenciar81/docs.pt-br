---
title: Enumeração COR_PRF_MONITOR
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
ms.openlocfilehash: 2d7984ce109fb2bac5a36ab5e4c83f386de5a488
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867094"
---
# <a name="cor_prf_monitor-enumeration"></a>Enumeração COR_PRF_MONITOR
Contém valores usados para especificar comportamentos, recursos ou eventos que o criador de perfis deseja assinar.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |   
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |   
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a>Membros  
 As seções a seguir listam `COR_PRF_MONITOR` membros de enumeração por categoria. As categorias são:  
  
- [Nenhum sinalizador definido](#None)  
  
- [Sinalizadores de retorno de chamada](#Callback)  
  
- [Sinalizadores de habilitação de recursos](#Feature)  
  
- [Sinalizadores de configuração](#Config)  
  
- [Sinalizadores compostos](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a>Nenhum sinalizador definido  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|Nenhum sinalizador está definido.|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a>Sinalizadores de retorno de chamada  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|Habilita todos os eventos de retorno de chamada.|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|Controla os retornos de chamada `AppDomainCreation*` e `AppDomainShutdown*` na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|Controla os retornos de chamada `AssemblyLoad*` e `AssemblyUnload*` na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|Controla os retornos de chamada `JITCachedFunctionSearch*` na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .<br /><br /> O comportamento deste sinalizador é alterado no .NET Framework versão 2.0.|  
|`COR_PRF_MONITOR_CCW`|Controla os retornos de chamada `COMClassicVTable*` na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CLASS_LOADS`|Controla os retornos de chamada `ClassLoad*` e `ClassUnload*` na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|Controla os retornos de chamada `ExceptionCLRCatcher*` na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|Controla os retornos de chamada [UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) e [ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_ENTERLEAVE`|Controla as [funções estáticas globais de perfil](profiling-global-static-functions.md) `FunctionEnter*`, `FunctionLeave*` e `FunctionTailCall*`.|  
|`COR_PRF_MONITOR_EXCEPTIONS`|Controla o retorno de chamada [ExceptionThrown](icorprofilercallback-exceptionthrown-method.md) e os retornos de chamada `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`e `ExceptionCatcher*` na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|Controla o retorno de chamada [FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_GC`|Controla os retornos de chamada [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md), [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md), [MovedReferences](icorprofilercallback-movedreferences-method.md), [MovedReferences2](icorprofilercallback4-movedreferences2-method.md), [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md), [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md), [RootReferences](icorprofilercallback-rootreferences-method.md), [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [HandleCreated](icorprofilercallback2-handlecreated-method.md), [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md)e [FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md) nas interfaces `ICorProfilerCallback*`. Quando `COR_PRF_MONITOR_GC` é alocado, a coleta de lixo simultânea é desativada.|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|Controla os retornos de chamada `JITCompilation*`, [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md)e [JITInlining](icorprofilercallback-jitinlining-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_MODULE_LOADS`|Controla os retornos de chamada `ModuleLoad*`, `ModuleUnload*`e [ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|Controla o retorno de chamada de [ObjectAllocated](icorprofilercallback-objectallocated-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_REMOTING`|Controla os retornos de chamada `Remoting*` na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|Controla se os retornos de chamada `Remoting*` vão monitorar ou não os eventos de forma assíncrona.|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|Controla se um cookie é passado para os retornos de chamada `Remoting*`.|  
|`COR_PRF_MONITOR_SUSPENDS`|Controla os retornos de chamada `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)e [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md) na interface [ICorProfilerCallback](icorprofilercallback-interface.md) .|  
|`COR_PRF_MONITOR_THREADS`|Controla os retornos de chamada [ThreadCreated](icorprofilercallback-threadcreated-method.md), [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md), [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)e [ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md) nas interfaces [ICorProfilerCallback](icorprofilercallback-interface.md) e [ICorProfilerCallback2](icorprofilercallback2-interface.md) .|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a>Sinalizadores de habilitação de recurso  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|Habilita a recuperação de um `ClassID` exato para uma função genérica chamando o método [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) com um valor de `COR_PRF_FRAME_INFO` retornado pelo retorno de chamada [FunctionEnter2](functionenter2-function.md) .|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|Habilita o rastreamento de argumentos usando o retorno de chamada [FunctionEnter2](functionenter2-function.md) ou o retorno de chamada [FunctionEnter3WithInfo](functionenter3withinfo-function.md) e o método [GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md) .|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|Habilita o rastreamento de valores de retorno usando o retorno de chamada [FunctionLeave2](functionleave2-function.md) ou o [FunctionLeave3WithInfo](functionleave3withinfo-function.md) retorno de chamada e o método [GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md) .|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|Preterido.<br /><br /> Não tem suporte no processo de depuração. Este sinalizador não tem efeito.|  
|`COR_PRF_ENABLE_JIT_MAPS`|Preterido.<br /><br /> Permite que o criador de perfil obtenha mapas de IL para nativo usando [GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md). A partir do .NET Framework 2.0, o runtime sempre acompanha os mapas IL para nativo, portanto, esse sinalizador é sempre considerado como definido.|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|Informa o runtime que o criador de perfil pode desejar para notificações de alocação do objeto. Este sinalizador deve ser definido durante a inicialização. Ele permite que o criador de perfil Use subseqüentemente o sinalizador `COR_PRF_MONITOR_OBJECT_ALLOCATED` para receber retornos de chamada de [objectallocate](icorprofilercallback-objectallocated-method.md) .|  
|`COR_PRF_ENABLE_REJIT`|Habilita chamadas para os métodos [RequestReJIT](icorprofilerinfo4-requestrejit-method.md) e [RequestRevert](icorprofilerinfo4-requestrevert-method.md) . O criador de perfil deve definir este sinalizador na inicialização.  Se o criador de perfil especificar este sinalizador, também deverá especificar `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|Habilita chamadas para o método [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) .|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a>Sinalizadores de configuração  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|Impede o carregamento de todas as imagens nativas (incluindo imagens aprimoradas do criador de perfil).  Se este sinalizador e o sinalizador `COR_PRF_USE_PROFILE_IMAGES` estiverem especificados, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` será usado.|  
|`COR_PRF_DISABLE_INLINING`|Desabilita todas as conexões embutidas.|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|Desabilita todas as otimizações de código.|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|Desabilita verificações de transparência de segurança que normalmente são feitas durante a compilação JIT (Just-in-Time) e o carregamento de classe para os conjuntos de confiança total. Isso pode facilitar a execução de instrumentação.|  
|`COR_PRF_USE_PROFILE_IMAGES`|Faz com que a imagem nativa procure imagens aprimoradas para o criador de perfil. Se nenhuma imagem aprimorada para o criador de perfil for encontrada para determinada montagem, o Common Language Runtime (CRL) retornará ao JIT para esse assembly. Se este sinalizador e o sinalizador `COR_PRF_DISABLE_ALL_NGEN_IMAGES` estiverem especificados, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` será usado.|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a>Sinalizadores compostos  
  
|{1&gt;Membro&lt;1}|Descrição|  
|------------|-----------------|  
|`COR_PRF_ALL`|Representa todos os valores de sinalizador `COR_PRF_MONITOR`.|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|Representa todos os sinalizadores `COR_PRF_MONITOR` que podem ser definidos após o criador de perfis ser anexado a um aplicativo em execução. A seção de sintaxe indica os sinalizadores individuais que estão presentes nesta bitmask.|  
|`COR_PRF_MONITOR_ALL`|Habilita todos os eventos de retorno de chamada.|  
|`COR_PRF_MONITOR_IMMUTABLE`|Representa todos os sinalizadores `COR_PRF_MONITOR` que podem ser definidos apenas durante a inicialização. A tentativa de alterar qualquer um desses sinalizadores após a inicialização retorna um valor `HRESULT` que indica falha.|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|Representa todos os sinalizadores `COR_PRF_MONITOR` que necessitam de imagens aprimoradas por perfil.|  
  
## <a name="remarks"></a>Comentários  
 Um valor de `COR_PRF_MONITOR` é usado com os métodos [ICorProfilerInfo:: GetEventMask](icorprofilerinfo-geteventmask-method.md) e [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) para definir as notificações de eventos que o Common Language Runtime faz para o criador de perfil.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Criando perfil de enumerações](profiling-enumerations.md)
- [Método GetEventMask](icorprofilerinfo-geteventmask-method.md)
- [Método SetEventMask](icorprofilerinfo-seteventmask-method.md)
