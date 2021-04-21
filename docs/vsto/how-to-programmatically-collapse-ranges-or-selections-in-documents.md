---
title: Programowe zwijanie zakresów lub wyborów w dokumentach
description: Dowiedz się, że jeśli pracujesz z obiektem Zakres lub Wybór, możesz zmienić zaznaczenie na punkt wstawiania przed wstawianiem tekstu.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5d1fb41943690da5144fb06245ed7f4aa70250aa
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828647"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>How to: Programowe zwijanie zakresów lub wyborów w dokumentach
  Jeśli pracujesz z obiektem lub , możesz zmienić zaznaczenie na punkt wstawiania przed wstawieniu tekstu, aby uniknąć <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> nadpisania istniejącego tekstu. Oba obiekty <xref:Microsoft.Office.Interop.Word.Range> i <xref:Microsoft.Office.Interop.Word.Selection> mają metodę Collapse, która korzysta z wartości <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> wyliczenia:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> Zwija zaznaczenie do początku zaznaczenia. Jest to wartość domyślna, jeśli nie określisz wartości wyliczenia.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> Zwija zaznaczenie na końcu zaznaczenia.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Aby zwinąć zakres i wstawić nowy tekst

1. Utwórz <xref:Microsoft.Office.Interop.Word.Range> obiekt, który składa się z pierwszego akapitu w dokumencie.

    Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet46":::

    Poniższy przykład kodu może być używany w dodatku VSTO. Ten kod używa aktywnego dokumentu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet46":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet46":::

2. Użyj wartości <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> wyliczenia, aby zwinąć zakres.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet47":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet47":::

3. Wstaw nowy tekst.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet48":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet48":::

4. Wybierz aplikację <xref:Microsoft.Office.Interop.Word.Range>.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet49":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet49":::

   Jeśli używasz wartości <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> wyliczenia, tekst zostanie wstawiony na początku poniższego akapitu.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet50":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet50":::

   Możesz oczekiwać, że wstawienie nowego zdania wstawi je przed znacznikiem akapitu, ale tak nie jest, ponieważ oryginalny zakres zawiera znacznik akapitu. Aby uzyskać więcej informacji, [zobacz Jak programowo wykluczać znaczniki akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Aby zwinąć zakres w dostosowywaniu na poziomie dokumentu

1. W poniższym przykładzie przedstawiono kompletną metodę dostosowywania na poziomie dokumentu. Aby użyć tego kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet45":::

## <a name="vsto-add-in-example"></a>Przykład dodatku VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Aby zwinąć zakres w dodatku VSTO

1. W poniższym przykładzie przedstawiono kompletną metodę dodatku VSTO. Aby użyć tego kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet45":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet45":::

## <a name="see-also"></a>Zobacz też
- [How to: Programowe wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [How to: Programowe pobieranie znaków początku i końca w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Dzieje się tak: Programowe wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Jak programowo rozszerzyć zakresy w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [How to: Programowe resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
