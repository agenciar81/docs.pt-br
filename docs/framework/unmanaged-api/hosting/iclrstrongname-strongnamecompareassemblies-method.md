---
title: Método ICLRStrongName::StrongNameCompareAssemblies
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: 16b51393c945061efb0e94e48e5388c60472ee11
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899754"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a>Método ICLRStrongName::StrongNameCompareAssemblies
Determina se dois assemblies diferem somente por suas assinaturas de nome forte.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `wszAssembly1`  
 no O caminho para o primeiro assembly.  
  
 `wszAssembly2`  
 no O caminho para o segundo assembly.  
  
 `pdwResult`  
 fora Um dos seguintes valores:  
  
- `SN_CMP_DIFFERENT` (0) – especifica que os assemblies contêm dados diferentes.  
  
- `SN_CMP_IDENTICAL` (1) – especifica que os assemblies são exatamente iguais, incluindo suas assinaturas e soma de verificação.  
  
- `SN_CMP_SIGONLY` (2) – especifica que os assemblies diferem somente por assinatura e soma de verificação.  
  
## <a name="return-value"></a>Valor de retorno  
 `S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="remarks"></a>Comentários  
 A assinatura de nome forte de um assembly consiste no nome de texto, versão, cultura e token de chave pública do assembly.  
  
## <a name="see-also"></a>Veja também

- [Interface ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
