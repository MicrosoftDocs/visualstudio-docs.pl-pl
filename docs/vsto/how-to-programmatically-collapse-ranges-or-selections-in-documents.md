---
title: Programistyczne zwijanie zakresów lub zaznaczenia w dokumentach
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bb22f97b6a876029ff5d984abf9bda32cfd3fbc
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585291"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Instrukcje: programowe zwijanie zakresów lub zaznaczenia w dokumentach
  Jeśli pracujesz z <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> obiektem lub, możesz chcieć zmienić zaznaczenie na punkt wstawiania przed wstawianiem tekstu, aby uniknąć zastępowania istniejącego tekstu. Zarówno <xref:Microsoft.Office.Interop.Word.Range> obiekty, jak i <xref:Microsoft.Office.Interop.Word.Selection> mają metodę zwijania, która korzysta z <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> wartości wyliczenia:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> zwija zaznaczenie do początku zaznaczenia. Jest to wartość domyślna, jeśli nie określisz wartości wyliczenia.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> zwija zaznaczenie do końca zaznaczenia.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Aby zwinąć zakres i wstawić nowy tekst

1. Utwórz <xref:Microsoft.Office.Interop.Word.Range> obiekt, który składa się z pierwszego akapitu w dokumencie.

    Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu.

    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]

    Poniższy przykład kodu może być używany w dodatku VSTO. Ten kod używa aktywnego dokumentu.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]

2. Użyj <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> wartości wyliczenia, aby zwinąć zakres.

    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]

3. Wstaw nowy tekst.

    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]

4. Wybierz aplikację <xref:Microsoft.Office.Interop.Word.Range>.

    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]

   Jeśli używasz <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> wartości wyliczenia, tekst zostanie wstawiony na początku następnego akapitu.

   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]

   Może się zdarzyć, że wstawienie nowego zdania spowoduje jego wstawienie przed znacznikiem akapitu, ale nie jest to przypadek, ponieważ oryginalny zakres zawiera znacznik akapitu. Aby uzyskać więcej informacji, zobacz [How to: programowe wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Aby zwinąć zakres w dostosowaniu na poziomie dokumentu

1. Poniższy przykład przedstawia metodę Complete dla dostosowania na poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Aby zwinąć zakres w dodatku narzędzi VSTO

1. Poniższy przykład przedstawia metodę Complete dla dodatku VSTO. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: programowe pobieranie znaków początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Instrukcje: Programowane wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Instrukcje: Programowane poszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Instrukcje: Programowane Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
