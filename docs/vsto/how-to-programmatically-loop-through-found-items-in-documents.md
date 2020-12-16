---
title: 'Instrukcje: programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach'
description: Dowiedz się, w jaki sposób można programowo zapętlać przez znalezione elementy w dokumencie programu Microsoft Word przy użyciu programu Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- loops, through found items in documents
- documents [Office development in Visual Studio], searching
- text [Office development in Visual Studio], searching in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 634012cae7f12f5346ec83bbd2b41c1019ef066d
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525628"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Instrukcje: programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach
  <xref:Microsoft.Office.Interop.Word.Find>Klasa ma <xref:Microsoft.Office.Interop.Word.Find.Found%2A> Właściwość, która zwraca **wartość true** za każdym razem, gdy zostanie znaleziony przeszukiwany element. Możesz przechodzić między wszystkimi wystąpieniami znajdującymi się w <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodzie przy użyciu metody.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>Aby wykonać pętlę przez znalezione elementy

1. Zadeklaruj <xref:Microsoft.Office.Interop.Word.Range> obiekt.

    Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu.

    [!code-vb[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#79)]

    Poniższy przykład kodu może być używany w dodatku VSTO. Ten przykład używa aktywnego dokumentu.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#79)]

2. Użyj <xref:Microsoft.Office.Interop.Word.Find.Found%2A> właściwości w pętli, aby wyszukać wszystkie wystąpienia ciągu w dokumencie i zwiększyć zmienną całkowitą o 1 za każdym razem, gdy zostanie znaleziony ciąg.

    [!code-vb[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#80)]
    [!code-csharp[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#80)]

3. Wyświetla liczbę wystąpień ciągu w oknie komunikatu.

    [!code-vb[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#81)]
    [!code-csharp[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#81)]

   W poniższych przykładach pokazano kompletną metodę.

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Aby przepętlać do elementów w dostosowaniu na poziomie dokumentu

1. Poniższy przykład pokazuje kompletny kod dla dostosowania na poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#78)]

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>Aby przepętlać do elementów w dodatku narzędzi VSTO

1. Poniższy przykład pokazuje kompletny kod dodatku VSTO. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#78)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: programowe wyszukiwanie i zastępowanie rext w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Instrukcje: Programowane Ustawianie opcji wyszukiwania w programie Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowane przywracanie zaznaczenia po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
