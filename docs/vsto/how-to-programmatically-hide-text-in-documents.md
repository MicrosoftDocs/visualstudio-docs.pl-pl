---
title: 'Instrukcje: programowe Ukrywanie tekstu w dokumentach'
description: Dowiedz się, jak ukryć tekst w dokumencie programu Microsoft Word, ustawiając właściwość Hidden czcionki dla określonego zakresu tekstu.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: a375e8b844f82b5d310841d7b4cdc092b18ff6c3
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525694"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Instrukcje: programowe Ukrywanie tekstu w dokumentach
  Można ukryć tekst w dokumencie, ustawiając <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> Właściwość <xref:Microsoft.Office.Interop.Word.Range.Font%2A> dla określonego zakresu tekstu.

 Na przykład można tymczasowo ukryć tekst wewnątrz <xref:Microsoft.Office.Tools.Word.Bookmark> (w dostosowaniu na poziomie dokumentu) lub <xref:Microsoft.Office.Interop.Word.Bookmark> (w dodatku VSTO) przed wysłaniem dokumentu do drukarki.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Aby ukryć tekst w kontrolce zakładki podczas drukowania dokumentu

1. Utwórz procedurę, która ukrywa cały tekst znajdujący się w określonym zakresie.

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. Utwórz procedurę, która ukrywa cały tekst, który znajduje się w określonym zakresie.

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. Przekazanie zakresu zakładki do `HideText` metody, wydrukowanie dokumentu, a następnie przekazanie tego samego zakresu do `UnhideText` metody.

     Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     Poniższy przykład kodu może być używany w dodatku VSTO. Ten przykład używa aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>Kompiluj kod
 W tym przykładzie kodu założono, że dokument zawiera <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę (w dostosowaniu na poziomie dokumentu) lub <xref:Microsoft.Office.Interop.Word.Bookmark> kontrolkę (w dodatku VSTO) o nazwie `bookmark1` .

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane drukowanie dokumentów](../vsto/how-to-programmatically-print-documents.md)
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowane Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Instrukcje: Programowane aktualizowanie tekstu zakładki](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
