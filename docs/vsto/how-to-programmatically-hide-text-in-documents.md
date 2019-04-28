---
title: 'Instrukcje: Programowe ukrywanie tekstu w dokumentach'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1da471ff1911cdda4a62ef9c150236b3a225342f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812771"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Instrukcje: Programowe ukrywanie tekstu w dokumentach
  Można ukryć tekstu w dokumencie, ustawiając <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> właściwość <xref:Microsoft.Office.Interop.Word.Range.Font%2A> dla określonego zakresu tekstu.

 Na przykład, można tymczasowo ukryć tekstu w <xref:Microsoft.Office.Tools.Word.Bookmark> (w dostosowaniu na poziomie dokumentu) lub <xref:Microsoft.Office.Interop.Word.Bookmark> (w VSTO Add-) przed wysłaniem dokumentu do drukarki.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Aby ukryć tekstu w kontrolce zakładki podczas wydruku dokumentu

1. Utwórz procedurę, która ukrywa cały tekst, który znajduje się w określonym zakresie.

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. Tworzenie procedury, która odkrywa cały tekst, który znajduje się w określonym zakresie.

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. Zakres zakładki w celu przekazania `HideText` metody, wydrukować dokument, a następnie przekazać ten sam zakres do `UnhideText` metody.

     Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     Poniższy przykład kodu może służyć w dodatku VSTO. W tym przykładzie użyto aktywnego dokumentu. Aby korzystać z przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład kodu zakłada, że dokument zawiera <xref:Microsoft.Office.Tools.Word.Bookmark> formantu (w dostosowaniu na poziomie dokumentu) lub <xref:Microsoft.Office.Interop.Word.Bookmark> formantu (w VSTO Add-), który nosi nazwę `bookmark1`.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe drukowanie dokumentów](../vsto/how-to-programmatically-print-documents.md)
- [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowe Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Instrukcje: Programowe Aktualizowanie tekstu zakładki](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
