---
title: Programistyczne Znajdowanie i zamienianie tekstu w dokumentach
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 18a50d6d4ef52a0c50be0b72b4cab5706da4e2db
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547046"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Instrukcje: programowe wyszukiwanie i zastępowanie tekstu w dokumentach
  <xref:Microsoft.Office.Interop.Word.Find>Obiekt jest członkiem obu <xref:Microsoft.Office.Interop.Word.Selection> obiektów i i można go <xref:Microsoft.Office.Interop.Word.Range> użyć do wyszukania tekstu w Microsoft Office dokumentach programu Word. Replace polecenie jest rozszerzeniem polecenia find.

 Użyj <xref:Microsoft.Office.Interop.Word.Find> obiektu, aby wykonać pętlę w Microsoft Office dokumencie programu Word i wyszukać określony tekst, formatowanie lub styl, a następnie użyj <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> właściwości, aby zastąpić wszystkie znalezione elementy.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Użyj obiektu zaznaczenia
 Gdy używasz <xref:Microsoft.Office.Interop.Word.Selection> obiektu do znajdowania tekstu, wszystkie określone kryteria wyszukiwania są stosowane tylko do aktualnie zaznaczonego tekstu. Jeśli <xref:Microsoft.Office.Interop.Word.Selection> jest punktem wstawiania, dokument jest przeszukiwany. Po znalezieniu elementu pasującego do kryteriów wyszukiwania jest on automatycznie wybierany.

 Należy pamiętać, że <xref:Microsoft.Office.Interop.Word.Find> kryteria są skumulowane, co oznacza, że kryteria są dodawane do poprzednich kryteriów wyszukiwania. Wyczyść formatowanie poprzedniego wyszukiwania przy użyciu <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> metody przed wyszukiwaniem.

### <a name="to-find-text-using-a-selection-object"></a>Aby znaleźć tekst przy użyciu obiektu zaznaczenia

1. Przypisz ciąg wyszukiwania do zmiennej.

    [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
    [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]

2. Wyczyść formatowanie od poprzedniego wyszukiwania.

    [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
    [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]

3. Wykonaj wyszukiwanie i Wyświetl okno komunikatu z wynikami.

    [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
    [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]

   Poniższy przykład przedstawia metodę Complete.

   [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
   [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]

## <a name="use-a-range-object"></a>Użyj obiektu zakresu
 Użycie <xref:Microsoft.Office.Interop.Word.Range> obiektu umożliwia wyszukiwanie tekstu bez wyświetlania niczego w interfejsie użytkownika. <xref:Microsoft.Office.Interop.Word.Find>Obiekt zwraca **wartość true** , jeśli znaleziono tekst pasujący do kryteriów wyszukiwania, i **wartość false** , jeśli nie. Ponadto <xref:Microsoft.Office.Interop.Word.Range> ponownie definiuje obiekt, aby pasował do kryteriów wyszukiwania po znalezieniu tekstu.

### <a name="to-find-text-using-a-range-object"></a>Aby znaleźć tekst przy użyciu obiektu zakresu

1. Zdefiniuj <xref:Microsoft.Office.Interop.Word.Range> obiekt, który składa się z akapitu drugiego w dokumencie.

    Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu.

    [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]

    Poniższy przykład kodu może być używany w dodatku VSTO. Ten przykład używa aktywnego dokumentu.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]

2. Używając <xref:Microsoft.Office.Interop.Word.Range.Find%2A> właściwości <xref:Microsoft.Office.Interop.Word.Range> obiektu, najpierw wyczyść wszystkie istniejące opcje formatowania, a następnie wyszukaj ciąg **Znajdź**.

    [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
    [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]

3. Wyświetl wyniki wyszukiwania w oknie komunikatu i wybierz opcję, <xref:Microsoft.Office.Interop.Word.Range> Aby ją wyświetlić.

    [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
    [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]

    Jeśli wyszukiwanie nie powiedzie się, zostanie wybrany drugi akapit; Jeśli to się powiedzie, zostaną wyświetlone kryteria wyszukiwania.

   Poniższy przykład pokazuje kompletny kod dla dostosowania na poziomie dokumentu. Aby użyć tego przykładu, należy uruchomić kod z `ThisDocument` klasy w projekcie.

   [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]

   Poniższy przykład pokazuje kompletny kod dodatku VSTO. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]

## <a name="search-for-and-replace-text-in-documents"></a>Wyszukiwanie i zastępowanie tekstu w dokumentach
 Poniższy kod przeszukuje bieżący wybór i zastępuje wszystkie wystąpienia ciągu **Znajdź mnie** **ciągiem.**

### <a name="to-search-for-and-replace-text-in-documents"></a>Aby wyszukać i zamienić tekst w dokumentach

1. Dodaj następujący przykładowy kod do `ThisDocument` `ThisAddIn` klasy or w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]

     <xref:Microsoft.Office.Interop.Word.Find>Klasa ma <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> metodę, a <xref:Microsoft.Office.Interop.Word.Replacement> Klasa ma także własną <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> metodę. Podczas wykonywania operacji znajdowania i zamieniania należy użyć metody ClearFormatting obu obiektów. Jeśli używasz go tylko do <xref:Microsoft.Office.Interop.Word.Find> obiektu, możesz uzyskać nieoczekiwane wyniki w tekście zastępczym.

2. Użyj <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Find> obiektu, aby zamienić każdy znaleziony element. Aby określić elementy, które mają zostać zamienione, użyj parametru *replace* . Ten parametr może mieć jedną z następujących <xref:Microsoft.Office.Interop.Word.WdReplace> wartości:

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll>zastępuje wszystkie znalezione elementy.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone>zastępuje żaden z znalezionych elementów.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne>zastępuje pierwszy znaleziony element.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane Ustawianie opcji wyszukiwania w programie Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Instrukcje: programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowane przywracanie zaznaczenia po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
