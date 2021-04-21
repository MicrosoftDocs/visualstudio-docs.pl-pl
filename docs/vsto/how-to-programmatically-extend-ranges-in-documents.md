---
title: 'Pisano: Programowe rozszerzanie zakresów w dokumentach'
description: Dowiedz się, jak programowo rozszerzyć zakresy punktów startowych i końcowych w dokumencie programu Microsoft Word na poziomie dokumentu lub aplikacji.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7a539bbbc4ad8d73477e660ef9903ac51dce712f
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826528"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Pisano: Programowe rozszerzanie zakresów w dokumentach
  Po zdefiniowaniu obiektu w dokumencie programu Microsoft Office Word można zmienić jego punkt rozpoczęcia i punkt końcowy przy <xref:Microsoft.Office.Interop.Word.Range> użyciu metod <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> i <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . Metody <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> i mają te same dwa <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> argumenty: *Unit* (Jednostka) i *Count (Liczba).* Argument *Count* jest liczbą jednostek do przeniesienia, a argument *Unit* może być jedną z następujących <xref:Microsoft.Office.Interop.Word.WdUnits> wartości:

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  W poniższym przykładzie zdefiniowano zakres siedmiu znaków. Następnie przenosi pozycję początku zakresu siedmiu znaków po oryginalnej pozycji rozpoczęcia. Ponieważ pozycja końcowa zakresu również miała siedem znaków po pozycji startowej, wynik jest zakresem, który składa się z zera znaków. Następnie kod przenosi pozycję końcową siedem znaków po bieżącej pozycji końcowej.

## <a name="to-extend-a-range"></a>Aby rozszerzyć zakres

1. Zdefiniuj zakres znaków. Aby uzyskać więcej informacji, [zobacz How to: Programmatically define and select ranges in documents (Jak programowo definiować i wybierać zakresy w dokumentach).](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)

     Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet39":::

     Poniższy przykład kodu może być używany w dodatku VSTO. W tym przykładzie jest używany aktywny dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet39":::

2. Użyj <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> metody obiektu <xref:Microsoft.Office.Interop.Word.Range> , aby przenieść pozycję rozpoczęcia zakresu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet40":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet40":::

3. Użyj <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody obiektu <xref:Microsoft.Office.Interop.Word.Range> , aby przenieść końcową pozycję zakresu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet41":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet41":::

## <a name="document-level-customization-code"></a>Kod dostosowywania na poziomie dokumentu

### <a name="to-extend-a-range-in-a-document-level-customization"></a>Aby rozszerzyć zakres w dostosowywaniu na poziomie dokumentu

1. W poniższym przykładzie pokazano kompletny kod dostosowywania na poziomie dokumentu. Aby użyć tego kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet38":::

## <a name="vsto-add-in-code"></a>Kod dodatku VSTO

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Aby rozszerzyć zakres w dodatku VSTO na poziomie aplikacji

1. W poniższym przykładzie pokazano pełny kod dodatku VSTO. Aby użyć tego kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet38":::

## <a name="see-also"></a>Zobacz też
- [How to: Programowe resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [How to: Programowe zwijanie zakresów lub wyborów w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [How to: Programowe pobieranie znaków początku i końca w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Dzieje się tak: Programowe wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
