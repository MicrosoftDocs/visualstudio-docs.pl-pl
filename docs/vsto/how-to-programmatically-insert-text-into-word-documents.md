---
title: 'Instrukcje: Programowe Wstawianie tekstu w dokumentach programu Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8d5a0382726e6fc481001f4afc7820875e436594
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828920"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Instrukcje: Programowe Wstawianie tekstu w dokumentach programu Word
  Istnieją trzy podstawowe sposoby Wstawianie tekstu w dokumentach programu Microsoft Office Word:  
  
-   Wstawianie tekstu w zakresie.  
  
-   Zastąp tekst w zakresie nowego tekstu.  
  
-   Użyj <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> metody <xref:Microsoft.Office.Interop.Word.Selection> obiektu, aby wstawić tekst na kursora lub zaznaczenia.  
  
> [!NOTE]  
>  Można także wstawianie tekstu w formantach zawartości i zakładki. Aby uzyskać więcej informacji, zobacz [udostępnia mechanizmy kontroli zawartości](../vsto/content-controls.md) i [Bookmark, formant](../vsto/bookmark-control.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="insert-text-in-a-range"></a>Wstawianie tekstu w zakresie  
 Użyj <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwość <xref:Microsoft.Office.Interop.Word.Range> obiektu umożliwia wstawianie tekstu w dokumencie.  
  
### <a name="to-insert-text-in-a-range"></a>Umożliwia wstawianie tekstu w zakresie  
  
1.  Określ zakres na początku dokumentu, a następnie wstawianie tekstu **nowy tekst**.  
  
     Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomation#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#51)]  
  
     Poniższy przykład kodu może służyć w dodatku VSTO. Ten kod używa aktywnego dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#51)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#51](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#51)]  
  
2.  Wybierz <xref:Microsoft.Office.Interop.Word.Range> obiektu, który zostały rozwinięte z jednego znaku i długość wstawionego tekstu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#52)]
     [!code-csharp[Trin_VstcoreWordAutomation#52](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#52)]  
  
## <a name="replace-text-in-a-range"></a>Zastępowanie tekstu w zakresie  
 Jeśli określony zakres zawiera tekst, cały tekst w zakresie jest zastępowany wstawionego tekstu.  
  
### <a name="to-replace-text-in-a-range"></a>Aby zamienić tekst w zakresie  
  
1.  Utwórz <xref:Microsoft.Office.Interop.Word.Range> obiekt, który składa się z pierwszych 12 znaków w dokumencie.  
  
     Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomation#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#53)]  
  
     Poniższy przykład kodu może służyć w dodatku VSTO. Ten kod używa aktywnego dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#53)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#53](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#53)]  
  
2.  Zastąp te znaki ciągu **nowy tekst**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#54)]
     [!code-csharp[Trin_VstcoreWordAutomation#54](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#54)]  
  
3.  Wybierz zakres.  
  
     [!code-vb[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#55)]
     [!code-csharp[Trin_VstcoreWordAutomation#55](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#55)]  
  
## <a name="insert-text-using-typetext"></a>Wstaw tekst za pomocą TypeText  
 <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> Metoda wstawia tekst na wybór. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> zachowuje się inaczej w zależności od opcji ustawione na komputerze użytkownika. Kod w poniższej procedurze deklaruje <xref:Microsoft.Office.Interop.Word.Selection> zmiennej obiektu i wyłącza **zastępowania** opcję, jeśli jest włączona. Jeśli **zastępowania** opcja jest aktywna, a następnie dowolny tekst, obok kursor zostanie zastąpiony.  
  
### <a name="to-insert-text-using-the-typetext-method"></a>Aby wstawić tekst przy użyciu metody TypeText  
  
1. Zadeklaruj <xref:Microsoft.Office.Interop.Word.Selection> zmiennej obiektu.  
  
    [!code-vb[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#57)]
    [!code-csharp[Trin_VstcoreWordAutomation#57](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#57)]  
  
2. Wyłącz **zastępowania** opcję, jeśli jest włączona.  
  
    [!code-vb[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#58)]
    [!code-csharp[Trin_VstcoreWordAutomation#58](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#58)]  
  
3. Sprawdź, czy bieżące zaznaczenie jest punkt wstawiania.  
  
    Jeśli tak jest, kod wstawia zdania przy użyciu <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>i następnie akapitu znacznik using <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> metody.  
  
    [!code-vb[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#59)]
    [!code-csharp[Trin_VstcoreWordAutomation#59](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#59)]  
  
4. Kod w **ElseIf** block testy, aby zobaczyć, czy zaznaczenie jest zaznaczeniem normalny. Jeśli tak jest, następnie inne **Jeśli** block testy, aby zobaczyć, czy **ReplaceSelection** opcja jest włączona. Jeśli tak jest, kod używa <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> Metoda wyboru, aby zwinąć zaznaczenie do punktu wstawiania na początku bloku zaznaczonego tekstu. Wstaw tekst i znacznik akapitu.  
  
    [!code-vb[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#60)]
    [!code-csharp[Trin_VstcoreWordAutomation#60](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#60)]  
  
5. Jeśli zaznaczenie nie znajduje się punkt wstawiania lub blok zaznaczonego tekstu, a następnie kod w **Else** bloku nic nie robi.  
  
    [!code-vb[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#61)]
    [!code-csharp[Trin_VstcoreWordAutomation#61](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#61)]  
  
   Można również użyć <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> metody <xref:Microsoft.Office.Interop.Word.Selection> obiektu, który naśladuje funkcjonalność **Backspace** kluczowe na klawiaturze. Jednakże, jeśli chodzi o wstawiania i manipulowania tekstem, <xref:Microsoft.Office.Interop.Word.Range> obiektu oferuje większą kontrolę.  
  
   Poniższy przykład pokazuje kompletny kod. Aby użyć tego przykładu, należy uruchomić kod z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
   [!code-vb[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#56)]
   [!code-csharp[Trin_VstcoreWordAutomation#56](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#56)]  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Programowe formatowanie tekstu w dokumentach](../vsto/how-to-programmatically-format-text-in-documents.md)   
 [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Instrukcje: Programowe rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)  
