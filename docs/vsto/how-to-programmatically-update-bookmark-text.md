---
title: 'Instrukcje: Programowe Aktualizowanie tekstu zakładki'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 436fefd425da46cea6a8cd1aba95fb9eb14362f7
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418963"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Instrukcje: Programowe Aktualizowanie tekstu zakładki
  Tak, aby przywrócić tekst w późniejszym czasie lub zastępowanie tekstu w zakładce, można wstawić tekst do symbolu zastępczego zakładki w dokumencie programu Microsoft Office Word. Jeśli tworzysz dostosowywania poziomie dokumentu, ale też aktualizować tekstu w <xref:Microsoft.Office.Tools.Word.Bookmark> formant, który jest powiązany z danymi. Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Może to być jeden z dwóch typów obiektu zakładkę:

- A <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki hosta.

   <xref:Microsoft.Office.Tools.Word.Bookmark> Formanty rozszerzać macierzysty <xref:Microsoft.Office.Interop.Word.Bookmark> obiektów po włączeniu powiązanie danych oraz udostępnianie zdarzeń. Aby uzyskać więcej informacji na temat formantów hosta zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

- Natywny <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu.

   <xref:Microsoft.Office.Interop.Word.Bookmark> obiekty nie mają możliwości wiązania zdarzenia lub dane.

  Po przypisaniu tekstu do zakładki zachowanie różni się między <xref:Microsoft.Office.Interop.Word.Bookmark> i <xref:Microsoft.Office.Tools.Word.Bookmark>. Aby uzyskać więcej informacji, zobacz [Bookmark, formant](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Użyj kontrolek hosta

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Aby zaktualizować zawartość zakładki przy użyciu formantu zakładki

1. Należy utworzyć procedurę, która przyjmuje `bookmark` argument nazwy zakładki, a `newText` argumentów dla ciągu można przypisać do <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwości.

    > [!NOTE]
    > Przypisywanie tekst <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> lub <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> właściwość <xref:Microsoft.Office.Tools.Word.Bookmark> formantu zakładki do usunięcia nie powoduje, że.

     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]

2. Przypisz *newText* ciągu do <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwość <xref:Microsoft.Office.Tools.Word.Bookmark>.

     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]

## <a name="use-word-objects"></a>Używanie obiektów programu Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Aby zaktualizować zawartość zakładki przy użyciu obiektem Bookmark programu Word

1. Tworzenie procedury, która ma `bookmark` argument dla nazwy <xref:Microsoft.Office.Interop.Word.Bookmark>, a `newText` argumentów dla ciągu można przypisać do <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwość zakładki.

    > [!NOTE]
    > Przypisywanie tekstu do natywnego programu Word <xref:Microsoft.Office.Interop.Word.Bookmark> obiektu powoduje, że zakładki do usunięcia.

     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]

2. Przypisz *newText* ciągu do <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwość zakładki, która automatycznie usuwa zakładki. Następnie ponownie dodać zakładkę do <xref:Microsoft.Office.Interop.Word.Bookmarks> kolekcji.

     Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]

     Poniższy przykład kodu może służyć w dodatku VSTO. W tym przykładzie użyto aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe Wstawianie tekstu w dokumentach programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)
- [BOOKMARK, kontrolka](../vsto/bookmark-control.md)
