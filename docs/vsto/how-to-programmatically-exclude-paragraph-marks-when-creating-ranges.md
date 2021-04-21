---
title: Wykluczanie znaczników akapitu podczas programowego tworzenia zakresów
description: Dowiedz się, jak programowo wykluczać znaczniki akapitu podczas tworzenia zakresów w dokumencie programu Microsoft Word.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c0929ccf3bb2567099dc7f3b795ad2257da0edb3
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825800"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Dzieje się tak: Programowe wykluczanie znaczników akapitu podczas tworzenia zakresów
  Za każdym razem, gdy tworzysz obiekt na podstawie akapitu, wszystkie znaki bez drukowania, takie jak znaczniki akapitu, są <xref:Microsoft.Office.Interop.Word.Range> uwzględniane w zakresie. Możesz wstawić tekst z akapitu źródłowego do akapitu docelowego. Jeśli nie chcesz dzielić akapitu docelowego na oddzielne akapity, musisz najpierw usunąć znacznik akapitu ze źródłowego akapitu. Ponadto, ponieważ informacje o formatowaniu akapitu są przechowywane w znaczniku akapitu, możesz nie chcieć uwzględnić go podczas wstawiania zakresu do istniejącego akapitu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Następująca przykładowa procedura deklaruje dwie zmienne ciągu, pobiera zawartość pierwszego i drugiego akapitu w aktywnym dokumencie, a następnie wymienia ich zawartość. Następnie w przykładzie pokazano usuwanie znacznika akapitu z zakresu przy użyciu metody i wstawianie <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> tekstu wewnątrz akapitu.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Aby kontrolować strukturę akapitu podczas wstawiania tekstu

1. Utwórz dwie zmienne zakresu dla pierwszego i drugiego akapitu i pobierz ich zawartość przy użyciu <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwości .

     Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet27":::

     Poniższy przykład kodu może być używany w dodatku VSTO na poziomie aplikacji. Ten kod używa aktywnego dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet27":::

2. Przypisz <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwość , zamieniając tekst między dwoma akapitami.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet28":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet28":::

3. Wybierz po kolei każdy zakres i wstrzymaj, aby wyświetlić wyniki w oknie komunikatu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet29":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet29":::

4. Dostosuj `firstRange` element przy użyciu metody , aby znacznik akapitu nie był <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> już częścią metody `firstRange` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet30":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet30":::

5. Zastąp pozostałą część tekstu w pierwszym akapicie, przypisując nowy ciąg do <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwości zakresu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet31":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet31":::

6. Zastąp tekst w , `secondRange` łącznie ze znakiem akapitu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet32":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet32":::

7. Wybierz `firstRange` i wstrzymaj, aby wyświetlić wyniki w oknie komunikatu, a następnie wykonaj te same polecenie za pomocą . `secondRange`

     Ponieważ `firstRange` została ponownie zdefiniowania w celu wykluczenia znacznika akapitu, oryginalne formatowanie akapitu jest zachowywane. Jednak nad znakiem akapitu w programie wstawiono `secondRange` zdanie, usuwając oddzielny akapit.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet33":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet33":::

     Oryginalna zawartość obu zakresów została zapisana jako ciągi, dzięki czemu można przywrócić oryginalny warunek dokumentu.

8. `firstRange`Dostosuj do dołączyć znak akapitu przy <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> użyciu metody dla pozycji jedno znakowej.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet34":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet34":::

9. Usuń folder `secondRange`. To przywróci pierwotną pozycję akapitu 3.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet35":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet35":::

10. Przywróć oryginalny tekst akapitu w pliku `firstRange` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet36":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet36":::

11. Użyj <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> metody obiektu <xref:Microsoft.Office.Interop.Word.Range> , aby wstawić oryginalną zawartość akapitu dwa po , a następnie wybierz pozycję `firstRange` `firstRange` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet37":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet37":::

## <a name="document-level-customization-example"></a>Przykład dostosowywania na poziomie dokumentu

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Aby kontrolować strukturę akapitu podczas wstawiania tekstu w dostosowaniach na poziomie dokumentu

1. W poniższym przykładzie przedstawiono kompletną metodę dostosowywania na poziomie dokumentu. Aby użyć tego kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet26":::

## <a name="vsto-add-in-example"></a>Przykład dodatku VSTO

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Aby kontrolować strukturę akapitu podczas wstawiania tekstu do dodatku VSTO

1. W poniższym przykładzie przedstawiono kompletną metodę dodatku VSTO. Aby użyć tego kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet26":::

## <a name="see-also"></a>Zobacz też
- [Jak programowo rozszerzyć zakresy w dokumentach](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [How to: Programowe zwijanie zakresów lub wyborów w dokumentach](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [How to: Programowe wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [How to: Programowe resetowanie zakresów w dokumentach programu Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
