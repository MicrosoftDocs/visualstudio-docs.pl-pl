---
title: 'Instrukcje: Dodaj zawartość formantów do dokumentów programu Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8a7f99768236c8945fe82645c70c586361edcdde
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53648049"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Instrukcje: Dodaj zawartość formantów do dokumentów programu Word
  W projektach programu Word na poziomie dokumentu można dodać formanty zawartości do dokumentu w projekcie w czasie projektowania lub w czasie wykonywania. W projektach dodatku narzędzi VSTO programu Word można dodać formanty zawartości dowolnego otwartego dokumentu w czasie wykonywania.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 W tym temacie opisano następujące zadania:  
  
- [Dodawanie formantów zawartości w czasie projektowania](#designtime)  
  
- [Dodawanie formantów zawartości w czasie wykonywania w projekcie na poziomie dokumentu](#runtimedoclevel)  
  
- [Dodawanie formantów zawartości w czasie wykonywania w projekcie dodatku narzędzi VSTO](#runtimeaddin)  
  
  Aby uzyskać informacje o formantach zawartości, zobacz [udostępnia mechanizmy kontroli zawartości](../vsto/content-controls.md).  
  
##  <a name="designtime"></a> Dodaj zawartość kontrolki w czasie projektowania  
 Istnieje kilka sposobów, aby dodać formanty zawartości do dokumentu w projekcie na poziomie dokumentu w czasie projektowania:  
  
- Dodaj kontrolkę zawartości z **formanty programu Word** karcie **przybornika**.  
  
- Dodawanie zawartości kontrolki do dokumentu w taki sam sposób możesz dodać macierzystym formancie zawartości w programie Word.  
  
- Przeciągnij formant zawartości do dokumentu z **źródeł danych** okna. Jest to przydatne, jeśli chcesz powiązać kontrolkę z danymi, po utworzeniu kontrolki. Aby uzyskać więcej informacji, zobacz [jak: Zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md) i [jak: Zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Aby dodać kontrolkę zawartości w dokumencie za pomocą przybornika  
  
1.  W dokumencie, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta, umieścić kursor, w której chcesz dodać formant zawartości lub zaznacz tekst, który ma formant zawartości w celu zastąpienia.  
  
2.  Otwórz **przybornika** i kliknij przycisk **formanty programu Word** kartę.  
  
3.  Dodaj kontrolkę, jeden z następujących sposobów:  
  
    -   Kliknij dwukrotnie formant zawartości w **przybornika**.  
  
         lub  
  
    -   Kliknij kontrolkę zawartości w **przybornika** , a następnie naciśnij klawisz **Enter** klucza.  
  
         lub  
  
    -   Przeciągnij formant zawartości z **przybornika** do dokumentu. Zawartość formant jest dodawany, bieżące zaznaczenie w dokumencie, a nie lokalizacja wskaźnika myszy.  
  
> [!NOTE]  
>  Nie można dodać <xref:Microsoft.Office.Tools.Word.GroupContentControl> przy użyciu **przybornika**. Możesz dodawać tylko <xref:Microsoft.Office.Tools.Word.GroupContentControl> w programie Word lub w czasie wykonywania.  
  
> [!NOTE]  
>  Program Visual Studio nie zapewnia kontrolkę zawartości pola wyboru w przyborniku. Aby dodać kontrolkę zawartości pola wyboru do dokumentu, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu programowo. Aby uzyskać więcej informacji, zobacz [udostępnia mechanizmy kontroli zawartości](../vsto/content-controls.md).  
  
#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Aby dodać kontrolkę zawartości do dokumentu programu Word  
  
1.  W dokumencie, który znajduje się w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta, umieścić kursor, w której chcesz dodać formant zawartości lub zaznacz tekst, który ma formant zawartości w celu zastąpienia.  
  
2.  Na wstążce kliknij **Developer** kartę.  
  
    > [!NOTE]  
    >  Jeśli **Developer** karta nie jest widoczna, najpierw musisz wyświetlić. Aby uzyskać więcej informacji, zobacz [jak: Pokazywanie karty dewelopera na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  W **formantów** grupy, kliknij ikonę formantu zawartości, który chcesz dodać.  
  
##  <a name="runtimedoclevel"></a> Dodawanie formantów zawartości w czasie wykonywania w projekcie na poziomie dokumentu  
 Można dodać formanty zawartości programowo do dokumentu w czasie wykonywania za pomocą metody <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwość `ThisDocument` klasy w projekcie. Każda metoda charakteryzuje się trzech przeciążeń, które można użyć, aby dodać kontrolkę zawartości w następujący sposób:  
  
- Dodaj kontrolkę na bieżącym zaznaczeniu.  
  
- Dodawanie kontrolki w określonym zakresie.  
  
- Dodaj kontrolkę, która opiera się na macierzystym formancie zawartości w dokumencie.  
  
  Tworzone dynamicznie zawartość, którą formanty nie są zachowywane w dokumencie, gdy dokument zostanie zamknięty. Jednak macierzystym formancie zawartości pozostaje w dokumencie. Można ponownie utworzyć kontrolkę zawartości, która opiera się na macierzystym formancie zawartości przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [dodawanie formantów do dokumentów pakietu Office w środowisku uruchomieniowym](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
> [!NOTE]  
>  Aby dodać kontrolkę zawartości pola wyboru do dokumentu w projekcie programu Word 2010, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu. Aby uzyskać więcej informacji, zobacz [udostępnia mechanizmy kontroli zawartości](../vsto/content-controls.md).  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>Aby dodać kontrolkę zawartości w bieżącym zaznaczeniu  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy z formantu zawartości, który chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i który ma jeden parametr dla nazwy nowego formantu.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodę, aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do początku dokumentu. Aby uruchomić ten kod, Dodaj kod, aby `ThisDocument` klasy w projekcie i Wywołaj `AddRichTextControlAtSelection` metody z `ThisDocument_Startup` programu obsługi zdarzeń.  
  
     [!code-csharp[Trin_ContentControlReference#700](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#700)]
     [!code-vb[Trin_ContentControlReference#700](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#700)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>Aby dodać kontrolkę zawartości w określonym zakresie  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu zawartości, którą chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i ma <xref:Microsoft.Office.Interop.Word.Range> parametru.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodę, aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> do początku dokumentu. Aby uruchomić ten kod, Dodaj kod, aby `ThisDocument` klasy w projekcie i Wywołaj `AddRichTextControlAtRange` metody z `ThisDocument_Startup` programu obsługi zdarzeń.  
  
     [!code-csharp[Trin_ContentControlReference#701](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#701)]
     [!code-vb[Trin_ContentControlReference#701](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#701)]  
  
### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Aby dodać kontrolkę zawartości, która opiera się na macierzystym formancie zawartości  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu zawartości, którą chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i ma `Microsoft.Office.Interop.Word.ContentControl` parametru.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodę, aby utworzyć nową <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dla każdego formantu natywnych tekstu sformatowanego, który znajduje się w dokumencie. Aby uruchomić ten kod, Dodaj kod, aby `ThisDocument` klasy w projekcie i Wywołaj `CreateRichTextControlsFromNativeControls` metody z `ThisDocument_Startup` programu obsługi zdarzeń.  
  
     [!code-csharp[Trin_ContentControlReference#702](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs#702)]
     [!code-vb[Trin_ContentControlReference#702](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb#702)]  
  
##  <a name="runtimeaddin"></a> Dodawanie formantów zawartości w czasie wykonywania w projekcie dodatku narzędzi VSTO  
 Można dodać formanty zawartości programowo dowolnego otwartego dokumentu w czasie wykonywania za pomocą dodatku narzędzi VSTO. Aby to zrobić, należy wygenerować <xref:Microsoft.Office.Tools.Word.Document> elementu, która jest oparta na otwartym dokumencie hosta, a następnie użyj metod <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> właściwości tego elementu host. Każda metoda charakteryzuje się trzech przeciążeń, które można użyć, aby dodać kontrolkę zawartości w następujący sposób:  
  
- Dodaj kontrolkę na bieżącym zaznaczeniu.  
  
- Dodawanie kontrolki w określonym zakresie.  
  
- Dodaj kontrolkę, która opiera się na macierzystym formancie zawartości w dokumencie.  
  
  Tworzone dynamicznie zawartość, którą formanty nie są zachowywane w dokumencie, gdy dokument zostanie zamknięty. Jednak macierzystym formancie zawartości pozostaje w dokumencie. Można ponownie utworzyć kontrolkę zawartości, która opiera się na macierzystym formancie zawartości przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [kontrolek dynamicznych w dokumentach pakietu Office utrwalenia](../vsto/persisting-dynamic-controls-in-office-documents.md).  
  
  Aby uzyskać więcej informacji na temat generowania elementów hosta w projektach dodatku narzędzi VSTO dla programów, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
> [!NOTE]  
>  Aby dodać kontrolkę zawartości pola wyboru do dokumentu, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu. Aby uzyskać więcej informacji, zobacz [udostępnia mechanizmy kontroli zawartości](../vsto/content-controls.md).  
  
### <a name="to-add-a-content-control-at-the-current-selection"></a>Aby dodać kontrolkę zawartości w bieżącym zaznaczeniu  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy z formantu zawartości, który chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i który ma jeden parametr dla nazwy nowego formantu.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodę, aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na początku aktywnego dokumentu. Aby uruchomić ten kod, Dodaj kod, aby `ThisAddIn` klasy w projekcie i Wywołaj `AddRichTextControlAtSelection` metody z `ThisAddIn_Startup` programu obsługi zdarzeń.  
  
     [!code-vb[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#1)]
     [!code-csharp[Trin_WordAddInDynamicControls#1](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#1)]  
  
### <a name="to-add-a-content-control-at-a-specified-range"></a>Aby dodać kontrolkę zawartości w określonym zakresie  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu zawartości, którą chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i ma <xref:Microsoft.Office.Interop.Word.Range> parametru.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodę, aby dodać nowy <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na początku aktywnego dokumentu. Aby uruchomić ten kod, Dodaj kod, aby `ThisAddIn` klasy w projekcie i Wywołaj `AddRichTextControlAtRange` metody z `ThisAddIn_Startup` programu obsługi zdarzeń.  
  
     [!code-vb[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#2)]
     [!code-csharp[Trin_WordAddInDynamicControls#2](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#2)]  
  
#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Aby dodać kontrolkę zawartości, która opiera się na macierzystym formancie zawartości  
  
1.  Użyj <xref:Microsoft.Office.Tools.Word.ControlCollection> metody, która ma nazwę `Add` \< *kontrolować klasy*> (gdzie *kontrolować klasy* jest nazwą klasy formantu zawartości, którą chcesz dodać, takich jak <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A>), i ma `Microsoft.Office.Interop.Word.ContentControl` parametru.  
  
     Poniższy przykład kodu wykorzystuje <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> metodę, aby utworzyć nową <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dla każdego formantu natywnych tekstu sformatowanego, który znajduje się w dokumencie, po otwarciu dokumentu. Aby uruchomić ten kod, Dodaj kod, aby `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#3)]
     [!code-csharp[Trin_WordAddInDynamicControls#3](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#3)]  
  
     Dla języka C#, musisz również dołączyć `Application_DocumentOpen` procedurę obsługi zdarzeń do <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzeń.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#6](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#6)]  
  
## <a name="see-also"></a>Zobacz także  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Dodawanie formantów do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)   
 [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)  
  