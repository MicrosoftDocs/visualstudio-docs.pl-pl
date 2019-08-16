---
title: 'Instrukcje: Programowo zapisuj dokumenty'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b4fbf8e4cb67d5216dc17c325911bb243fae6e1c
ms.sourcegitcommit: 5b34052a1c7d86179d7898ed532babb2d9dad4a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490610"
---
# <a name="how-to-programmatically-save-documents"></a>Instrukcje: Programowo zapisuj dokumenty

Istnieje kilka sposobów zapisywania dokumentów programu Microsoft Office Word. Możesz zapisać dokument bez zmiany nazwy dokumentu lub zapisać dokument z nową nazwą.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Zapisz dokument bez zmiany nazwy

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Aby zapisać dokument skojarzony z dostosowywaniem na poziomie dokumentu

1. Wywoływanie <xref:Microsoft.Office.Tools.Word.Document>metodyklasy. <xref:Microsoft.Office.Tools.Word.Document.Save%2A> Aby użyć tego przykładu kodu, należy uruchomić go `ThisDocument` z klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreWordAutomation#7](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#7)]

### <a name="to-save-the-active-document"></a>Aby zapisać aktywny dokument

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodę dla aktywnego dokumentu. Aby użyć tego przykładu kodu, należy uruchomić go `ThisDocument` z `ThisAddIn` lub klasy w projekcie.

    [!code-vb[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#8)]
    [!code-csharp[Trin_VstcoreWordAutomation#8](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#8)]

   Jeśli nie masz pewności, czy dokument, który chcesz zapisać, jest aktywnym dokumentem, możesz odwołać się do niego według jego nazwy.

### <a name="to-save-a-document-specified-by-name"></a>Aby zapisać dokument określony przez nazwę

1. Użyj nazwy dokumentu jako argumentu do <xref:Microsoft.Office.Interop.Word.Documents> kolekcji. Aby użyć tego przykładu kodu, należy uruchomić go `ThisDocument` z `ThisAddIn` lub klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#9)]
     [!code-csharp[Trin_VstcoreWordAutomation#9](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#9)]

## <a name="save-a-document-with-a-new-name"></a>Zapisz dokument o nowej nazwie

Użyj metody `SaveAs` , aby zapisać dokument z nową nazwą. Tej metody <xref:Microsoft.Office.Tools.Word.Document> można użyć dla elementu hosta w projekcie programu Word na poziomie dokumentu lub obiektu natywnego <xref:Microsoft.Office.Interop.Word.Document> w dowolnym projekcie programu Word. Ta metoda wymaga określenia nowej nazwy pliku, ale inne argumenty są opcjonalne.

> [!NOTE]
> Jeśli w programie `ThisDocument` obsługi <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> zdarzeń zostanie wyświetlone okno dialogowe SaveAs i ustawisz **wartość false**dla parametru *Cancel* , aplikacja może zostać nieoczekiwanie zakończona. Jeśli ustawisz dla parametru *Cancel* **wartość true**, zostanie wyświetlony komunikat o błędzie z informacją, że Autozapisywanie zostało wyłączone.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Aby zapisać dokument skojarzony z dostosowaniem na poziomie dokumentu przy użyciu nowej nazwy

1. Wywołaj `ThisDocument` metodę klasy w projekcie, używając w pełni kwalifikowanej ścieżki i nazwy pliku. `SaveAs` Jeśli plik o tej nazwie już istnieje w tym folderze, zostanie nadpisany w trybie dyskretnym. Aby użyć tego przykładu kodu, należy uruchomić go `ThisDocument` z klasy.

    > [!NOTE]
    > `SaveAs` Metoda zgłasza wyjątek, jeśli katalog docelowy nie istnieje lub występują inne problemy z zapisywaniem pliku. Dobrym sposobem jest użycie`try...catch` bloku `SaveAs` wokół metody lub wewnątrz metody wywołującej.

     [!code-vb[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#10)]

### <a name="to-save-a-native-document-with-a-new-name"></a>Aby zapisać dokument natywny z nową nazwą

1. Wywołaj <xref:Microsoft.Office.Interop.Word.Document> metodę, która ma zostać zapisana, przy użyciu w pełni kwalifikowanej ścieżki i nazwy pliku. <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Jeśli plik o tej nazwie już istnieje w tym folderze, zostanie nadpisany w trybie dyskretnym.

     Poniższy przykład kodu zapisuje aktywny dokument z nową nazwą. Aby użyć tego przykładu kodu, należy uruchomić go `ThisDocument` z `ThisAddIn` lub klasy w projekcie.

    > [!NOTE]
    > <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> Metoda zgłasza wyjątek, jeśli katalog docelowy nie istnieje lub występują inne problemy z zapisywaniem pliku. Dobrym sposobem jest użycie **try... blok catch** wokół <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metody lub wewnątrz metody wywołującej.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#10)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#10)]

## <a name="compile-the-code"></a>Skompilować kod

Ten przykład kodu wymaga następujących czynności:

- Aby zapisać dokument według nazwy, dokument o nazwie *NewDocument. doc* musi znajdować się w katalogu o nazwie *test* na dysku C.

- Aby zapisać dokument o nowej nazwie, katalog o nazwie *test* musi znajdować się na dysku C.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Programowe Zamykanie dokumentów](../vsto/how-to-programmatically-close-documents.md)
- [Instrukcje: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
