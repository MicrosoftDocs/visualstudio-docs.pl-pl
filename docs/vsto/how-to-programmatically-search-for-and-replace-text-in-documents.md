---
title: Programowe znajdowanie i zastępowanie tekstu w dokumentach
description: Dowiedz się, jak używać Visual Studio do programowego wyszukiwania i zastępowania tekstu w dokumencie programu Microsoft Word.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0f2fc5bbfabbe2672ae59c55734a5cf57fc84318
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825163"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>How to: Programowe wyszukiwanie i zastępowanie tekstu w dokumentach
  Obiekt jest członkiem obiektów i można użyć jednego z nich do wyszukiwania tekstu w Microsoft Office <xref:Microsoft.Office.Interop.Word.Find> <xref:Microsoft.Office.Interop.Word.Selection> programu <xref:Microsoft.Office.Interop.Word.Range> Word. Zastąpić polecenie jest rozszerzeniem znaleźć polecenia.

 Obiekt w pętli przechodzi przez Microsoft Office programu Word, wyszukuje określony tekst, formatowanie lub styl, a następnie używa właściwości , aby zastąpić dowolny z <xref:Microsoft.Office.Interop.Word.Find> <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> znalezionych elementów.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Używanie obiektu Selection
 W przypadku wyszukiwania tekstu przy użyciu obiektu wszystkie określone kryteria wyszukiwania są stosowane tylko do <xref:Microsoft.Office.Interop.Word.Selection> aktualnie zaznaczonego tekstu. Jeśli element <xref:Microsoft.Office.Interop.Word.Selection> jest punktem wstawiania, dokument zostanie przeszukany. W przypadku wyszukiwania elementu, który spełnia kryteria wyszukiwania, zostanie on automatycznie wybrany.

 Należy pamiętać, że kryteria kumulują się, co oznacza, że <xref:Microsoft.Office.Interop.Word.Find> kryteria są dodawane do poprzednich kryteriów wyszukiwania. Wyczyść formatowanie z poprzednich wyszukiwań przy <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> użyciu metody przed wyszukiwaniem.

### <a name="to-find-text-using-a-selection-object"></a>Aby znaleźć tekst przy użyciu obiektu Selection

1. Przypisz ciąg wyszukiwania do zmiennej.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet68":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet68":::

2. Wyczyść formatowanie z poprzednich wyszukiwań.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet69":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet69":::

3. Wykonaj wyszukiwanie i wyświetl okno komunikatu z wynikami.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet70":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet70":::

   W poniższym przykładzie przedstawiono metodę complete.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet67":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet67":::

## <a name="use-a-range-object"></a>Używanie obiektu Range
 Użycie obiektu <xref:Microsoft.Office.Interop.Word.Range> umożliwia wyszukiwanie tekstu bez wyświetlania czegokolwiek w interfejsie użytkownika. Jeśli zostanie znaleziony tekst, który spełnia kryteria wyszukiwania, obiekt zwraca wartość True, a wartość <xref:Microsoft.Office.Interop.Word.Find> **False,**  jeśli nie. Ponadto obiekt jest ponownie <xref:Microsoft.Office.Interop.Word.Range> definiowany w celu dopasowania go do kryteriów wyszukiwania, jeśli zostanie znaleziony tekst.

### <a name="to-find-text-using-a-range-object"></a>Aby znaleźć tekst przy użyciu obiektu Range

1. <xref:Microsoft.Office.Interop.Word.Range>Zdefiniuj obiekt, który składa się z drugiego akapitu w dokumencie.

    Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet72":::

    Poniższy przykład kodu może być używany w dodatku VSTO. W tym przykładzie jest używany aktywny dokument.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet72":::

2. Używając właściwości obiektu , najpierw wyczyść wszystkie istniejące opcje formatowania, a następnie wyszukaj <xref:Microsoft.Office.Interop.Word.Range.Find%2A> <xref:Microsoft.Office.Interop.Word.Range> ciąg znajdź **mnie**.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet73":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet73":::

3. Wyświetl wyniki wyszukiwania w oknie komunikatu, a następnie wybierz pozycję , <xref:Microsoft.Office.Interop.Word.Range> aby była widoczna.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet74":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet74":::

    Jeśli wyszukiwanie nie powiedzie się, zostanie wybrany drugi akapit; Jeśli to się powiedzie, zostaną wyświetlone kryteria wyszukiwania.

   W poniższym przykładzie pokazano pełny kod dostosowywania na poziomie dokumentu. Aby użyć tego przykładu, uruchom kod z `ThisDocument` klasy w projekcie.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet71":::

   W poniższym przykładzie pokazano pełny kod dodatku VSTO. Aby użyć tego przykładu, uruchom kod z `ThisAddIn` klasy w projekcie.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet71":::

## <a name="search-for-and-replace-text-in-documents"></a>Wyszukiwanie i zastępowanie tekstu w dokumentach
 Poniższy kod wyszukuje bieżący wybór i zastępuje wszystkie wystąpienia ciągu **znajdź mnie** ciągiem **Znaleziono**.

### <a name="to-search-for-and-replace-text-in-documents"></a>Aby wyszukać i zamienić tekst w dokumentach

1. Dodaj następujący przykładowy kod do `ThisDocument` klasy lub `ThisAddIn` w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet75":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet75":::

     Klasa <xref:Microsoft.Office.Interop.Word.Find> ma metodę , a klasa ma również własną <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> <xref:Microsoft.Office.Interop.Word.Replacement> <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> metodę. Podczas wykonywania operacji znajdowania i zamieniania należy użyć metody ClearFormatting obu obiektów. Jeśli używasz go tylko w obiekcie , możesz uzyskać nieprzewidziane <xref:Microsoft.Office.Interop.Word.Find> wyniki w tekście zastępczym.

2. Użyj <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody obiektu <xref:Microsoft.Office.Interop.Word.Find> , aby zastąpić każdy znaleziony element. Aby określić, które elementy zastąpić, użyj *zastąpić parametru.* Ten parametr może być jedną z następujących <xref:Microsoft.Office.Interop.Word.WdReplace> wartości:

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> Zastępuje wszystkie znalezione elementy.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> Nie zastępuje żadnego z znalezionych elementów.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> zastępuje pierwszy znaleziony element.

## <a name="see-also"></a>Zobacz też
- [How to: Programowe ustawianie opcji wyszukiwania w programie Word](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [How to: Programmatically loop through found items in documents ( Jak programowo przechodzić w pętli przez znalezione elementy w dokumentach)](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [How to: Programmatically restore selections after searches (2. Tworzyć programowe przywracanie zaznaczenia po wyszukiwaniu)](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
