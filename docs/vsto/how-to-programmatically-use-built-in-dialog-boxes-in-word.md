---
title: 'Instrukcje: Programowane Używanie wbudowanych okien dialogowych w programie Word'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 6edba0b1fe9f06dbf7dba8dd1a3d01c4041ba8fe
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585657"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Instrukcje: Programowane Używanie wbudowanych okien dialogowych w programie Word
  Podczas pracy z programem Microsoft Office Word istnieją przypadki, gdy konieczne jest wyświetlenie okien dialogowych dotyczących danych wejściowych użytkownika. Mimo że możesz utworzyć własne, możesz również użyć wbudowanych okien dialogowych w programie Word, które są uwidocznione w <xref:Microsoft.Office.Interop.Word.Dialogs> kolekcji <xref:Microsoft.Office.Interop.Word.Application> obiektów. Dzięki temu można uzyskać dostęp do ponad 200 wbudowanych okien dialogowych, które są reprezentowane jako wyliczenia.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Wyświetlanie okien dialogowych
 Aby wyświetlić okno dialogowe, użyj jednej z wartości <xref:Microsoft.Office.Interop.Word.WdWordDialog> wyliczenia, aby utworzyć <xref:Microsoft.Office.Interop.Word.Dialog> obiekt, który reprezentuje okno dialogowe, które chcesz wyświetlić. Następnie Wywołaj <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metodę <xref:Microsoft.Office.Interop.Word.Dialog> obiektu.

 Poniższy przykład kodu pokazuje, jak wyświetlić okno dialogowe **Otwórz plik** . Aby użyć tego przykładu, należy uruchomić go `ThisDocument` z `ThisAddIn` klasy lub w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#100)]
 [!code-csharp[Trin_VstcoreWordAutomation#100](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#100)]

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Dostęp do członków okna dialogowego, które są dostępne za późnym wiązaniem
 Niektóre właściwości i metody okien dialogowych w programie Word są dostępne tylko przez późne wiązanie. W Visual Basic projekty, w których **opcja Strict** jest włączona, należy użyć odbicia, aby uzyskać dostęp do tych elementów członkowskich. Aby uzyskać więcej informacji, zobacz [późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).

 Poniższy przykład kodu demonstruje, jak używać właściwości **name** okna dialogowego **otwieranie pliku** w projektach Visual Basic, gdzie **Option Strict** jest wyłączona lub w projektach Visual C#, które są przeznaczone dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Aby użyć tego przykładu, należy uruchomić go `ThisDocument` z `ThisAddIn` klasy lub w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Poniższy przykład kodu ilustruje sposób używania odbicia w celu uzyskania dostępu do właściwości **Nazwa** okna dialogowego **otwieranie pliku** w projektach Visual Basic, w których **opcja Strict** jest włączona. Aby użyć tego przykładu, należy uruchomić go `ThisDocument` z `ThisAddIn` klasy lub w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane korzystanie z okien dialogowych programu Word w trybie ukrytym](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Option Strict — Instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
