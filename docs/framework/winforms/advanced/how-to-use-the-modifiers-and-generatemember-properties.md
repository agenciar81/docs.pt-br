---
title: 'Como: usar os modificadores e as propriedades GenerateMember'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
ms.openlocfilehash: 3fbaaae53aa60f6356c3a8daa0513de86ef2dacb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211292"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a>Como: usar os modificadores e as propriedades GenerateMember

Quando você coloca um componente em um Windows Form, duas propriedades são fornecidas pelo ambiente de design: `GenerateMember` e `Modifiers`. A propriedade `GenerateMember` especifica quando o Designer de Formulários do Windows gera uma variável de membro de um componente. A propriedade `Modifiers` é o modificador de acesso atribuído a essa variável de membro. Se o valor da propriedade `GenerateMember` for `false`, o valor da propriedade `Modifiers` não terá efeito.

## <a name="specify-whether-a-component-is-a-member-of-the-form"></a>Especifique se um componente é um membro do formulário

1. No Visual Studio, no Designer de formulários do Windows, abra o formulário.

2. Abra o **caixa de ferramentas**e no formulário, coloque três <xref:System.Windows.Forms.Button> controles.

3. Defina as `GenerateMember` e `Modifiers` propriedades de cada <xref:System.Windows.Forms.Button> controle de acordo com a tabela a seguir.

    |Nome do botão|Valor GenerateMember|Valor de modificadores|
    |-----------------|--------------------------|---------------------|
    |`button1`|`true`|`private`|
    |`button2`|`true`|`protected`|
    |`button3`|`false`|Nenhuma alteração|

4. Compile a solução.

5. Em **Gerenciador de Soluções**, clique no botão **Mostrar Todos os Arquivos**.

6. Abra o nó **Form1** e no **Editor de Códigos**, abra o arquivo **Form1.Designer.vb** ou **Form1. Designer.cs**. Esse arquivo contém o código emitido pelo Designer de Formulários do Windows.

7. Localize as declarações dos três botões. O exemplo de código a seguir mostra as diferenças especificadas pelas propriedades `GenerateMember` e `Modifiers`.

     [!code-csharp[System.Windows.Forms.GenerateMember#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]

     [!code-csharp[System.Windows.Forms.GenerateMember#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]

> [!NOTE]
> Por padrão, o Designer de formulários do Windows atribui a `private` (`Friend` no Visual Basic) modificador para controles de contêiner como <xref:System.Windows.Forms.Panel>. Se sua base <xref:System.Windows.Forms.UserControl> ou <xref:System.Windows.Forms.Form> tem um controle de contêiner, ele não aceitará novos filhos em controles e formulários herdados. A solução é alterar o modificador da caixa de controles de base para `protected` ou `public`.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.Button>
- [Herança Visual dos Windows Forms](windows-forms-visual-inheritance.md)
- [Passo a passo: Demonstrando Herança Visual](walkthrough-demonstrating-visual-inheritance.md)
- [Como: Herdar Windows Forms](how-to-inherit-windows-forms.md)
