---
title: 'How to: Programowe wstawianie tekstu do dokumentów programu Word'
description: Dowiedz się, jak programowo wstawiać tekst do dokumentu programu Microsoft Word przy użyciu Visual Studio.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f17828b4617f84cb104761918787b4bbb79f7afc
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827360"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>How to: Programowe wstawianie tekstu do dokumentów programu Word
  Istnieją trzy podstawowe sposoby wstawiania tekstu do dokumentów Microsoft Office Word:

- Wstaw tekst w zakresie.

- Zastąp tekst w zakresie nowym tekstem.

- Użyj <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> metody obiektu <xref:Microsoft.Office.Interop.Word.Selection> , aby wstawić tekst do kursora lub zaznaczenia.

> [!NOTE]
> Możesz również wstawić tekst do kontrolek zawartości i zakładek. Aby uzyskać więcej informacji, zobacz [Kontrolki zawartości i](../vsto/content-controls.md) [Kontrolka zakładki](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>Wstawianie tekstu w zakresie
 Użyj właściwości <xref:Microsoft.Office.Interop.Word.Range.Text%2A> obiektu <xref:Microsoft.Office.Interop.Word.Range> , aby wstawić tekst do dokumentu.

### <a name="to-insert-text-in-a-range"></a>Aby wstawić tekst do zakresu

1. Określ zakres na początku dokumentu i wstaw tekst **Nowy tekst**.

     Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet51":::

     Poniższy przykład kodu może być używany w dodatku VSTO. Ten kod używa aktywnego dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet51":::

2. Wybierz <xref:Microsoft.Office.Interop.Word.Range> obiekt, który został rozwinięty z jednego znaku na długość wstawionego tekstu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet52":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet52":::

## <a name="replace-text-in-a-range"></a>Zastępowanie tekstu w zakresie
 Jeśli określony zakres zawiera tekst, cały tekst z zakresu jest zastępowany wstawionego tekstu.

### <a name="to-replace-text-in-a-range"></a>Aby zastąpić tekst w zakresie

1. Utwórz <xref:Microsoft.Office.Interop.Word.Range> obiekt, który składa się z pierwszych 12 znaków w dokumencie.

     Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet53":::

     Poniższy przykład kodu może być używany w dodatku VSTO. Ten kod używa aktywnego dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet53":::

2. Zastąp te znaki ciągiem **New Text**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet54":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet54":::

3. Wybierz zakres.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet55":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet55":::

## <a name="insert-text-using-typetext"></a>Wstawianie tekstu przy użyciu funkcji TypeText
 Metoda <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> wstawia tekst po zaznaczeniu. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> Działa inaczej w zależności od opcji ustawionych na komputerze użytkownika. Kod w poniższej procedurze deklaruje zmienną obiektu i wyłącza opcję <xref:Microsoft.Office.Interop.Word.Selection> **Overtype,** jeśli jest włączona. Jeśli opcja **Overtype** zostanie aktywowana, dowolny tekst obok kursora zostanie zastąpiony.

### <a name="to-insert-text-using-the-typetext-method"></a>Aby wstawić tekst przy użyciu metody TypeText

1. <xref:Microsoft.Office.Interop.Word.Selection>Zadeklaruj zmienną obiektu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet57":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet57":::

2. Wyłącz opcję **Overtype (Typ** zastępowania), jeśli jest włączona.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet58":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet58":::

3. Przetestuj, aby sprawdzić, czy bieżący wybór jest punktem wstawiania.

    Jeśli tak jest, kod wstawia zdanie przy użyciu <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> metody , a następnie znak <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> akapitu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet59":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet59":::

4. Kod w bloku **ElseIf** sprawdza, czy wybór jest zwykłym wyborem. Jeśli tak, to inny test **If** block, aby sprawdzić, czy **opcja ReplaceSelection** jest włączona. Jeśli tak jest, kod używa metody zaznaczenia, aby zwinąć zaznaczenie do punktu wstawiania na początku <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> wybranego bloku tekstu. Wstaw tekst i znacznik akapitu.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet60":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet60":::

5. Jeśli zaznaczenie nie jest punktem wstawiania ani blokiem zaznaczonego tekstu, kod w bloku **Else** nic nie robi.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet61":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet61":::

   Możesz również użyć metody obiektu , która naśladuje funkcjonalność <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> <xref:Microsoft.Office.Interop.Word.Selection> **klawisza Backspace** na klawiaturze. Jednak jeśli chodzi o wstawianie tekstu i manipulowanie nim, <xref:Microsoft.Office.Interop.Word.Range> obiekt oferuje większą kontrolę.

   Poniższy przykład przedstawia kompletny kod. Aby użyć tego przykładu, uruchom kod z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet56":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet56":::

## <a name="see-also"></a>Zobacz też
- [Jak programowo sformatować tekst w dokumentach](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Jak programowo rozszerzyć zakresy w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
