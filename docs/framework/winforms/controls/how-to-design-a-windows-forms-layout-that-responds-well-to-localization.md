---
title: "How to: Design a Windows Forms Layout that Responds Well to Localization"
ms.date: "03/30/2017"
dev_langs: 
  - "csharp"
  - "vb"
helpviewer_keywords: 
  - "TableLayoutPanel control [Windows Forms]"
  - "application design [Windows Forms], localization"
  - "Windows Forms, localization"
  - "localization [Windows Forms], Windows Forms layout"
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
---
# How to: Design a Windows Forms Layout that Responds Well to Localization
Creating forms that are ready to be localized greatly speeds development for international markets. You can use the <xref:System.Windows.Forms.TableLayoutPanel> control to implement layouts that respond gracefully as controls resize due to changes in their <xref:System.Windows.Forms.Control.Text%2A> property values.  
  
## Example  
 This form demonstrates how to create a layout that proportionally adjusts when you translate displayed string values into other languages. This process of translation is called *localization*. For more information, see [Localization](../../../../docs/standard/globalization-localization/localization.md).  
  
 There is extensive support for this task in Visual Studio.  See also [Walkthrough: Creating a Layout That Adjusts Proportion for Localization](https://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [How to: Align and Stretch a Control in a TableLayoutPanel Control](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel](https://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))  
  
3.  [How to: Span Rows and Columns in a TableLayoutPanel Control](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4.  [How to: Edit Columns and Rows in a TableLayoutPanel Control](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5.  [Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](https://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))  
  
6.  [Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
7.  [Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property](https://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))  
  
8.  [How to: Support Localization on Windows Forms Using AutoSize and the TableLayoutPanel Control](https://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))  
  
9. [Walkthrough: Creating a Resizable Windows Form for Data Entry](https://msdn.microsoft.com/library/991eahec\(v=vs.110\))  
  
## Compiling the Code  
 This example requires:  
  
-   References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.  
  
 For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). You can also build this example in Visual Studio by pasting the code into a new project.  Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## See Also  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [Localization](../../../../docs/standard/globalization-localization/localization.md)
