---
title: O tipo <typename> não é compatível com CLS
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 2805cac71cb36d21f5ab21a5875183803d07a4b4
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65642376"
---
# <a name="type-typename-is-not-cls-compliant"></a>Tipo \<typename > não é compatível com CLS
Uma variável, propriedade ou função de retorno é declarada com um tipo de dados que não é compatível com CLS.  
  
 Para um aplicativo esteja em conformidade com o [independência de linguagem e componentes independentes de linguagem](../../../standard/language-independence-and-language-independent-components.md) (CLS), ele deve usar somente tipos compatíveis com CLS.  
  
 Os seguintes tipos de dados do Visual Basic não são compatíveis com CLS:  
  
- [Tipo de Dados SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [Tipo de Dados UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [Tipo de Dados ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [Tipo de Dados UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **ID do erro:** BC40041  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Se seu aplicativo precisa ser compatível com CLS, altere o tipo de dados desse elemento para o tipo compatível com CLS mais próximo. Por exemplo, no lugar de `UInteger` talvez você possa usar `Integer` se você não precisar que o intervalo de valores acima de 2.147.483.647. Se você precisar de intervalo estendido, você pode substituir `UInteger` com `Long`.  
  
- Se seu aplicativo não precisa ser compatível com CLS, você não precisará alterar nada. Você deve estar atento a sua falta de conformidade, no entanto.
