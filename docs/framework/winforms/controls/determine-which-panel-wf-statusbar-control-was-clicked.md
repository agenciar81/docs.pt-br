---
title: Determine em qual painel no controle StatusBar foi clicado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
ms.openlocfilehash: 94619f8bd426a42e5dafa0db99880e20d24f9963
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746017"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Como determinar qual painel no controle StatusBar dos Windows Forms foi clicado
> [!IMPORTANT]
> Os controles <xref:System.Windows.Forms.StatusStrip> e <xref:System.Windows.Forms.ToolStripStatusLabel> substituem e adicionam funcionalidade aos controles <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel>; no entanto, os controles <xref:System.Windows.Forms.StatusBar> e <xref:System.Windows.Forms.StatusBarPanel> são mantidos para compatibilidade com versões anteriores e uso futuro, se você escolher.  
  
 Para programar o controle [StatusBar](statusbar-control-windows-forms.md) Control para responder aos cliques do usuário, use uma instrução case dentro do evento <xref:System.Windows.Forms.StatusBar.PanelClick>. O evento contém um argumento (o argumento de painel), que contém uma referência ao <xref:System.Windows.Forms.StatusBarPanel>clicado. Usando essa referência, determine o índice do painel clicado e programe adequadamente.  
  
> [!NOTE]
> Verifique se a propriedade <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> do controle de <xref:System.Windows.Forms.StatusBar> está definida como `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Para determinar qual painel foi clicado  
  
1. No manipulador de eventos <xref:System.Windows.Forms.StatusBar.PanelClick>, use uma instrução `Select Case` (na Visual Basic) ou `switch case` ( C# Visual ou C++Visual) para determinar qual painel foi clicado examinando o índice do painel clicado nos argumentos do evento.  
  
     O exemplo de código a seguir requer a presença, no formulário, de um controle de <xref:System.Windows.Forms.StatusBar>, `StatusBar1`e dois objetos <xref:System.Windows.Forms.StatusBarPanel>, `StatusBarPanel1` e `StatusBarPanel2`.  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,   
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     (Visual C#, Visual C++) Coloque o seguinte código no construtor do formulário para registrar o manipulador de eventos.  
  
    ```csharp  
    this.statusBar1.PanelClick += new   
       System.Windows.Forms.StatusBarPanelClickEventHandler   
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Como definir o tamanho de painéis da barra de status](how-to-set-the-size-of-status-bar-panels.md)
- [Passo a passo: atualizando informações da barra de status em tempo de execução](walkthrough-updating-status-bar-information-at-run-time.md)
- [Visão geral do controle StatusBar](statusbar-control-overview-windows-forms.md)
