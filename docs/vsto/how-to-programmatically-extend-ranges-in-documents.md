---
title: 'Instrukcje: Programowane poszerzanie zakresów w dokumentach'
description: Dowiedz się, jak programowo zwiększyć zakres początkowy i punkt końcowy w dokumencie programu Microsoft Word na poziomie dokumentu lub na poziomie aplikacji.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 61ed056b5cebcebb6fe2dffd66dc374e4e1f9205
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525745"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Instrukcje: Programowane poszerzanie zakresów w dokumentach
  Po zdefiniowaniu <xref:Microsoft.Office.Interop.Word.Range> obiektu w Microsoft Office dokumencie programu Word można zmienić jego początkową i końcową punkty za pomocą <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> metod i <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A>Metody i <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> przyjmują te same dwa argumenty, *jednostkę* i *liczbę*. Argument *Count* to liczba jednostek do przeniesienia, a argument *Unit* może być jedną z następujących <xref:Microsoft.Office.Interop.Word.WdUnits> wartości:

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

  Poniższy przykład definiuje zakres siedmiu znaków. Następnie przenosi początkową pozycję zakresu siedem znaków po oryginalnej pozycji początkowej. Ponieważ Pozycja końcowa zakresu była również siedem znaków po pozycji początkowej, wynik jest zakresem zawierającym zero znaków. Następnie kod przenosi koniec siedmiu znaków po bieżącej pozycji końcowej.

## <a name="to-extend-a-range"></a>Aby rozwinąć zakres

1. Zdefiniuj zakres znaków. Aby uzyskać więcej informacji, zobacz [How to: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

     Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomation#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#39)]

     Poniższy przykład kodu może być używany w dodatku VSTO. Ten przykład używa aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#39)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#39](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#39)]

2. Użyj <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiektu, aby przenieść pozycję początkową zakresu.

     [!code-vb[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#40)]
     [!code-csharp[Trin_VstcoreWordAutomation#40](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#40)]

3. Użyj <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiektu, aby przenieść pozycję końca zakresu.

     [!code-vb[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#41)]
     [!code-csharp[Trin_VstcoreWordAutomation#41](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#41)]

## <a name="document-level-customization-code"></a>Kod dostosowania na poziomie dokumentu

### <a name="to-extend-a-range-in-a-document-level-customization"></a>Aby zwiększyć zakres w dostosowaniu na poziomie dokumentu

1. Poniższy przykład pokazuje kompletny kod dla dostosowania na poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomation#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#38)]

## <a name="vsto-add-in-code"></a>Kod dodatku narzędzi VSTO

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Aby rozwinąć zakres w dodatku VSTO na poziomie aplikacji

1. Poniższy przykład pokazuje kompletny kod dodatku VSTO. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#38)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#38](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#38)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Instrukcje: programowe zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: programowe pobieranie znaków początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Instrukcje: Programowane wykluczanie znaczników akapitu podczas tworzenia zakresów](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
