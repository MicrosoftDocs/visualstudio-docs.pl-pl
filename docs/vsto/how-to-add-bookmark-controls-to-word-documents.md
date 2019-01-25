---
title: 'Instrukcje: Dodawanie formantów zakładek do dokumentów programu Word'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Bookmark.Dialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Bookmark control, adding to documents
- Create Bookmark Control dialog box
- controls [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 019319a2f4f2eb7da8646317796e89b2d3322d28
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54874214"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Instrukcje: Dodawanie formantów zakładek do dokumentów programu Word
  W projektach na poziomie dokumentu, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu w projekcie w czasie projektowania lub w czasie wykonywania. W projektach dodatku narzędzi VSTO dla programów, można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formantów dowolnego otwartego dokumentu w czasie wykonywania.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 W tym temacie opisano następujące zadania:  
  
- [Dodawanie formantów zakładek w czasie projektowania](#designtime)  
  
- [Dodawanie formantów zakładek w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)  
  
- [Dodawanie formantów zakładek w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
  Aby uzyskać więcej informacji na temat <xref:Microsoft.Office.Tools.Word.Bookmark> formantów, zobacz [Bookmark, formant](../vsto/bookmark-control.md).  
  
##  <a name="designtime"></a> Dodawanie formantów zakładek w czasie projektowania  
 Istnieje kilka sposobów, aby dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu w projekcie na poziomie dokumentu, w czasie projektowania:  
  
- W programie Visual Studio **przybornika**.  
  
   Można przeciągnąć <xref:Microsoft.Office.Tools.Word.Bookmark> z kontrolować **przybornika** do dokumentu. Należy wybrać w ten sposób, jeśli już używasz **przybornika** do dodawania formantów Windows Forms do dokumentu.  
  
- Z poziomu programu Word.  
  
   Możesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu w taki sam sposób należy dodać zakładki natywnych. Zaletą dodawania go w ten sposób jest to nazwy formantu w czasie jego tworzenia.  
  
- Z **źródeł danych** okna.  
  
   Można przeciągnąć <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu z **źródeł danych** okna. Jest to przydatne, jeśli chcesz powiązać kontrolkę z danymi w tym samym czasie. Można dodać kontrolki hosta w taki sam sposób, należy dodać kontrolkę formularza Windows z **źródeł danych** okna. Aby uzyskać więcej informacji, zobacz [powiązanie danych oraz Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Aby dodać kontrolkę zakładki w dokumencie z przybornika  
  
1.  Otwórz **przybornika** i kliknij przycisk **formanty programu Word** kartę.  
  
2.  Przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu.  
  
     **Dodaj zakładkę** pojawi się okno dialogowe.  
  
3.  Wybierz tekst lub inne elementy, które mają zostać uwzględnione w zakładce.  
  
4.  Kliknij przycisk **OK**.  
  
     Jeśli nie chcesz zachować domyślnej nazwy zakładki, można zmienić nazwę w **właściwości** okna.  
  
#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Aby dodać kontrolkę zakładki w dokumencie programu Word  
  
1.  W dokumencie, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta, umieścić kursor, w której chcesz dodać zakładki, lub zaznacz tekst, który chcesz, aby zakładki, aby ująć.  
  
2.  Na **Wstaw** karty wstążki w **łącza** grupy, kliknij przycisk **zakładki** przycisku.  
  
3.  W **zakładki** okno dialogowe, wpisz nazwę nowej zakładki, a następnie kliknij przycisk **Dodaj**.  
  
##  <a name="runtimedoclevel"></a> Dodawanie formantów zakładek w czasie wykonywania w projekcie na poziomie dokumentu  
 Możesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> programowo kontrolki do dokumentu w czasie wykonywania, za pomocą metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwość `ThisDocument` klasy w projekcie. Istnieją dwa przeciążenia metody, których można użyć, aby dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli w następujący sposób:  
  
- Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> w określonym zakresie.  
  
- Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> opartego na natywny zakładki w dokumencie (czyli <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
  Tworzone dynamicznie <xref:Microsoft.Office.Tools.Word.Bookmark> formanty nie są zachowywane w dokumencie, gdy dokument zostanie zamknięty. Jednak macierzystej <xref:Microsoft.Office.Interop.Word.Bookmark> pozostaje w dokumencie. Można odtworzyć <xref:Microsoft.Office.Tools.Word.Bookmark> opartego na natywny zakładki przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Aby programowo dodać kontrolkę zakładki w dokumencie  
  
1.  W `ThisDocument_Startup` programu obsługi zdarzeń w projekcie, Wstaw następujący kod, aby dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formant do pierwszego akapitu w dokumencie.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]  
  
    > [!NOTE]  
    >  Jeśli chcesz utworzyć <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki z istniejącego <xref:Microsoft.Office.Interop.Word.Bookmark>, użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metody i przekazać w istniejącym <xref:Microsoft.Office.Interop.Word.Bookmark>.  
  
##  <a name="runtimeaddin"></a> Dodawanie formantów zakładek w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Możesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki programowo do dowolnego otwartego dokumentu w czasie wykonywania za pomocą dodatku narzędzi VSTO. Aby to zrobić, należy wygenerować <xref:Microsoft.Office.Tools.Word.Document> elementu, która jest oparta na otwartym dokumencie hosta, a następnie użyj metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości tego elementu host. Istnieją dwa przeciążenia metody, których można użyć, aby dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontroli w następujący sposób:  
  
- Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> w określonym zakresie.  
  
- Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> opartego na natywny zakładki w dokumencie (czyli <xref:Microsoft.Office.Interop.Word.Bookmark>).  
  
  Tworzone dynamicznie <xref:Microsoft.Office.Tools.Word.Bookmark> formanty nie są zachowywane w dokumencie, gdy dokument zostanie zamknięty. Jednak macierzystej <xref:Microsoft.Office.Interop.Word.Bookmark> pozostaje w dokumencie. Można odtworzyć <xref:Microsoft.Office.Tools.Word.Bookmark> opartego na natywny zakładki przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [kontrolek dynamicznych w dokumentach pakietu Office utrwalenia](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
  Aby uzyskać więcej informacji na temat generowania elementów hosta w projektach dodatku narzędzi VSTO dla programów, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Aby dodać kontrolkę zakładki w określonym zakresie  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metody i przekaż <xref:Microsoft.Office.Interop.Word.Range> gdzie chcesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Poniższy przykład kodu dodaje nowy <xref:Microsoft.Office.Tools.Word.Bookmark> na początku aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn_Startup` program obsługi zdarzeń w projekcie dodatku narzędzi VSTO programu Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]  
  
#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Aby dodać kontrolkę zakładki, która opiera się na macierzystym kontrolka zakładki  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metody i przekazać w istniejącym <xref:Microsoft.Office.Interop.Word.Bookmark> , którą chcesz użyć jako podstawy dla nowego <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     Poniższy przykład kodu tworzy nową <xref:Microsoft.Office.Tools.Word.Bookmark> oznacza to na podstawie pierwszego <xref:Microsoft.Office.Interop.Word.Bookmark> w aktywnym dokumencie. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn_Startup` program obsługi zdarzeń w projekcie dodatku narzędzi VSTO programu Word.  
  
     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]  
  
## <a name="see-also"></a>Zobacz także  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)   
 [Instrukcje: Zmiana rozmiaru formantów zakładki](../vsto/how-to-resize-bookmark-controls.md)  
