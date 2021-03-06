---
title: Classe Delegate '<classname>' não tem nenhum método Invoke. Portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método
ms.date: 07/20/2015
f1_keywords:
- vbc30220
- bc30220
helpviewer_keywords:
- BC30220
ms.assetid: 6be0d61c-f2f9-4f9b-ab90-8871a0d7206d
ms.openlocfilehash: 3fe164d868ee7bde0e687e1d592f4d5a17565aea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803630"
---
# <a name="delegate-class-classname-has-no-invoke-method-so-an-expression-of-this-type-cannot-be-the-target-of-a-method-call"></a>Classe delegate\<classname >' não tem método Invoke, portanto, uma expressão desse tipo não pode ser o destino de uma chamada de método
Uma chamada para `Invoke` através de um delegado falhou porque `Invoke` não está implementado na classe de delegado.  
  
 **ID do erro:** BC30220  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Certifique-se de que uma instância da classe de delegado foi criada com uma `Dim` instrução e que um procedimento foi designado para a instância de delegado com o `AddressOf` operador.  
  
2. Localize o código que implementa a classe delegada e verifique se ele implementa o `Invoke` procedimento.  
  
## <a name="see-also"></a>Consulte também

- [Delegados](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Instrução Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Operador AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
