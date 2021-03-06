---
title: Usando variação em delegações
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: 9c2aad0e4b9408939600938412fe5c3e73b5bf15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349026"
---
# <a name="using-variance-in-delegates-visual-basic"></a>Usando a variação em delegados (Visual Basic)

Quando você atribui um método a um delegado, a *covariância* e a *contravariância* fornece flexibilidade para corresponder um tipo de delegado a uma assinatura de método. A covariância permite que um método tenha o tipo de retorno mais derivado do que o definido no delegado. A contravariância permite que um método que tem tipos de parâmetro menos derivados do que no tipo delegado.

## <a name="example-1-covariance"></a>Exemplo 1: covariância

### <a name="description"></a>Descrição

Este exemplo demonstra como delegados podem ser usados com métodos que têm tipos de retorno que são derivados do tipo de retorno na assinatura do delegado. O tipo de dados retornado por `DogsHandler` é do tipo `Dogs`, que deriva do tipo `Mammals` definido no delegado.

### <a name="code"></a>Código

```vb
Class Mammals
End Class

Class Dogs
    Inherits Mammals
End Class
Class Test
    Public Delegate Function HandlerMethod() As Mammals
    Public Shared Function MammalsHandler() As Mammals
        Return Nothing
    End Function
    Public Shared Function DogsHandler() As Dogs
        Return Nothing
    End Function
    Sub Test()
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler
        ' Covariance enables this assignment.
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler
    End Sub
End Class
```

## <a name="example-2-contravariance"></a>Exemplo 2: contravariância

### <a name="description"></a>Descrição

Este exemplo demonstra como representantes podem ser usados com métodos que têm parâmetros cujos tipos são tipos base do tipo de parâmetro de assinatura do representante. Com a contravariância, você pode usar um manipulador de eventos em vez de manipuladores separados. O seguinte exemplo usa dois representantes:

- Um representante <xref:System.Windows.Forms.KeyEventHandler> que define a assinatura do evento [Button.KeyDown](xref:System.Windows.Forms.Control.KeyDown). Sua assinatura é:

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- Um representante <xref:System.Windows.Forms.MouseEventHandler> que define a assinatura do evento [Button.MouseClick](xref:System.Windows.Forms.Control.MouseDown). Sua assinatura é:

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

O exemplo define um manipulador de eventos com um parâmetro <xref:System.EventArgs> e o usa para manipular os eventos `Button.KeyDown` e `Button.MouseClick`. Ele pode fazer isso porque <xref:System.EventArgs> é um tipo base de <xref:System.Windows.Forms.KeyEventArgs> e <xref:System.Windows.Forms.MouseEventArgs>.

### <a name="code"></a>Código

```vb
' Event handler that accepts a parameter of the EventArgs type.
Private Sub MultiHandler(ByVal sender As Object,
                         ByVal e As System.EventArgs)
    Label1.Text = DateTime.Now
End Sub

Private Sub Form1_Load(ByVal sender As System.Object,
    ByVal e As System.EventArgs) Handles MyBase.Load

    ' You can use a method that has an EventArgs parameter,
    ' although the event expects the KeyEventArgs parameter.
    AddHandler Button1.KeyDown, AddressOf MultiHandler

    ' You can use the same method
    ' for the event that expects the MouseEventArgs parameter.
    AddHandler Button1.MouseClick, AddressOf MultiHandler
End Sub
```

## <a name="see-also"></a>Consulte também

- [Variação em delegados (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Usando variação para delegados genéricos Func e Action (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
