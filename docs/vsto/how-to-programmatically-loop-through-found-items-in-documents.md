---
title: 'How to: Programmatically loop through found items in documents ( Jak programowo przechodzić w pętli przez znalezione elementy w dokumentach)'
description: Dowiedz się, jak programowo przechodzić w pętli przez znalezione elementy w dokumencie programu Microsoft Word przy użyciu Visual Studio.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ce3153eb4e2fd7fd44318097a6b76ef6e0346086
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827347"
---
# <a name="how-to-programmatically-loop-through-found-items-in-documents"></a>How to: Programmatically loop through found items in documents ( Jak programowo przechodzić w pętli przez znalezione elementy w dokumentach)
  Klasa ma właściwość , która zwraca wartość true za każdym razem, gdy zostanie znaleziony <xref:Microsoft.Office.Interop.Word.Find> <xref:Microsoft.Office.Interop.Word.Find.Found%2A> wyszukiwany element.  Możesz przechodzić w pętli przez wszystkie wystąpienia znalezione w metodzie <xref:Microsoft.Office.Interop.Word.Range> przy użyciu <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-loop-through-found-items"></a>Aby w pętli przechodzić przez znalezione elementy

1. Zadeklaruj <xref:Microsoft.Office.Interop.Word.Range> obiekt .

    Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet79":::

    Poniższy przykład kodu może być używany w dodatku VSTO. W tym przykładzie jest używany aktywny dokument.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet79":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet79":::

2. Użyj właściwości w pętli, aby wyszukać wszystkie wystąpienia ciągu w dokumencie i zwiększyć zmienną całkowitą o 1 za każdym razem, gdy <xref:Microsoft.Office.Interop.Word.Find.Found%2A> ciąg zostanie znaleziony.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet80":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet80":::

3. Wyświetlanie liczby znalezionych ciągów w oknie komunikatu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet81":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet81":::

   W poniższych przykładach przedstawiono metodę complete.

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="to-loop-through-items-in-a-document-level-customization"></a>Aby przechodzić w pętli przez elementy w dostosowywaniu na poziomie dokumentu

1. W poniższym przykładzie pokazano kompletny kod dostosowywania na poziomie dokumentu. Aby użyć tego kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet78":::

## <a name="vsto-add-in-example"></a>Przykład dodatku VSTO

### <a name="to-loop-through-items-in-a-vsto-add-in"></a>Aby w pętli przechodzić przez elementy w dodatku VSTO

1. W poniższym przykładzie pokazano pełny kod dodatku VSTO. Aby użyć tego kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet78":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet78":::

## <a name="see-also"></a>Zobacz też
- [How to: Programowe wyszukiwanie i zastępowanie rext w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Jak programowo ustawić opcje wyszukiwania w programie Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [How to: Programowe przywracanie wyborów po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
