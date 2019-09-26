---
title: 'Instrukcje: Programistyczne używanie okien dialogowych programu Word w trybie ukrytym'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: e32c97069e3400b447f8756f9638c9d88d38d99a
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255850"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Instrukcje: Programistyczne używanie okien dialogowych programu Word w trybie ukrytym
  Można wykonywać złożone operacje przy użyciu jednego wywołania metody przez wywoływanie wbudowanych okien dialogowych w Microsoft Office Word bez wyświetlania ich użytkownikowi. Można to zrobić za pomocą <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Dialog> obiektu bez wywoływania <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> metody.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Przykłady
 Poniższy przykład kodu pokazuje, jak używać okna dialogowego **Ustawienia strony** w trybie ukrytym do ustawiania właściwości ustawień wielu stron bez wprowadzania danych przez użytkownika. W przykładach użyto <xref:Microsoft.Office.Interop.Word.Dialog> obiektu do skonfigurowania niestandardowego rozmiaru strony. Określone ustawienia dla ustawień strony, takie jak górny margines, dolny margines i tak dalej, są dostępne jako właściwości <xref:Microsoft.Office.Interop.Word.Dialog> z późnym wiązaniem obiektu. Te właściwości są tworzone dynamicznie przez program Word w czasie wykonywania.

 W poniższym przykładzie pokazano, jak wykonać to zadanie w Visual Basic projektach, w których **opcja Strict** jest wyłączona i C# w projektach wizualnych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]przeznaczonych dla. W tych projektach można używać funkcji późnego wiązania w kompilatorach Visual Basic i wizualizacji C# . Aby użyć tego przykładu, należy uruchomić go `ThisDocument` z `ThisAddIn` klasy lub w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 W poniższym przykładzie pokazano, jak wykonać to zadanie w Visual Basic projekty, w których **opcja Strict** jest włączona. W tych projektach należy użyć odbicia, aby uzyskać dostęp do właściwości z późnym wiązaniem. Aby użyć tego przykładu, należy uruchomić go `ThisDocument` z `ThisAddIn` klasy lub w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowo używaj wbudowanych okien dialogowych w programie Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)
- [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)
- [OdbicieC#()](/dotnet/csharp/programming-guide/concepts/reflection)
- [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
