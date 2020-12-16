---
title: 'Instrukcje: Programowane wstawianie tekstu do dokumentów programu Word'
description: Dowiedz się, jak programowo wstawić tekst do dokumentu programu Microsoft Word przy użyciu programu Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9567ea197c9a181141aeb52db0cca56ad4776237
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525683"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Instrukcje: Programowane wstawianie tekstu do dokumentów programu Word
  Istnieją trzy podstawowe sposoby wstawiania tekstu do Microsoft Office dokumentów programu Word:

- Wstaw tekst do zakresu.

- Zastąp tekst w zakresie nowym tekstem.

- Użyj <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> metody <xref:Microsoft.Office.Interop.Word.Selection> obiektu, aby wstawić tekst do kursora lub zaznaczenia.

> [!NOTE]
> Możesz również wstawić tekst do kontrolek zawartości i zakładek. Aby uzyskać więcej informacji, zobacz [kontrolki zawartości](../vsto/content-controls.md) i [kontrolka zakładka](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>Wstaw tekst do zakresu
 Użyj <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwości <xref:Microsoft.Office.Interop.Word.Range> obiektu, aby wstawić tekst do dokumentu.

### <a name="to-insert-text-in-a-range"></a>Aby wstawić tekst do zakresu

1. Określ zakres na początku dokumentu i Wstaw tekst **Nowy tekst**.

     Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]

     Poniższy przykład kodu może być używany w dodatku VSTO. Ten kod używa aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]

2. Wybierz <xref:Microsoft.Office.Interop.Word.Range> obiekt, który rozwinięto z jednego znaku na długość wstawionego tekstu.

     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]

## <a name="replace-text-in-a-range"></a>Zastąp tekst w zakresie
 Jeśli określony zakres zawiera tekst, cały tekst w zakresie zostanie zastąpiony wstawionym tekstem.

### <a name="to-replace-text-in-a-range"></a>Aby zamienić tekst w zakresie

1. Utwórz <xref:Microsoft.Office.Interop.Word.Range> obiekt, który składa się z pierwszych 12 znaków w dokumencie.

     Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]

     Poniższy przykład kodu może być używany w dodatku VSTO. Ten kod używa aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]

2. Zamień te znaki na ciąg **New Text**.

     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]

3. Wybierz zakres.

     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]

## <a name="insert-text-using-typetext"></a>Wstawianie tekstu przy użyciu TypeText
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>Metoda wstawia tekst w zaznaczeniu. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> działa inaczej w zależności od opcji ustawionych na komputerze użytkownika. Kod w poniższej procedurze deklaruje <xref:Microsoft.Office.Interop.Word.Selection> zmienną obiektu i wyłącza opcję **zastępowania** , jeśli jest włączona. Jeśli opcja **zastępowania** została aktywowana, każdy tekst obok kursora zostanie nadpisany.

### <a name="to-insert-text-using-the-typetext-method"></a>Aby wstawić tekst przy użyciu metody TypeText

1. Zadeklaruj <xref:Microsoft.Office.Interop.Word.Selection> zmienną obiektu.

    [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
    [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]

2. Wyłącz opcję **zastępowania** , jeśli jest włączona.

    [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
    [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]

3. Przetestuj, aby sprawdzić, czy bieżący wybór jest punktem wstawiania.

    Jeśli tak, kod wstawia zdania przy użyciu <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> , a następnie znacznik akapitu przy użyciu <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> metody.

    [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
    [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]

4. Kod w bloku **ElseIf** testuje, aby zobaczyć, czy zaznaczenie jest normalnym wyborem. Jeśli tak jest, kolejną opcją, **Jeśli** blokuje testy, aby sprawdzić, czy opcja **ReplaceSelection** jest włączona. Jeśli tak, kod używa <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> metody wyboru, aby zwinąć zaznaczenie do punktu wstawiania na początku zaznaczonego bloku tekstu. Wstaw tekst i znacznik akapitu.

    [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
    [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]

5. Jeśli zaznaczenie nie jest punktem wstawiania ani blokiem zaznaczonego tekstu, kod w bloku **else** nie robi nic.

    [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
    [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]

   Można również użyć <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> metody <xref:Microsoft.Office.Interop.Word.Selection> obiektu, który naśladuje funkcjonalność klawisza **Backspace** na klawiaturze. Jednak w przypadku wstawiania i manipulowania tekstem <xref:Microsoft.Office.Interop.Word.Range> obiekt oferuje większą kontrolę.

   Poniższy przykład pokazuje kompletny kod. Aby użyć tego przykładu, należy uruchomić kod z `ThisDocument` `ThisAddIn` klasy lub w projekcie.

   [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
   [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane formatowanie tekstu w dokumentach](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Instrukcje: Programowane poszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
