---
title: 'Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: de5868674790239b8374ef9796308280588ae96e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547254"
---
# <a name="how-to-add-bookmark-controls-to-word-documents"></a>Instrukcje: Dodawanie kontrolek zakładek do dokumentów programu Word
  W projektach na poziomie dokumentu można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dokumentu w projekcie w czasie projektowania lub w czasie wykonywania. W projektach dodatku VSTO można dodać <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki do dowolnego otwartego dokumentu w czasie wykonywania.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 W tym temacie opisano następujące zadania:

- [Dodawanie kontrolek zakładek w czasie projektowania](#designtime)

- [Dodawanie kontrolek zakładek w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek zakładek w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

  Aby uzyskać więcej informacji o <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolkach, zobacz [kontrolka zakładka](../vsto/bookmark-control.md).

## <a name="add-bookmark-controls-at-design-time"></a><a name="designtime"></a>Dodawanie kontrolek zakładek w czasie projektowania
 Istnieje kilka sposobów dodawania <xref:Microsoft.Office.Tools.Word.Bookmark> formantów do dokumentu w projekcie na poziomie dokumentu w czasie projektowania:

- Z **przybornika**programu Visual Studio.

   Możesz przeciągnąć <xref:Microsoft.Office.Tools.Word.Bookmark> formant z **przybornika** do dokumentu. Możesz wybrać ten sposób, jeśli używasz już **przybornika** , aby dodać kontrolki Windows Forms do dokumentu.

- Z poziomu programu Word.

   Możesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formant do dokumentu w taki sam sposób, jak dodać zakładkę natywną. Zaletą dodawania IT w ten sposób jest to, że można nazwać swój formant w momencie jego tworzenia.

- W oknie **źródła danych** .

   Możesz przeciągnąć <xref:Microsoft.Office.Tools.Word.Bookmark> formant do dokumentu z okna **źródła danych** . Jest to przydatne, gdy chcesz powiązać kontrolkę z danymi w tym samym czasie. Można dodać kontrolkę hosta w taki sam sposób, jak dodać kontrolkę formularz systemu Windows z okna **źródła danych** . Aby uzyskać więcej informacji, zobacz temat [powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

#### <a name="to-add-a-bookmark-control-to-a-document-from-the-toolbox"></a>Aby dodać kontrolkę zakładki do dokumentu z przybornika

1. Otwórz **Przybornik** i kliknij kartę **formanty wyrazów** .

2. Przeciągnij <xref:Microsoft.Office.Tools.Word.Bookmark> formant do dokumentu.

     Pojawi się okno dialogowe **Dodaj zakładkę** .

3. Zaznacz tekst lub inne elementy, które mają zostać uwzględnione w zakładce.

4. Kliknij przycisk **OK**.

     Jeśli nie chcesz zachować domyślnej nazwy zakładki, możesz zmienić nazwę w oknie **Właściwości** .

#### <a name="to-add-a-bookmark-control-to-a-document-in-word"></a>Aby dodać kontrolkę zakładki do dokumentu w programie Word

1. W dokumencie, który jest hostowany w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie, umieść kursor w miejscu, w którym chcesz dodać zakładkę, lub zaznacz tekst, który ma zostać umieszczony w zakładce.

2. Na karcie **Wstawianie** wstążki w grupie **linki** kliknij przycisk **zakładka** .

3. W oknie dialogowym **zakładka** wpisz nazwę nowej zakładki, a następnie kliknij przycisk **Dodaj**.

## <a name="add-bookmark-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a>Dodawanie kontrolek zakładek w czasie wykonywania w projekcie na poziomie dokumentu
 <xref:Microsoft.Office.Tools.Word.Bookmark>Kontrolki można dodawać programowo do dokumentu w czasie wykonywania przy użyciu metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości `ThisDocument` klasy w projekcie. Istnieją dwa przeciążenia metod, których można użyć do dodania <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki w następujący sposób:

- Dodaj do <xref:Microsoft.Office.Tools.Word.Bookmark> określonego zakresu.

- Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> , który jest oparty na zakładce natywnej w dokumencie (czyli <xref:Microsoft.Office.Interop.Word.Bookmark> ).

  Formanty utworzone dynamicznie <xref:Microsoft.Office.Tools.Word.Bookmark> nie są utrwalane w dokumencie, gdy dokument jest zamknięty. Jednak natywny <xref:Microsoft.Office.Interop.Word.Bookmark> pozostanie w dokumencie. Możesz ponownie utworzyć obiekt <xref:Microsoft.Office.Tools.Word.Bookmark> , który jest oparty na zakładce natywne przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

#### <a name="to-add-a-bookmark-control-to-a-document-programmatically"></a>Aby programowo dodać kontrolkę zakładki do dokumentu

1. W programie `ThisDocument_Startup` obsługi zdarzeń w projekcie Wstaw poniższy kod, aby dodać <xref:Microsoft.Office.Tools.Word.Bookmark> formant do pierwszego akapitu w dokumencie.

     [!code-csharp[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsWord#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#1)]

    > [!NOTE]
    > Jeśli chcesz utworzyć <xref:Microsoft.Office.Tools.Word.Bookmark> formant z istniejącego <xref:Microsoft.Office.Interop.Word.Bookmark> , użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metody i przekaż istniejący <xref:Microsoft.Office.Interop.Word.Bookmark> .

## <a name="add-bookmark-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>Dodawanie kontrolek zakładek w czasie wykonywania w projekcie dodatku narzędzi VSTO
 <xref:Microsoft.Office.Tools.Word.Bookmark>Kontrolki można dodawać programowo do dowolnego otwartego dokumentu w czasie wykonywania przy użyciu dodatku VSTO. W tym celu należy wygenerować <xref:Microsoft.Office.Tools.Word.Document> element hosta, który jest oparty na otwartym dokumencie, a następnie użyć metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości tego elementu hosta. Istnieją dwa przeciążenia metod, których można użyć do dodania <xref:Microsoft.Office.Tools.Word.Bookmark> kontrolki w następujący sposób:

- Dodaj do <xref:Microsoft.Office.Tools.Word.Bookmark> określonego zakresu.

- Dodaj <xref:Microsoft.Office.Tools.Word.Bookmark> , który jest oparty na zakładce natywnej w dokumencie (czyli <xref:Microsoft.Office.Interop.Word.Bookmark> ).

  Formanty utworzone dynamicznie <xref:Microsoft.Office.Tools.Word.Bookmark> nie są utrwalane w dokumencie, gdy dokument jest zamknięty. Jednak natywny <xref:Microsoft.Office.Interop.Word.Bookmark> pozostanie w dokumencie. Możesz ponownie utworzyć obiekt <xref:Microsoft.Office.Tools.Word.Bookmark> , który jest oparty na zakładce natywne przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Utrwalanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Aby uzyskać więcej informacji na temat generowania elementów hosta w projektach dodatku VSTO, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

#### <a name="to-add-a-bookmark-control-at-a-specified-range"></a>Aby dodać kontrolkę zakładka z określonym zakresem

1. Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metody i Przekaż w miejscu, w <xref:Microsoft.Office.Interop.Word.Range> którym chcesz dodać <xref:Microsoft.Office.Tools.Word.Bookmark> .

     Poniższy przykład kodu dodaje nowy <xref:Microsoft.Office.Tools.Word.Bookmark> na początku aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn_Startup` programu obsługi zdarzeń w projekcie dodatku programu Word VSTO.

     [!code-vb[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#4)]
     [!code-csharp[Trin_WordAddInDynamicControls#4](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#4)]

#### <a name="to-add-a-bookmark-control-that-is-based-on-a-native-bookmark-control"></a>Aby dodać kontrolkę zakładki, która jest oparta na natywnej kontrolce zakładki

1. Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddBookmark%2A> metody i przekaż istniejący, <xref:Microsoft.Office.Interop.Word.Bookmark> który ma być używany jako podstawa dla nowego <xref:Microsoft.Office.Tools.Word.Bookmark> .

     Poniższy przykład kodu tworzy nowy <xref:Microsoft.Office.Tools.Word.Bookmark> , który jest oparty na pierwszej <xref:Microsoft.Office.Interop.Word.Bookmark> w aktywnym dokumencie. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn_Startup` programu obsługi zdarzeń w projekcie dodatku programu Word VSTO.

     [!code-vb[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#5)]
     [!code-csharp[Trin_WordAddInDynamicControls#5](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#5)]

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Instrukcje: zmiana rozmiaru kontrolek zakładek](../vsto/how-to-resize-bookmark-controls.md)
