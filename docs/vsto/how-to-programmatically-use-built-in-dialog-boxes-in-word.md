---
title: 'Instrukcje: Programowe używanie wbudowanych okien dialogowych w programie Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f8037e4d91aa7706c7ffd7b9f32778dfeac79488
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644942"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Instrukcje: Programowe używanie wbudowanych okien dialogowych w programie Word
  Podczas pracy z programu Microsoft Office Word, istnieją razy, gdy zachodzi potrzeba wyświetlanie okien dialogowych na dane wejściowe użytkownika. Mimo że można tworzyć własne, można także podejścia użycia wbudowanych okien dialogowych w programie Word, które są widoczne w <xref:Microsoft.Office.Interop.Word.Dialogs> zbiór <xref:Microsoft.Office.Interop.Word.Application> obiektu. Umożliwia dostęp do ponad 200 wbudowanych okien dialogowych, które są reprezentowane jako wyliczenia.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Wyświetlanie okien dialogowych
 Aby wyświetlić okno dialogowe, użyj jednej z wartości <xref:Microsoft.Office.Interop.Word.WdWordDialog> wyliczeniu, aby utworzyć <xref:Microsoft.Office.Interop.Word.Dialog> obiekt reprezentujący okno dialogowe, które mają być wyświetlane. Następnie wywołaj <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metody <xref:Microsoft.Office.Interop.Word.Dialog> obiektu.

 Poniższy przykład kodu demonstruje sposób wyświetlania **Otwórz plik** okno dialogowe. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Dostęp do okna dialogowego pole składowe, które są dostępne za pośrednictwem późne powiązania
 Niektóre właściwości i metody okien dialogowych w programie Word są dostępne wyłącznie za pośrednictwem późnym wiązaniu. W języku Visual Basic projektów, gdzie **Option Strict** jest włączona, należy używać odbicia do dostęp do tych elementów członkowskich. Aby uzyskać więcej informacji, zobacz [późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).

 Poniższy przykład kodu demonstruje sposób używania **nazwa** właściwość **Otwórz plik** okno dialogowe w języku Visual Basic, projekty gdzie **Option Strict** jest wyłączone lub w języku Visual C# projekty przeznaczone [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Poniższy przykład kodu pokazuje, jak używać odbicia w celu uzyskania dostępu do **nazwa** właściwość **Otwórz plik** okno dialogowe w języku Visual Basic, projekty gdzie **Option Strict** jest na serwerze. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe używanie okien dialogowych programu Word w trybie ukrytym](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Option strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
