---
title: '2017: Dodawanie kontrolek zawartości do dokumentów programu Word'
description: Dowiedz się, że w projektach programu Word na poziomie dokumentu możesz dodawać kontrolki zawartości do dokumentu w projekcie w czasie projektowania lub w czasie uruchamiania.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a902e85f8c53aa7a3d1ebe3b6480a7c68fa60601
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827906"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>2017: Dodawanie kontrolek zawartości do dokumentów programu Word
  W projektach programu Word na poziomie dokumentu można dodawać kontrolki zawartości do dokumentu w projekcie w czasie projektowania lub w czasie uruchamiania. W projektach dodatku Word VSTO można dodawać kontrolki zawartości do dowolnego otwartego dokumentu w czasie uruchamiania.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 W tym temacie opisano następujące zadania:

- [Dodawanie kontrolek zawartości w czasie projektowania](#designtime)

- [Dodawanie kontrolek zawartości w czasie uruchamiania w projekcie na poziomie dokumentu](#runtimedoclevel)

- [Dodawanie kontrolek zawartości w czasie uruchamiania w projekcie dodatku VSTO](#runtimeaddin)

  Aby uzyskać informacje na temat kontrolek zawartości, zobacz [Kontrolki zawartości.](../vsto/content-controls.md)

## <a name="add-content-controls-at-design-time"></a><a name="designtime"></a> Dodawanie kontrolek zawartości w czasie projektowania
 Istnieje kilka sposobów dodawania kontrolek zawartości do dokumentu w projekcie na poziomie dokumentu w czasie projektowania:

- Dodaj kontrolkę zawartości z karty **Kontrolki programu Word** przybornika . 

- Dodaj kontrolkę zawartości do dokumentu w taki sam sposób, jak w przypadku dodawania kontrolki zawartości natywnej w programie Word.

- Przeciągnij kontrolkę zawartości do dokumentu z **okna Źródła** danych. Jest to przydatne, gdy chcesz powiązać kontrolkę z danymi po utworzeniu kontrolki. Aby uzyskać więcej informacji, zobacz How [to: Populate documents with data from objects](../vsto/how-to-populate-documents-with-data-from-objects.md) (Jak wypełnić dokumenty danymi z obiektów) i How [to: Populate documents with data from a database](../vsto/how-to-populate-documents-with-data-from-a-database.md)(Jak wypełnić dokumenty danymi z bazy danych).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Aby dodać kontrolkę zawartości do dokumentu przy użyciu przybornika

1. W dokumencie hostowanych w projektancie umieść kursor w miejscu, w którym chcesz dodać kontrolkę zawartości, lub wybierz tekst, który ma zostać zastąpiony przez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kontrolkę zawartości.

2. Otwórz **przybornik i** kliknij **kartę Kontrolki** programu Word.

3. Dodaj kontrolkę na jeden z następujących sposobów:

    - Kliknij dwukrotnie kontrolkę zawartości w **przyborniku**.

         lub

    - Kliknij kontrolkę zawartości w **przyborniku,** a następnie naciśnij klawisz **Enter.**

         lub

    - Przeciągnij kontrolkę zawartości z **przybornika** do dokumentu. Kontrolka zawartości jest dodawana przy bieżącym zaznaczeniu w dokumencie, a nie w lokalizacji wskaźnika myszy.

> [!NOTE]
> Nie można dodać przy <xref:Microsoft.Office.Tools.Word.GroupContentControl> użyciu **przybornika**. Możesz dodać tylko w <xref:Microsoft.Office.Tools.Word.GroupContentControl> programie Word lub w czasie uruchamiania.

> [!NOTE]
> Visual Studio nie zapewnia kontrolki zawartości pola wyboru w przyborniku. Aby dodać kontrolkę zawartości pola wyboru do dokumentu, należy utworzyć obiekt <xref:Microsoft.Office.Tools.Word.ContentControl> programowo. Aby uzyskać więcej informacji, zobacz [Kontrolki zawartości](../vsto/content-controls.md).

#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Aby dodać kontrolkę zawartości do dokumentu w programie Word

1. W dokumencie hostowany w projektancie umieść kursor w miejscu, w którym chcesz dodać kontrolkę zawartości, lub wybierz tekst, który ma zostać zastąpiony przez [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] kontrolkę zawartości.

2. Na wstążce kliknij **kartę Deweloper.**

    > [!NOTE]
    > Jeśli karta **Deweloper** nie jest widoczna, musisz ją najpierw wyświetlić. Aby uzyskać więcej informacji, [zobacz Jak wyświetlić kartę Deweloper na wstążce](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

3. W grupie **Kontrolki** kliknij ikonę kontrolki zawartości, którą chcesz dodać.

## <a name="add-content-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Dodawanie kontrolek zawartości w czasie uruchamiania w projekcie na poziomie dokumentu
 Kontrolki zawartości można dodać programowo do dokumentu w czasie działania przy użyciu metod właściwości <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> `ThisDocument` klasy w projekcie. Każda metoda ma trzy przeciążenia, których można użyć, aby dodać kontrolkę zawartości w następujący sposób:

- Dodaj kontrolkę przy bieżącym zaznaczeniu.

- Dodaj kontrolkę w określonym zakresie.

- Dodaj kontrolkę, która jest oparta na natywnej kontrolce zawartości w dokumencie.

  Dynamicznie tworzone kontrolki zawartości nie są utrwalane w dokumencie po zamknięciu dokumentu. Jednak w dokumencie pozostaje natywna kontrolka zawartości. Kontrolkę zawartości opartą na natywnej kontrolce zawartości można odtworzyć przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym.](../vsto/adding-controls-to-office-documents-at-run-time.md)

> [!NOTE]
> Aby dodać kontrolkę zawartości pola wyboru do dokumentu w projekcie programu Word 2010, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt . Aby uzyskać więcej informacji, zobacz [Kontrolki zawartości](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Aby dodać kontrolkę zawartości przy bieżącym zaznaczeniu

1. Użyj metody, która ma nazwę (gdzie klasa sterowania jest nazwą klasy kontrolki zawartości, którą chcesz dodać, na przykład ), i która ma jeden parametr dla nazwy nowej <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*>  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> kontrolki.

     W poniższym przykładzie kodu użyto metody , aby dodać nową <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na początku dokumentu. Aby uruchomić ten kod, dodaj kod do klasy w projekcie i wywołaj `ThisDocument` metodę z procedury obsługi `AddRichTextControlAtSelection` `ThisDocument_Startup` zdarzeń.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet700":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet700":::

### <a name="to-add-a-content-control-at-a-specified-range"></a>Aby dodać kontrolkę zawartości w określonym zakresie

1. Użyj metody, która ma nazwę (gdzie klasa sterowania jest nazwą klasy kontroli zawartości, którą chcesz dodać, na przykład ), i która <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> ma parametr  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> <xref:Microsoft.Office.Interop.Word.Range> .

     W poniższym przykładzie kodu użyto metody , aby dodać nową <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> na początku dokumentu. Aby uruchomić ten kod, dodaj kod do klasy w projekcie i wywołaj `ThisDocument` metodę z procedury obsługi `AddRichTextControlAtRange` `ThisDocument_Startup` zdarzeń.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet701":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet701":::

### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Aby dodać kontrolkę zawartości opartą na natywnej kontrolce zawartości

1. Użyj metody, która ma nazwę (gdzie klasa sterowania jest nazwą klasy kontroli zawartości, którą chcesz dodać, na przykład ), i która <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> ma parametr  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> `Microsoft.Office.Interop.Word.ContentControl` .

     W poniższym przykładzie kodu użyto metody , aby utworzyć nową dla każdej natywnej kontrolki tekstu <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> sformatowanego, która znajduje się w dokumencie. Aby uruchomić ten kod, dodaj kod do klasy w projekcie `ThisDocument` i wywołaj `CreateRichTextControlsFromNativeControls` metodę z procedury `ThisDocument_Startup` obsługi zdarzeń.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet702":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet702":::

## <a name="add-content-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a> Dodawanie kontrolek zawartości w czasie uruchamiania w projekcie dodatku VSTO
 Kontrolki zawartości można dodać programowo do dowolnego otwartego dokumentu w czasie uruchamiania przy użyciu dodatku VSTO. W tym celu wygeneruj element hosta oparty na otwartym dokumencie, a następnie użyj metod właściwości <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> tego elementu hosta. Każda metoda ma trzy przeciążenia, których można użyć, aby dodać kontrolkę zawartości w następujący sposób:

- Dodaj kontrolkę przy bieżącym zaznaczeniu.

- Dodaj kontrolkę w określonym zakresie.

- Dodaj kontrolkę opartą na natywnej kontrolce zawartości w dokumencie.

  Dynamicznie tworzone kontrolki zawartości nie są utrwalane w dokumencie po zamknięciu dokumentu. Jednak w dokumencie pozostaje natywna kontrolka zawartości. Kontrolkę zawartości opartą na natywnej kontrolce zawartości można odtworzyć przy następnym otwarciu dokumentu. Aby uzyskać więcej informacji, zobacz [Utrwalanie kontrolek dynamicznych w dokumentach pakietu Office.](../vsto/persisting-dynamic-controls-in-office-documents.md)

  Aby uzyskać więcej informacji na temat generowania elementów hosta w projektach dodatków VSTO, zobacz Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatekach [VSTO w czasie uruchamiania.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

> [!NOTE]
> Aby dodać kontrolkę zawartości pola wyboru do dokumentu, należy utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt . Aby uzyskać więcej informacji, zobacz [Kontrolki zawartości](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Aby dodać kontrolkę zawartości przy bieżącym zaznaczeniu

1. Użyj metody o nazwie (gdzie klasa steruje jest nazwą klasy kontrolki zawartości, którą chcesz dodać, na przykład ), i która ma jeden parametr dla nazwy nowej <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*>  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> kontrolki.

     W poniższym przykładzie kodu <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> użyto metody , aby dodać nowy na początku aktywnego <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dokumentu. Aby uruchomić ten kod, dodaj kod do klasy w projekcie `ThisAddIn` i wywołaj `AddRichTextControlAtSelection` metodę z procedury `ThisAddIn_Startup` obsługi zdarzeń.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet1":::

### <a name="to-add-a-content-control-at-a-specified-range"></a>Aby dodać kontrolkę zawartości w określonym zakresie

1. Użyj metody, która ma nazwę (gdzie klasa sterowania jest nazwą klasy kontroli zawartości, którą chcesz dodać, na przykład ), i która <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> ma parametr  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> <xref:Microsoft.Office.Interop.Word.Range> .

     W poniższym przykładzie kodu użyto metody , aby dodać nową na <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> początku aktywnego <xref:Microsoft.Office.Tools.Word.RichTextContentControl> dokumentu. Aby uruchomić ten kod, dodaj kod do klasy w projekcie i wywołaj `ThisAddIn` metodę z procedury obsługi `AddRichTextControlAtRange` `ThisAddIn_Startup` zdarzeń.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet2":::

#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Aby dodać kontrolkę zawartości opartą na natywnej kontrolce zawartości

1. Użyj metody, która ma nazwę (gdzie klasa sterowania jest nazwą klasy kontroli zawartości, którą chcesz dodać, na przykład ), i która <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> ma parametr  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> `Microsoft.Office.Interop.Word.ContentControl` .

     W poniższym przykładzie kodu użyto metody , aby utworzyć nową dla każdej natywnej kontrolki tekstu sformatowanego, która znajduje się w dokumencie <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> <xref:Microsoft.Office.Tools.Word.RichTextContentControl> po otwarciu dokumentu. Aby uruchomić ten kod, dodaj kod do `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet3":::

     W przypadku języka C# należy również dołączyć do zdarzenia `Application_DocumentOpen` program obsługi <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> zdarzeń.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet6":::

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Omówienie elementów hosta i kontrolek hosta](../vsto/host-items-and-host-controls-overview.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Programowe ograniczenia elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Zaprogramowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
