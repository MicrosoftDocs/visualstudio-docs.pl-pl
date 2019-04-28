---
title: 'Instrukcje: Programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 22f8035cc7c1b09e7fd54f3c10842237ee6273b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812416"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>Instrukcje: Programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach
  <xref:Microsoft.Office.Interop.Word.Find> Klasa ma <xref:Microsoft.Office.Interop.Word.Find.Found%2A> właściwość, która zwraca **true** zawsze, gdy zostanie znaleziony przeszukiwane dla elementu. Można pętli za pośrednictwem wszystkich wystąpień w <xref:Microsoft.Office.Interop.Word.Range> przy użyciu <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>W pętli poprzez znalezione elementy

1. Zadeklaruj <xref:Microsoft.Office.Interop.Word.Range> obiektu.

    Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu.

    [!code-vb[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomation#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#79)]

    Poniższy przykład kodu może służyć w dodatku VSTO. W tym przykładzie użyto aktywnego dokumentu.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#79)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#79](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#79)]

2. Użyj <xref:Microsoft.Office.Interop.Word.Find.Found%2A> właściwości w pętli, aby wyszukać wszystkie wystąpienia ciągu w dokumencie i zwiększ zmienną całkowitą przez 1 każdorazowo ciąg zostanie znaleziony.

    [!code-vb[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#80)]
    [!code-csharp[Trin_VstcoreWordAutomation#80](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#80)]

3. Wyświetlana jest liczba przypadków, gdy ciąg został znaleziony w oknie komunikatu.

    [!code-vb[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#81)]
    [!code-csharp[Trin_VstcoreWordAutomation#81](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#81)]

   Poniższe przykłady przedstawiają kompletny metody.

## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Pętli elementów w dostosowaniu na poziomie dokumentu

1. Poniższy przykład pokazuje kompletny kod dla dostosowywania poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomation#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#78)]

## <a name="vsto-add-in-example"></a>Przykładu dodatku narzędzi VSTO

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>W pętli między elementami w dodatku narzędzi VSTO

1. Poniższy przykład pokazuje kompletny kod dla dodatku VSTO. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#78)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#78](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#78)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe wyszukiwanie i zastępowanie rext w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Instrukcje: Programowe Ustawianie opcji wyszukiwania w programie Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowe Przywracanie zaznaczenia po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
