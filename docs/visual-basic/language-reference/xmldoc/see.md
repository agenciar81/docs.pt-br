---
title: <see>
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 3c149b8ff60bcc2aba06856ad95f461fb18da4b6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352224"
---
# <a name="see-visual-basic"></a>\<Ver > (Visual Basic)
Especifica um link para outro membro.  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<see cref="member"/>  
```  
  
## <a name="parameters"></a>Parâmetros  
 `member`  
 Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída. `member` deve ser exibido entre aspas duplas (" ").  
  
## <a name="remarks"></a>Comentários  
 Use a marca `<see>` para especificar um link de dentro do texto. Use [\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) para indicar o texto que você pode querer que apareça em uma seção "Veja também".  
  
 Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa a marca `<see>` na seção `UpdateRecord` comentários para fazer referência ao método `DoesRecordExist`.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Consulte também

- [Marcações de Comentário XML](../../../visual-basic/language-reference/xmldoc/index.md)
