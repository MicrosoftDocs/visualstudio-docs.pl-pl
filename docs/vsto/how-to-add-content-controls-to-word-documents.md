---
title: 'Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word'
description: Dowiedz się, że w projektach programu Word na poziomie dokumentu, możesz dodać kontrolki zawartości do dokumentu w projekcie w czasie projektowania lub w czasie wykonywania.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aa1528371a1466ec2886bf652ed33561b66b7028
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845560"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word
  W projektach programu Word na poziomie dokumentu można dodawać kontrolki zawartości do dokumentu w projekcie w czasie projektowania lub w czasie wykonywania. W projektach dodatku programu Word VSTO można dodać kontrolki zawartości do dowolnego otwartego dokumentu w czasie wykonywania.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 W tym temacie opisano następujące zadania:

- [Dodawanie kontrolek zawartości w czasie projektowania](#designtime)

- [Dodawanie kontrolek zawartości w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek zawartości w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)

  Aby uzyskać informacje o kontrolkach zawartości, zobacz [formanty zawartości](../vsto/content-controls.md).

## <a name="add-content-controls-at-design-time"></a><a name="designtime"></a> Dodawanie kontrolek zawartości w czasie projektowania
 Istnieje kilka sposobów dodawania kontrolek zawartości do dokumentu w projekcie na poziomie dokumentu w czasie projektowania:

- Dodaj kontrolkę zawartość z karty **formanty słowa** w **przyborniku**.

- Dodaj kontrolkę zawartości do dokumentu w taki sam sposób, jak dodać natywną kontrolkę zawartości w programie Word.

- Przeciągnij kontrolkę zawartość do dokumentu z okna **źródła danych** . Jest to przydatne, gdy chcesz powiązać formant z danymi podczas tworzenia formantu. Aby uzyskać więcej informacji, zobacz [How to: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md) i [instrukcje: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Aby dodać kontrolkę zawartości do dokumentu przy użyciu przybornika

1. W dokumencie, który jest hostowany w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie, umieść kursor, do którego chcesz dodać formant zawartości, lub zaznacz tekst, który ma zostać zastąpiony przez formant zawartości.

2. Otwórz **Przybornik** i kliknij kartę **formanty wyrazów** .

3. Dodaj kontrolkę jeden z następujących sposobów:

    - Kliknij dwukrotnie formant zawartości w **przyborniku**.

         lub

    - Kliknij kontrolkę zawartość w **przyborniku** , a następnie naciśnij klawisz **Enter** .

         lub

    - Przeciągnij kontrolkę zawartości z **przybornika** do dokumentu. Kontrolka zawartości zostanie dodana w bieżącym zaznaczeniu w dokumencie, a nie w lokalizacji wskaźnika myszy.

> [!NOTE]
> Nie można dodać <xref:Microsoft.Office.Tools.Word.GroupContentControl> za pomocą **przybornika**. Można dodać tylko w programie <xref:Microsoft.Office.Tools.Word.GroupContentControl> Word lub w czasie wykonywania.

> [!NOTE]
> Program Visual Studio nie udostępnia kontrolki zawartości pola wyboru w przyborniku. Aby dodać kontrolkę zawartości pola wyboru do dokumentu, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt programowo. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).

#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Aby dodać kontrolkę zawartości do dokumentu w programie Word

1. W dokumencie, który jest hostowany w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie, umieść kursor, do którego chcesz dodać formant zawartości, lub zaznacz tekst, który ma zostać zastąpiony przez formant zawartości.

2. Na wstążce kliknij kartę **deweloper** .

    > [!NOTE]
    > Jeśli karta **deweloper** nie jest widoczna, należy ją najpierw pokazać. Aby uzyskać więcej informacji, zobacz [jak: wyświetlić kartę Deweloper na Wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. W grupie **formanty** kliknij ikonę dla kontrolki zawartości, którą chcesz dodać.

## <a name="add-content-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Dodawanie kontrolek zawartości w czasie wykonywania w projekcie na poziomie dokumentu
 Kontrolki zawartości można dodawać programowo do dokumentu w czasie wykonywania przy użyciu metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości `ThisDocument` klasy w projekcie. Każda metoda ma trzy przeciążenia, których można użyć do dodania kontrolki zawartości w następujący sposób:

- Dodaj kontrolkę w bieżącym zaznaczeniu.

- Dodaj kontrolkę w określonym zakresie.

- Dodaj kontrolkę opartą na natywnej kontrolce zawartości w dokumencie.

  Dynamicznie utworzone kontrolki zawartości nie są utrwalane w dokumencie, gdy dokument jest zamknięty. Jednak natywny formant zawartości pozostaje w dokumencie. Możesz ponownie utworzyć formant zawartości, który jest oparty na natywnej kontrolce zawartości przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

> [!NOTE]
> Aby dodać kontrolkę zawartości pola wyboru do dokumentu w projekcie programu Word 2010, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Aby dodać kontrolkę zawartości w bieżącym zaznaczeniu

1. Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \<*control class*> (gdzie *Klasa sterowania* jest nazwą klasy kontrolki zawartości, która ma zostać dodana, taka jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) i która ma jeden parametr dla nazwy nowej kontrolki.

     Poniższy przykład kodu używa metody, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> Aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na początku dokumentu. Aby uruchomić ten kod, Dodaj kod do `ThisDocument` klasy w projekcie i Wywołaj `AddRichTextControlAtSelection` metodę z `ThisDocument_Startup` procedury obsługi zdarzeń.

     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]

### <a name="to-add-a-content-control-at-a-specified-range"></a>Aby dodać kontrolkę zawartości z określonym zakresem

1. Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \<*control class*> (gdzie *Klasa sterowania* jest nazwą klasy kontrolki zawartości, która ma zostać dodana, taka jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) i która ma <xref:Microsoft.Office.Interop.Word.Range> parametr.

     Poniższy przykład kodu używa metody, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> Aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na początku dokumentu. Aby uruchomić ten kod, Dodaj kod do `ThisDocument` klasy w projekcie i Wywołaj `AddRichTextControlAtRange` metodę z `ThisDocument_Startup` procedury obsługi zdarzeń.

     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]

### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Aby dodać kontrolkę zawartości opartą na natywnej kontrolce zawartości

1. Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \<*control class*> (gdzie *Klasa sterowania* jest nazwą klasy kontrolki zawartości, która ma zostać dodana, taka jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) i która ma `Microsoft.Office.Interop.Word.ContentControl` parametr.

     Poniższy przykład kodu używa metody, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> Aby utworzyć nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dla każdej natywnej kontrolki tekstu sformatowanego, która znajduje się w dokumencie. Aby uruchomić ten kod, Dodaj kod do `ThisDocument` klasy w projekcie i Wywołaj `CreateRichTextControlsFromNativeControls` metodę z `ThisDocument_Startup` procedury obsługi zdarzeń.

     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]

## <a name="add-content-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Dodawanie kontrolek zawartości w czasie wykonywania w projekcie dodatku narzędzi VSTO
 Formanty zawartości można dodawać programowo do dowolnego otwartego dokumentu w czasie wykonywania przy użyciu dodatku VSTO. W tym celu należy wygenerować <xref:Microsoft.Office.Tools.Word.Document> element hosta, który jest oparty na otwartym dokumencie, a następnie użyć metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości tego elementu hosta. Każda metoda ma trzy przeciążenia, których można użyć do dodania kontrolki zawartości w następujący sposób:

- Dodaj kontrolkę w bieżącym zaznaczeniu.

- Dodaj kontrolkę w określonym zakresie.

- Dodaj kontrolkę opartą na natywnej kontrolce zawartości w dokumencie.

  Dynamicznie utworzone kontrolki zawartości nie są utrwalane w dokumencie, gdy dokument jest zamknięty. Jednak natywny formant zawartości pozostaje w dokumencie. Możesz ponownie utworzyć formant zawartości, który jest oparty na natywnej kontrolce zawartości przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Utrwalanie formantów dynamicznych w dokumentach pakietu Office](../vsto/persisting-dynamic-controls-in-office-documents.md).

  Aby uzyskać więcej informacji na temat generowania elementów hosta w projektach dodatku VSTO, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

> [!NOTE]
> Aby dodać kontrolkę zawartości pola wyboru do dokumentu, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt. Aby uzyskać więcej informacji, zobacz [formanty zawartości](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Aby dodać kontrolkę zawartości w bieżącym zaznaczeniu

1. Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \<*control class*> (gdzie *Klasa sterowania* jest nazwą klasy kontrolki zawartości, która ma zostać dodana, taka jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) i która ma jeden parametr dla nazwy nowej kontrolki.

     Poniższy przykład kodu używa metody, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> Aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na początku aktywnego dokumentu. Aby uruchomić ten kod, Dodaj kod do `ThisAddIn` klasy w projekcie i Wywołaj `AddRichTextControlAtSelection` metodę z `ThisAddIn_Startup` procedury obsługi zdarzeń.

     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]

### <a name="to-add-a-content-control-at-a-specified-range"></a>Aby dodać kontrolkę zawartości z określonym zakresem

1. Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \<*control class*> (gdzie *Klasa sterowania* jest nazwą klasy kontrolki zawartości, która ma zostać dodana, taka jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) i która ma <xref:Microsoft.Office.Interop.Word.Range> parametr.

     Poniższy przykład kodu używa metody, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> Aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na początku aktywnego dokumentu. Aby uruchomić ten kod, Dodaj kod do `ThisAddIn` klasy w projekcie i Wywołaj `AddRichTextControlAtRange` metodę z `ThisAddIn_Startup` procedury obsługi zdarzeń.

     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]

#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Aby dodać kontrolkę zawartości opartą na natywnej kontrolce zawartości

1. Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \<*control class*> (gdzie *Klasa sterowania* jest nazwą klasy kontrolki zawartości, która ma zostać dodana, taka jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> ) i która ma `Microsoft.Office.Interop.Word.ContentControl` parametr.

     Poniższy przykład kodu używa metody, <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> Aby utworzyć nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dla każdej natywnej kontrolki tekstu sformatowanego, która znajduje się w dokumencie, po otwarciu dokumentu. Aby uruchomić ten kod, Dodaj kod do `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]

     W przypadku języka C# należy również dołączyć `Application_DocumentOpen` procedurę obsługi zdarzeń do <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzenia.

     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]

## <a name="see-also"></a>Zobacz także
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
