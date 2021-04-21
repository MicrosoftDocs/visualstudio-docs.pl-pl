---
title: Jak programowo zaktualizować tekst zakładki
description: Dowiedz się, jak używać Visual Studio w celu programowego wstawiania tekstu do zakładki symbolu zastępczego w dokumencie programu Microsoft Word.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f67dbbe4d1d5c24d617f9cbc49a58ec2d134e90b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826203"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Jak programowo zaktualizować tekst zakładki
  Możesz wstawić tekst do zakładki symbolu zastępczego w dokumencie programu Microsoft Office Word, aby później pobrać tekst lub zastąpić tekst w zakładce. Jeśli opracowujesz dostosowanie na poziomie dokumentu, możesz również zaktualizować tekst w kontrolce <xref:Microsoft.Office.Tools.Word.Bookmark> powiązanej z danymi. Aby uzyskać więcej informacji, zobacz [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office.](../vsto/binding-data-to-controls-in-office-solutions.md)

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Obiekt bookmark może być jednym z dwóch typów:

- Kontrolka <xref:Microsoft.Office.Tools.Word.Bookmark> hosta.

   <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki <xref:Microsoft.Office.Interop.Word.Bookmark> rozszerzają obiekty natywne, włączając powiązanie danych i ujawniając zdarzenia. Aby uzyskać więcej informacji na temat kontrolek hosta, zobacz [Host items and host controls overview (Omówienie elementów hosta i kontrolek hosta).](../vsto/host-items-and-host-controls-overview.md)

- Obiekt <xref:Microsoft.Office.Interop.Word.Bookmark> natywny.

   <xref:Microsoft.Office.Interop.Word.Bookmark> Obiekty nie mają możliwości zdarzeń ani powiązań danych.

  W przypadku przypisywania tekstu do zakładki zachowanie między a <xref:Microsoft.Office.Interop.Word.Bookmark> i <xref:Microsoft.Office.Tools.Word.Bookmark> . Aby uzyskać więcej informacji, zobacz [Kontrolka zakładki](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Używanie kontrolek hosta

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Aby zaktualizować zawartość zakładki przy użyciu kontrolki Zakładka

1. Utwórz procedurę, która przyjmuje argument dla nazwy zakładki i argument dla ciągu do `bookmark` `newText` przypisania do <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwości.

    > [!NOTE]
    > Przypisanie tekstu do właściwości lub kontrolki nie powoduje usunięcia <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> zakładki.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet63":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet63":::

2. Przypisz *ciąg newText* do <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> właściwości <xref:Microsoft.Office.Tools.Word.Bookmark> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet64":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet64":::

## <a name="use-word-objects"></a>Korzystanie z obiektów programu Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Aby zaktualizować zawartość zakładki przy użyciu obiektu zakładki programu Word

1. Utwórz procedurę, która ma argument dla nazwy , i argument dla ciągu do przypisania do `bookmark` <xref:Microsoft.Office.Interop.Word.Bookmark> właściwości `newText` <xref:Microsoft.Office.Interop.Word.Range.Text%2A> zakładki.

    > [!NOTE]
    > Przypisanie tekstu do natywnego obiektu programu Word <xref:Microsoft.Office.Interop.Word.Bookmark> powoduje usunięcie zakładki.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet65":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet65":::

2. Przypisz *ciąg newText* do <xref:Microsoft.Office.Interop.Word.Range.Text%2A> właściwości zakładki, która automatycznie usuwa zakładkę. Następnie ponownie dodaj zakładkę do <xref:Microsoft.Office.Interop.Word.Bookmarks> kolekcji.

     Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet66":::

     Poniższy przykład kodu może być używany w dodatku VSTO. W tym przykładzie jest używany aktywny dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet66":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet66":::

## <a name="see-also"></a>Zobacz też
- [How to: Programowe wstawianie tekstu do dokumentów programu Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Omówienie modelu obiektów programu Word](../vsto/word-object-model-overview.md)
- [Kontrolka zakładki](../vsto/bookmark-control.md)
