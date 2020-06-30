---
title: 'Instrukcje: Programowane korzystanie z okien dialogowych programu Word w trybie ukrytym'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 923fc7ddec0350f254968fe17494ecbe27f76b13
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537582"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Instrukcje: Programowane korzystanie z okien dialogowych programu Word w trybie ukrytym
  Można wykonywać złożone operacje przy użyciu jednego wywołania metody przez wywoływanie wbudowanych okien dialogowych w Microsoft Office Word bez wyświetlania ich użytkownikowi. Można to zrobić za pomocą <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Dialog> obiektu bez wywoływania <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> metody.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Przykłady
 Poniższy przykład kodu pokazuje, jak używać okna dialogowego **Ustawienia strony** w trybie ukrytym do ustawiania właściwości ustawień wielu stron bez wprowadzania danych przez użytkownika. W przykładach użyto <xref:Microsoft.Office.Interop.Word.Dialog> obiektu do skonfigurowania niestandardowego rozmiaru strony. Określone ustawienia dla ustawień strony, takie jak górny margines, dolny margines i tak dalej, są dostępne jako właściwości z późnym wiązaniem <xref:Microsoft.Office.Interop.Word.Dialog> obiektu. Te właściwości są tworzone dynamicznie przez program Word w czasie wykonywania.

 W poniższym przykładzie pokazano, jak wykonać to zadanie w Visual Basic projektach, w których **opcja Strict** jest wyłączona i w projektach Visual C#, które są przeznaczone dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . W tych projektach można używać funkcji późnego wiązania w kompilatorach Visual Basic i Visual C#. Aby użyć tego przykładu, należy uruchomić go `ThisDocument` z `ThisAddIn` klasy lub w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 W poniższym przykładzie pokazano, jak wykonać to zadanie w Visual Basic projekty, w których **opcja Strict** jest włączona. W tych projektach należy użyć odbicia, aby uzyskać dostęp do właściwości z późnym wiązaniem. Aby użyć tego przykładu, należy uruchomić go `ThisDocument` z `ThisAddIn` klasy lub w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane Używanie wbudowanych okien dialogowych w programie Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)
- [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)
- [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
