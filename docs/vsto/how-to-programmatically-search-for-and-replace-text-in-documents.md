---
title: 'Instrukcje: Programowe wyszukiwanie i zastępowanie tekstu w dokumentach'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ccd9fc41ce0be5aa209098dd574f142b22ad2996
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53823678"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Instrukcje: Programowe wyszukiwanie i zastępowanie tekstu w dokumentach
  <xref:Microsoft.Office.Interop.Word.Find> Obiektu jest elementem członkowskim obu <xref:Microsoft.Office.Interop.Word.Selection> i <xref:Microsoft.Office.Interop.Word.Range> obiektów i możesz użyć dowolnego z nich do wyszukiwania tekstu w dokumentach programu Microsoft Office Word. Polecenie replace jest rozszerzeniem polecenie find.  
  
 Użyj <xref:Microsoft.Office.Interop.Word.Find> obiektu pętli dokumentu Microsoft Office Word i wyszukać określonego tekstu, formatowanie lub styl, a następnie użyj <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> właściwości w celu zastąpienia wszystkich elementów, znaleziono.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="use-a-selection-object"></a>Użyj obiektu zaznaczenia  
 Kiedy używasz <xref:Microsoft.Office.Interop.Word.Selection> obiektu do znalezienia tekstu, dowolne wyszukiwanie określone kryteria są stosowane wyłącznie w odniesieniu do aktualnie zaznaczonego tekstu. Jeśli <xref:Microsoft.Office.Interop.Word.Selection> jest punkt wstawiania, a następnie przeszukiwany jest dokumentu. Gdy element zostanie znaleziony, który jest zgodny z kryteriami wyszukiwania, automatycznie wybrano.  
  
 Ważne jest, aby pamiętać, że <xref:Microsoft.Office.Interop.Word.Find> kryteria kumulują, co oznacza, że kryteria są dodawane do poprzednich kryteria wyszukiwania. Wyczyść formatowanie poprzednich wyników wyszukiwania za pomocą <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> metoda przed wyszukiwania.  
  
### <a name="to-find-text-using-a-selection-object"></a>Aby wyszukać tekst za pomocą obiektu zaznaczenia  
  
1. Ciąg wyszukiwania można przypisać do zmiennej.  
  
    [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
    [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]  
  
2. Wyczyść formatowanie z poprzednich wyników wyszukiwania.  
  
    [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
    [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]  
  
3. Wykonaj wyszukiwanie i wyświetlić okno komunikatu z wynikami.  
  
    [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
    [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]  
  
   Poniższy przykład pokazuje całą metodę.  
  
   [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
   [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]  
  
## <a name="use-a-range-object"></a>Użyj obiektu zakresu  
 Za pomocą <xref:Microsoft.Office.Interop.Word.Range> obiekt umożliwia wyszukiwanie tekstu bez wyświetlania niczego w interfejsie użytkownika. <xref:Microsoft.Office.Interop.Word.Find> Zwraca obiekt **True** Jeśli zostanie znaleziony tekst, który pasuje do kryteriów wyszukiwania i **False** Jeśli tak nie jest. Również redefiniuje <xref:Microsoft.Office.Interop.Word.Range> obiekt do pasujących do kryteriów wyszukiwania, jeśli zostanie znaleziony tekst.  
  
### <a name="to-find-text-using-a-range-object"></a>Aby znaleźć tekstu przy użyciu obiektu zakresu  
  
1. Zdefiniuj <xref:Microsoft.Office.Interop.Word.Range> obiekt, który składa się z drugim akapit w dokumencie.  
  
    Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu.  
  
    [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]  
  
    Poniższy przykład kodu może służyć w dodatku VSTO. W tym przykładzie użyto aktywnego dokumentu.  
  
    [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]  
  
2. Za pomocą <xref:Microsoft.Office.Interop.Word.Range.Find%2A> właściwość <xref:Microsoft.Office.Interop.Word.Range> obiektu, najpierw usuń wszystkie istniejące opcje formatowania i następnie wyszukaj ciąg **mnie znaleźć**.  
  
    [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
    [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]  
  
3. Wyświetl wyniki wyszukiwania w oknie komunikatu, a następnie wybierz pozycję <xref:Microsoft.Office.Interop.Word.Range> aby była widoczna.  
  
    [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
    [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]  
  
    Jeśli wyszukiwanie zakończy się niepowodzeniem, jest zaznaczone, akapit. Jeśli się powiedzie, kryteria wyszukiwania są wyświetlane.  
  
   Poniższy przykład pokazuje kompletny kod dla dostosowywania poziomie dokumentu. Aby użyć tego przykładu, należy uruchomić kod z `ThisDocument` klasy w projekcie.  
  
   [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]  
  
   Poniższy przykład pokazuje kompletny kod dla dodatku VSTO. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
   [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]  
  
## <a name="search-for-and-replace-text-in-documents"></a>Wyszukiwanie i zastępowanie tekstu w dokumentach  
 Poniższy kod wyszukuje w bieżącym zaznaczeniu i zamienia wszystkie wystąpienia ciągu **mnie znaleźć** parametrami **znaleziono**.  
  
### <a name="to-search-for-and-replace-text-in-documents"></a>Wyszukiwanie i zastępowanie tekstu w dokumentach  
  
1.  Dodaj następujący kod przykładowy w celu `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]  
  
     <xref:Microsoft.Office.Interop.Word.Find> Klasa ma <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> metody i <xref:Microsoft.Office.Interop.Word.Replacement> klasa ma również swój własny <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A> metody. Podczas przeprowadzania operacji znajdowania i zamieniania, należy użyć metody ClearFormatting obu obiektów. Jeśli jest ona używana tylko na <xref:Microsoft.Office.Interop.Word.Find> obiektu, możesz otrzymać nieprzewidziane wyniki w tekst zastępczy.  
  
2.  Użyj <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Find> obiektu w celu zastąpienia każdego znalezionego elementu. Aby określić elementy, które można zastąpić, użyj *Zastąp* parametru. Ten parametr może być jedną z następujących <xref:Microsoft.Office.Interop.Word.WdReplace> wartości:  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> Zamienia wszystkie znalezione elementy.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> zastępuje brak znalezione elementy.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> zastępuje pierwszego znalezionego elementu.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Programowe Ustawianie opcji wyszukiwania w programie Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Instrukcje: Programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Instrukcje: Programowe Przywracanie zaznaczenia po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
