---
title: Jak zmienić rozmiar kontrolek zakładki
description: Dowiedz się, jak za pomocą Visual Studio ustawić rozmiar kontrolki Zakładka po dodaniu jej do dokumentu programu Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b2b2bd963b2f0b4eb574630382930eb0805909be
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825787"
---
# <a name="how-to-resize-bookmark-controls"></a>Jak zmienić rozmiar kontrolek zakładki
  Rozmiar kontrolki ustawia się podczas dodawania jej do dokumentu <xref:Microsoft.Office.Tools.Word.Bookmark> Microsoft Office Word. Możesz również zmienić jego rozmiar w późniejszym czasie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Istnieją trzy sposoby zmiany rozmiaru zakładki:

- Dodaj lub usuń tekst w <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolce.

   Za każdym razem, gdy dodajesz tekst do zakładki, rozmiar zakładki automatycznie zwiększa się, aby zawierał nowy tekst. Po usunięciu tekstu rozmiar zakładki automatycznie się zmniejsza.

- Zmień właściwości <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> i <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki.

   Jest to przydatne, jeśli zmieniasz rozmiar tylko o kilka znaków.

- Utwórz ponownie <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkę.

   Jest to przydatne w przypadku znaczącej zmiany rozmiaru lub lokalizacji zakładki.

  W projektach na poziomie dokumentu można dodawać kontrolki do dokumentu w projekcie w czasie <xref:Microsoft.Office.Tools.Word.Bookmark> projektowania lub w czasie uruchamiania. W projektach dodatków VSTO można dodawać kontrolki <xref:Microsoft.Office.Tools.Word.Bookmark> do dowolnego otwartego dokumentu w czasie uruchamiania. Aby uzyskać więcej informacji, zobacz [How to: Add Bookmark controls to Word documents (Jak dodać kontrolki zakładek do dokumentów programu Word).](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="change-the-start-and-end-properties"></a>Zmienianie właściwości początku i końca

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Aby zmienić rozmiar zakładki w projekcie na poziomie dokumentu w czasie projektowania

1. Wybierz zakładkę w **oknie** Właściwości.

2. Zwiększ lub zmniejsz wartość <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> właściwości.

3. Zwiększ lub zmniejsz wartość <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> właściwości.

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>Aby zmienić rozmiar zakładki w projekcie na poziomie dokumentu w czasie uruchamiania

1. <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> Zmodyfikuj właściwości i obiektu <xref:Microsoft.Office.Tools.Word.Bookmark> utworzonego w czasie uruchamiania lub w czasie projektowania.

     Poniższy przykład kodu dodaje pięć znaków na początku zakładki o nazwie `SampleBookmark` . W tym kodzie przyjęto założenie, że przed zakładką znajduje się co najmniej pięć znaków tekstu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet2":::

     Poniższy przykład kodu dodaje pięć znaków na końcu tej samej zakładki. W tym kodzie przyjęto założenie, że po zakładce znajduje się co najmniej pięć znaków tekstu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet3":::

### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-run-time"></a>Aby zmienić rozmiar zakładki w projekcie dodatku VSTO w czasie uruchamiania

1. <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> Zmodyfikuj właściwości i obiektu <xref:Microsoft.Office.Tools.Word.Bookmark> utworzonego w czasie uruchamiania.

     Poniższy przykład kodu tworzy , który zawiera tekst w pierwszym akapicie aktywnego dokumentu, a następnie usuwa pięć znaków z początku i <xref:Microsoft.Office.Tools.Word.Bookmark> końca <xref:Microsoft.Office.Tools.Word.Bookmark> ciągu .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet16":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet16":::

## <a name="recreate-the-bookmark"></a>Ponowne utworzenie zakładki
 Rozmiar zakładki w projekcie na poziomie dokumentu można zmienić, dodając nową zakładkę o takiej samej nazwie jak istniejąca zakładka, ale o innym rozmiarze.

### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Aby ponownie utworzyć zakładkę w projekcie na poziomie dokumentu w czasie projektowania

1. Wybierz tekst, który ma zostać uwzględniony w nowej <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolce.

2. W menu **Wstaw** kliknij pozycję **Zakładka.**

3. W **oknie dialogowym** Zakładka wybierz nazwę zakładki, której rozmiar chcesz zmienić, a następnie kliknij przycisk **Dodaj**.

## <a name="see-also"></a>Zobacz też
- [How to: Add Bookmark controls to Word documents (Jak dodać kontrolki zakładek do dokumentów programu Word)](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [How to: Resize NamedRange controls (2017: Zmienianie rozmiaru kontrolek NamedRange)](../vsto/how-to-resize-namedrange-controls.md)
- [How to: Resize ListObject controls (2017: Zmienianie rozmiaru kontrolek ListObject)](../vsto/how-to-resize-listobject-controls.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
