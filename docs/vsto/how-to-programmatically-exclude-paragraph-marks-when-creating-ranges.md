---
title: Wykluczanie znaczników akapitu podczas tworzenia zakresów programowe
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 852dc6c51215e00c1fdc1571f51940a44f727794
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402142"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Instrukcje: Programowe wykluczanie znaczników akapitu podczas tworzenia zakresów
  Zawsze, gdy tworzysz <xref:Microsoft.Office.Interop.Word.Range> obiektu w oparciu akapitu, wszystkie znaki niedrukowane, takie jak znaczniki akapitu, znajdują się w zakresie. Możesz wstawić tekst z akapitu źródła do docelowego akapitu. Jeśli chcesz podzielić akapit docelowy na oddzielnych akapitów, następnie należy najpierw usunąć znak z akapitu źródła. Ponadto ponieważ informacje o formatowaniu akapitu są przechowywane w ramach znak, nie można uwzględniać, to podczas wstawiania zakresu do istniejącego akapitu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Poniższej przykładowej procedurze deklaruje dwie zmienne ciągu, pobiera zawartość akapitów pierwszego i drugiego w aktywnym dokumencie, a następnie zamienia ich zawartość. W przykładzie pokazano następnie usuwanie znaczników akapitu z zakresu przy użyciu <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody i wstawianie tekstu akapitu.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Aby kontrolować struktury akapitu podczas wstawiania tekstu

1. Utwórz dwie zmienne zakresu akapitów pierwszego i drugiego, a następnie pobrać ich zawartość przy użyciu <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwości.

     Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]

     Poniższy przykład kodu może służyć w dodatku narzędzi VSTO dla dodatku poziomu aplikacji. Ten kod używa aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]

2. Przypisz <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwość, zamiana tekstu między dwoma akapitami.

     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]

3. Z kolei wybierz każdy z zakresów, a następnie Wstrzymaj, aby wyświetlić wyniki w oknie komunikatu.

     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]

4. Dostosuj `firstRange` przy użyciu <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody, aby znaczników akapitu nie jest już częścią `firstRange`.

     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]

5. Zastąp pozostały tekst w pierwszym akapicie, przypisując nowy ciąg do <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwości zakresu.

     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]

6. Zastąp tekst umieszczony w `secondRange`, wraz ze znacznikiem.

     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]

7. Wybierz `firstRange` i Wstrzymaj, aby wyświetlić wyniki w oknie komunikatu, a następnie wykonaj taki sam jak `secondRange`.

     Ponieważ `firstRange` zostało ponownie zdefiniowane Aby wykluczyć znak akapitu, oryginalnym formatowanie akapitu są zachowywane. Jednak zdania został wstawiony przez znak akapitu w `secondRange`, usuwając oddzielny akapit.

     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]

     Oryginalną zawartość obu zakresów zostały zapisane jako ciągi, dzięki czemu można przywrócić go do stanu.

8. Dopasuj `firstRange` dołączenie znak za pomocą <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metodę dla jednego znaku na pozycji.

     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]

9. Usuń folder `secondRange`. Spowoduje to przywrócenie akapitu trzy do swojego pierwotnego położenia.

     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]

10. Przywrócić oryginalny tekst akapitu w `firstRange`.

     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]

11. Użyj <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiekt do wstawienia pierwotną wersją zawartości dwóch akapitu po `firstRange`, a następnie wybierz pozycję `firstRange`.

     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]

## <a name="document-level-customization-example"></a>Przykład dostosowania na poziomie dokumentu

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Do kontrolowania struktury akapitu po Wstawianie tekstu w dostosowaniach na poziomie dokumentu

1. Poniższy przykład pokazuje całą metodę dla dostosowywania poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]

## <a name="vsto-add-in-example"></a>Przykładu dodatku narzędzi VSTO

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Do kontrolowania struktury akapitu po Wstawianie tekstu w dodatku narzędzi VSTO

1. Poniższy przykład pokazuje całą metodę dla dodatku VSTO. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe rozszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Instrukcje: Programowe zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Instrukcje: Programowe Wstawianie tekstu w dokumentach programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Instrukcje: Programowe Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
