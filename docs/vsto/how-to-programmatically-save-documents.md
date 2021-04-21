---
title: 'How to: Programowe zapisywanie dokumentów'
description: Dowiedz się, jak za Visual Studio można programowo zapisać dokument bez zmiany jego nazwy lub nowej nazwy.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving
- Word [Office development in Visual Studio], saving documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 97f56ce0bd44eac71430a099b4fda9a7eddc7958
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107829011"
---
# <a name="how-to-programmatically-save-documents"></a>How to: Programowe zapisywanie dokumentów

Istnieje kilka sposobów zapisywania Microsoft Office programu Word. Możesz zapisać dokument bez zmiany jego nazwy lub zapisać dokument pod nową nazwą.

[!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="save-a-document-without-changing-the-name"></a>Zapisywanie dokumentu bez zmiany nazwy

### <a name="to-save-the-document-associated-with-a-document-level-customization"></a>Aby zapisać dokument skojarzony z dostosowaniem na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.Save%2A> metodę <xref:Microsoft.Office.Tools.Word.Document> klasy . Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet7":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet7":::

### <a name="to-save-the-active-document"></a>Aby zapisać aktywny dokument

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.Save%2A> metodę dla aktywnego dokumentu. Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet8":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet8":::

   Jeśli nie masz pewności, czy dokument, który chcesz zapisać, jest aktywnym dokumentem, możesz odwołać się do niego za pomocą jego nazwy.

### <a name="to-save-a-document-specified-by-name"></a>Aby zapisać dokument określony przez nazwę

1. Użyj nazwy dokumentu jako argumentu do <xref:Microsoft.Office.Interop.Word.Documents> kolekcji. Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet9":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet9":::

## <a name="save-a-document-with-a-new-name"></a>Zapisywanie dokumentu pod nową nazwą

Użyj `SaveAs` metody , aby zapisać dokument pod nową nazwą. Tej metody elementu hosta można użyć w projekcie programu Word na poziomie dokumentu lub obiektu natywnego <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> w dowolnym projekcie programu Word. Ta metoda wymaga określenia nowej nazwy pliku, ale inne argumenty są opcjonalne.

> [!NOTE]
> Jeśli w programie obsługi zdarzeń programu zostanie wyświetlone okno dialogowe **SaveAs** i ustawisz parametr Anuluj na wartość false, aplikacja <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> może zostać `ThisDocument` nieoczekiwanie zamknięty.   Jeśli ustawisz parametr *Anuluj* na **wartość true,** zostanie wyświetlony komunikat o błędzie informujący o tym, że autozabłysanie zostało wyłączone.

### <a name="to-save-the-document-associated-with-a-document-level-customization-with-a-new-name"></a>Aby zapisać dokument skojarzony z dostosowaniem na poziomie dokumentu z nową nazwą

1. Wywołaj `SaveAs` metodę klasy w `ThisDocument` projekcie przy użyciu w pełni kwalifikowanej ścieżki i nazwy pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, zostanie dyskretnie zastąpiony. Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy .

    > [!NOTE]
    > Metoda zgłasza wyjątek, jeśli katalog docelowy nie istnieje lub jeśli występują inne problemy `SaveAs` z zapisywaniem pliku. Dobrym rozwiązaniem jest użycie bloku wokół metody `try...catch` `SaveAs` lub wewnątrz metody wywołującej.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet10":::

### <a name="to-save-a-native-document-with-a-new-name"></a>Aby zapisać dokument natywny z nową nazwą

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metodę metody , którą chcesz <xref:Microsoft.Office.Interop.Word.Document> zapisać, używając w pełni kwalifikowanej ścieżki i nazwy pliku. Jeśli plik o tej nazwie już istnieje w tym folderze, zostanie dyskretnie zastąpiony.

     Poniższy przykład kodu zapisuje aktywny dokument pod nową nazwą. Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

    > [!NOTE]
    > Metoda zgłasza wyjątek, jeśli katalog docelowy nie istnieje lub jeśli występują inne problemy <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> z zapisywaniem pliku. Dobrym rozwiązaniem jest **wypróbowanie... Blok catch** wokół <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> metody lub wewnątrz metody wywołującej.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet10":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet10":::

## <a name="compile-the-code"></a>Kompilowanie kodu

Ten przykład kodu wymaga następujących czynności:

- Aby zapisać dokument według nazwy, dokument o *nazwieNewDocument.doc* musi istnieć w katalogu o nazwie *Test* na dysku C.

- Aby zapisać dokument pod nową nazwą, na dysku C musi istnieć katalog o nazwie *Test.*

## <a name="see-also"></a>Zobacz też

- [Pisano: Programowe zamykanie dokumentów](../vsto/how-to-programmatically-close-documents.md)
- [2018: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
