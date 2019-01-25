---
title: 'Instrukcje: Zmiana rozmiaru formantów zakładki'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: f23094aae38cb1b0dc89a2b30ab7a812d7a9cb66
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869804"
---
# <a name="how-to-resize-bookmark-controls"></a>Instrukcje: Zmiana rozmiaru formantów zakładki
  Ustaw rozmiar <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli po dodaniu go do dokumentu programu Microsoft Office Word. Można też zmienić w późniejszym czasie.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Istnieją trzy sposoby, aby zmienić rozmiar zakładkę:  
  
- Dodaj lub usuń tekst w <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli.  
  
   Gdy tylko dodasz tekstu w zakładce Rozmiar zakładki automatycznie zwiększa zawiera nowego tekstu. Po usunięciu tekstowe zmniejsza się automatycznie rozmiar zakładki  
  
- Zmiana <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> i <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> właściwości <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli.  
  
   Jest to przydatne, jeśli zmieniasz rozmiar, tylko kilku znaków.  
  
- Utwórz ponownie <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli.  
  
   Jest to przydatne, jeśli ma poważne zmiany rozmiaru lub położenia zakładki.  
  
  W projektach na poziomie dokumentu, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu w projekcie w czasie projektowania lub w czasie wykonywania. W projektach dodatku narzędzi VSTO dla programów, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantów dowolnego otwartego dokumentu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="change-the-start-and-end-properties"></a>Zmień właściwości rozpoczęcia i zakończenia  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Aby zmienić rozmiar zakładki w projekcie na poziomie dokumentu w czasie projektowania  
  
1.  Wybierz zakładkę w **właściwości** okna.  
  
2.  Zwiększ lub zmniejsz wartość <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> właściwości.  
  
3.  Zwiększ lub zmniejsz wartość <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> właściwości.  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-runtime"></a>Aby zmienić rozmiar zakładki w projektach na poziomie dokumentu, w czasie wykonywania  
  
1.  Modyfikowanie <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> i <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> właściwości <xref:Microsoft.Office.Tools.Word.Bookmark> utworzone w czasie wykonywania, czy w czasie projektowania.  
  
     Poniższy przykład kodu dodaje pięć znaków na początku zakładki o nazwie `SampleBookmark`. Ten kod zakłada, że nie istnieją co najmniej pięć znaków tekstu przed zakładką.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     Poniższy przykład kodu dodaje pięć znaków na końcu tego samego zakładki. Ten kod zakłada, że po zakładki są co najmniej pięć znaków tekstu.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-runtime"></a>Aby zmienić rozmiar zakładki w projekcie dodatku narzędzi VSTO w czasie wykonywania  
  
1.  Modyfikowanie <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> i <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> właściwości <xref:Microsoft.Office.Tools.Word.Bookmark> tworzony w czasie wykonywania.  
  
     Poniższy przykład kodu tworzy <xref:Microsoft.Office.Tools.Word.Bookmark> , zawierający tekst, który w pierwszym akapicie aktywnego dokumentu, a następnie usuwa pięć znaków od początku i końca <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreate-the-bookmark"></a>Odtworzyć zakładce  
 Przez dodanie nowej zakładki, która ma taką samą nazwę jak istniejący zakładki, ale nie ma inny rozmiar można zmienić rozmiar zakładki w projekcie na poziomie dokumentu.  
  
### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Aby ponownie utworzyć zakładki w projekcie na poziomie dokumentu w czasie projektowania  
  
1.  Zaznacz tekst, które mają zostać uwzględnione w nowym <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli.  
  
2.  Na **Wstaw** menu, kliknij przycisk **zakładki**.  
  
3.  W **zakładki** okno dialogowe Wybierz nazwę zakładki, który chcesz zmienić rozmiar, a następnie kliknij przycisk **Dodaj**.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Dodawanie formantów zakładek do dokumentów programu Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Instrukcje: Zmiana rozmiaru formantów NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Instrukcje: Zmiana rozmiaru formantów ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
