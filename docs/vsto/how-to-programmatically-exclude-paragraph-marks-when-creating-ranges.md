---
title: Wyklucz znaczniki akapitu w przypadku programistycznego tworzenia zakresów
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: fa4686acb6a806fd97a78064214c6805a4b354e9
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585200"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Instrukcje: Programowane wykluczanie znaczników akapitu podczas tworzenia zakresów
  Za każdym razem, gdy tworzysz <xref:Microsoft.Office.Interop.Word.Range> obiekt na podstawie akapitu, wszystkie znaki niedrukowalne, takie jak znaczniki akapitu, są uwzględniane w zakresie. Możesz chcieć wstawić tekst z akapitu źródłowego do akapitu docelowego. Jeśli nie chcesz podzielić akapitu docelowego na oddzielne akapity, należy najpierw usunąć znacznik akapitu z akapitu źródłowego. Ponadto, ponieważ informacje o formatowaniu akapitu są przechowywane w znaczniku akapitu, nie należy uwzględniać tego, gdy wstawisz zakres do istniejącego akapitu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Poniższa przykładowa procedura deklaruje dwie zmienne String, pobiera zawartość pierwszego i drugiego akapitu w aktywnym dokumencie, a następnie wymienia ich zawartość. W przykładzie pokazano, jak usunąć znacznik akapitu z zakresu przy użyciu <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody i wstawiając tekst w akapicie.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Aby kontrolować strukturę akapitu podczas wstawiania tekstu

1. Utwórz dwie zmienne zakresów dla pierwszych i drugich akapitów, a następnie Pobierz ich zawartość przy użyciu <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwości.

     Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]

     Poniższy przykład kodu może być używany w dodatku VSTO na poziomie aplikacji. Ten kod używa aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]

2. Przypisz <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Właściwość, zamieniając tekst między dwa akapity.

     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]

3. Zaznacz każdy zakres z kolei i Wstrzymaj, aby wyświetlić wyniki w oknie komunikatu.

     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]

4. Dostosuj `firstRange` przy użyciu <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody, aby znacznik akapitu nie był już częścią `firstRange` .

     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]

5. Zastąp resztę tekstu w pierwszym akapicie, przypisując nowy ciąg do <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Właściwości zakresu.

     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]

6. Zastąp tekst w `secondRange` , włącznie z oznaczeniem akapitu.

     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]

7. Wybierz `firstRange` i Wstrzymaj, aby wyświetlić wyniki w oknie komunikatu, a następnie wykonaj te same czynności z poleceniem `secondRange` .

     Ze względu `firstRange` na to, że zostały ponownie zdefiniowane do wykluczenia znacznika akapitu, oryginalne formatowanie akapitu zostanie zachowane. Jednak zdanie zostało wstawione nad znacznikiem akapitu w `secondRange` , usuwając odrębny akapit.

     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]

     Oryginalna zawartość obu zakresów została zapisana jako ciągi, dzięki czemu można przywrócić oryginalny warunek dokumentu.

8. Dopasowuje dopasowanie, `firstRange` Aby uwzględnić znacznik akapitu przy użyciu <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metody dla jednoznakowego położenia.

     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]

9. Usuń folder `secondRange`. Spowoduje to przywrócenie akapitu trzeciego do jego oryginalnego położenia.

     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]

10. Przywróć tekst oryginalnego akapitu w `firstRange` .

     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]

11. Użyj <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> metody <xref:Microsoft.Office.Interop.Word.Range> obiektu, aby wstawić oryginalny akapit — dwie zawartość po `firstRange` , a następnie wybierz `firstRange` .

     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Aby kontrolować strukturę akapitu podczas wstawiania tekstu w dostosowaniach na poziomie dokumentu

1. Poniższy przykład przedstawia metodę Complete dla dostosowania na poziomie dokumentu. Aby użyć tego kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]

## <a name="vsto-add-in-example"></a>Przykład dodatku narzędzi VSTO

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Aby kontrolować strukturę akapitu podczas wstawiania tekstu w dodatku narzędzi VSTO

1. Poniższy przykład przedstawia metodę Complete dla dodatku VSTO. Aby użyć tego kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane poszerzanie zakresów w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Instrukcje: programowe zwijanie zakresów lub zaznaczenia w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Instrukcje: Programowane wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Instrukcje: Programowane Resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Instrukcje: programowe Definiowanie i wybieranie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
