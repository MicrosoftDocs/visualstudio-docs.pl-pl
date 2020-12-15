---
title: 'Instrukcje: Programowane aktualizowanie tekstu zakładki'
description: Dowiedz się, jak można użyć programu Visual Studio do programistycznego wstawiania tekstu do zakładki zastępczej w dokumencie programu Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 9b9fa4b5ef19fdcaae38ef477952580f6568fcc0
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523560"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Instrukcje: Programowane aktualizowanie tekstu zakładki
  Możesz wstawić tekst do zakładki zastępczej w Microsoft Office dokumencie programu Word, aby można było pobrać tekst w późniejszym czasie lub zamienić tekst w zakładce. Jeśli tworzysz dostosowanie na poziomie dokumentu, możesz również zaktualizować tekst w <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolce, która jest powiązana z danymi. Aby uzyskać więcej informacji, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Obiekt zakładki może być jednym z dwóch typów:

- <xref:Microsoft.Office.Tools.Word.Bookmark>Kontrolka hosta.

   <xref:Microsoft.Office.Tools.Word.Bookmark> formanty rozszerzają <xref:Microsoft.Office.Interop.Word.Bookmark> obiekty natywne przez włączenie powiązań danych i Uwidacznianie zdarzeń. Aby uzyskać więcej informacji na temat kontrolek hosta, zobacz temat [elementy hosta i kontrolki hosta](../vsto/host-items-and-host-controls-overview.md).

- Obiekt macierzysty <xref:Microsoft.Office.Interop.Word.Bookmark> .

   <xref:Microsoft.Office.Interop.Word.Bookmark> obiekty nie mają możliwości zdarzeń ani powiązań danych.

  Po przypisaniu tekstu do zakładki zachowanie różni się od <xref:Microsoft.Office.Interop.Word.Bookmark> i <xref:Microsoft.Office.Tools.Word.Bookmark> . Aby uzyskać więcej informacji, zobacz [kontrolka zakładka](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Korzystanie z kontrolek hosta

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Aby zaktualizować zawartość zakładki przy użyciu kontrolki zakładki

1. Utwórz procedurę, która przyjmuje `bookmark` argument dla nazwy zakładki i `newText` argument dla ciągu do przypisania do <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwości.

    > [!NOTE]
    > Przypisanie tekstu do <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwości lub <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki nie powoduje usunięcia zakładki.

     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]

2. Przypisz ciąg *newText* do <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwości <xref:Microsoft.Office.Tools.Word.Bookmark> .

     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]

## <a name="use-word-objects"></a>Korzystanie z obiektów programu Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Aby zaktualizować zawartość zakładki przy użyciu obiektu zakładki programu Word

1. Utwórz procedurę, która ma `bookmark` argument dla nazwy <xref:Microsoft.Office.Interop.Word.Bookmark> i `newText` argumentu dla ciągu, który ma zostać przypisany do <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Właściwości zakładki.

    > [!NOTE]
    > Przypisanie tekstu do macierzystego obiektu programu Word <xref:Microsoft.Office.Interop.Word.Bookmark> powoduje usunięcie zakładki.

     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]

2. Przypisz ciąg *newText* do <xref:Microsoft.Office.Interop.Word.Range.Text%2A> Właściwości zakładki, która automatycznie usuwa zakładkę. Następnie ponownie Dodaj zakładkę do <xref:Microsoft.Office.Interop.Word.Bookmarks> kolekcji.

     Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]

     Poniższy przykład kodu może być używany w dodatku VSTO. Ten przykład używa aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)
- [Kontrolka zakładki](../vsto/bookmark-control.md)
