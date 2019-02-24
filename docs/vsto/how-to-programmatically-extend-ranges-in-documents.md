---
title: 'Instrukcje: Programowe rozszerzanie zakresów w dokumentach'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13aca5195a965fb6078be80e5fe681a49e7d4a09
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639268"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Instrukcje: Programowe rozszerzanie zakresów w dokumentach
  Po zdefiniowaniu <xref:Microsoft.Office.Interop.Word.Range> obiektów w dokumencie programu Microsoft Office Word, zmienić jego punkt początkowy i końcowy za pomocą <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> i <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody. <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> i <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody przyjmują tego samego dwa argumenty *jednostki* i *liczba*. *Liczba* argument jest liczba jednostek, aby przenieść, a *jednostki* argument może być jedną z następujących <xref:Microsoft.Office.Interop.Word.WdUnits> wartości:

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

  W poniższym przykładzie zdefiniowano zakres siedem znaków. Przenosi następnie pozycja początkowa zakresu siedem znaków, po oryginalny pozycja początkowa. Ponieważ pozycja końcowa zakresu również siedem znaków od pozycji początkowej, wynik jest zakres, który składa się z zero znaków. Kod spowoduje przesunięcie pozycji zakończenia siedem znaków po bieżącej pozycji zakończenia.

## <a name="to-extend-a-range"></a>Aby rozszerzyć zakres

1.  Zdefiniuj zakres znaków. Aby uzyskać więcej informacji, zobacz [jak: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

     Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]

     Poniższy przykład kodu może służyć w dodatku VSTO. W tym przykładzie użyto aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]

2.  Użyj <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> metody <xref:Microsoft.Office.Interop.Word.Range> przesunięcia pozycja początkowa zakresu.

     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]

3.  Użyj <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody <xref:Microsoft.Office.Interop.Word.Range> przesunięcia pozycja końcowa zakresu.

     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]

## <a name="document-level-customization-code"></a>Kod dostosowywania poziomie dokumentu

### <a name="to-extend-a-range-in-a-document-level-customization"></a>Aby rozszerzyć zakres w dostosowaniu na poziomie dokumentu

1.  Poniższy przykład pokazuje kompletny kod dla dostosowywania poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]

## <a name="vsto-add-in-code"></a>Kodu dodatku narzędzi VSTO

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Aby rozszerzyć zakres w dodatku narzędzi VSTO dla dodatku poziomu aplikacji

1.  Poniższy przykład pokazuje kompletny kod dla dodatku VSTO. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Instrukcje: Programowe zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowe pobieranie znaków początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Instrukcje: Programowe wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
