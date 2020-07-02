---
title: 'Instrukcje: zmiana rozmiaru kontrolek zakładek'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6cc7b26bb767c233ed8699519261d4b5b708306b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545863"
---
# <a name="how-to-resize-bookmark-controls"></a>Instrukcje: zmiana rozmiaru kontrolek zakładek
  Należy ustawić rozmiar <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki, gdy dodasz ją do dokumentu programu Microsoft Office Word. Możesz również zmienić jego rozmiar w późniejszym czasie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Istnieją trzy sposoby zmiany rozmiaru zakładki:

- Dodawanie lub usuwanie tekstu w <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolce.

   Za każdym razem, gdy dodasz tekst w zakładce, rozmiar zakładki jest automatycznie zwiększany w celu dodania nowego tekstu. Po usunięciu tekstu rozmiar zakładki jest automatycznie zmniejszany.

- Zmień <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> właściwości i <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki.

   Jest to przydatne, jeśli zmieniasz rozmiar tylko przez kilka znaków.

- Utwórz ponownie <xref:Microsoft.Office.Tools.Word.Bookmark> formant.

   Jest to przydatne, jeśli istnieje istotna zmiana rozmiaru lub lokalizacji zakładki.

  W projektach na poziomie dokumentu można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu w projekcie w czasie projektowania lub w czasie wykonywania. W projektach dodatku VSTO można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dowolnego otwartego dokumentu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="change-the-start-and-end-properties"></a>Zmiana właściwości początkowych i końcowych

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Aby zmienić rozmiar zakładki w projekcie na poziomie dokumentu w czasie projektowania

1. Wybierz zakładkę w oknie **Właściwości** .

2. Zwiększ lub zmniejsz wartość <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> właściwości.

3. Zwiększ lub zmniejsz wartość <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> właściwości.

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>Aby zmienić rozmiar zakładki w projekcie na poziomie dokumentu w czasie wykonywania

1. Modyfikuj <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> właściwości i, <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> które zostały utworzone w czasie wykonywania lub w czasie projektowania.

     Poniższy przykład kodu dodaje pięć znaków do początku zakładki o nazwie `SampleBookmark` . Ten kod zakłada, że przed zakładką występuje co najmniej pięć znaków tekstu.

     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]

     Poniższy przykład kodu dodaje pięć znaków na końcu tej samej zakładki. W tym kodzie założono, że po zakładce istnieje co najmniej pięć znaków tekstu.

     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]

### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-run-time"></a>Aby zmienić rozmiar zakładki w projekcie dodatku VSTO w czasie wykonywania

1. Modyfikuj <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> właściwości i, <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> <xref:Microsoft.Office.Tools.Word.Bookmark> które zostały utworzone w czasie wykonywania.

     Poniższy przykład kodu tworzy <xref:Microsoft.Office.Tools.Word.Bookmark> , który zawiera tekst w pierwszym akapicie aktywnego dokumentu, a następnie usuwa pięć znaków z początku i na końcu <xref:Microsoft.Office.Tools.Word.Bookmark> .

     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]

## <a name="recreate-the-bookmark"></a>Utwórz ponownie zakładkę
 Można zmienić rozmiar zakładki w projekcie na poziomie dokumentu, dodając nową zakładkę, która ma taką samą nazwę jak istniejąca zakładka, ale ma inny rozmiar.

### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Aby ponownie utworzyć zakładkę w projekcie na poziomie dokumentu w czasie projektowania

1. Zaznacz tekst, który ma zostać uwzględniony w nowej <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolce.

2. W menu **Wstaw** kliknij **zakładkę**.

3. W oknie dialogowym **zakładka** wybierz nazwę zakładki, której rozmiar chcesz zmienić, a następnie kliknij przycisk **Dodaj**.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Instrukcje: zmiana rozmiaru kontrolek NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Instrukcje: Zmienianie rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
