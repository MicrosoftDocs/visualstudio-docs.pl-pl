---
title: Kontrolki zawartości
description: Poznaj kontrolki zawartości i sposób, w jaki formanty zawartości umożliwiają projektowanie dokumentów i szablonów.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: ce692bf10c5473c648fd6587b6b6568d369ed496
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948000"
---
# <a name="content-controls"></a>Kontrolki zawartości
  Formanty zawartości umożliwiają projektowanie dokumentów i szablonów, które mają następujące funkcje:

- Interfejs użytkownika, który ma kontrolowane dane wejściowe, takie jak formularz.

- Ograniczenia, które uniemożliwiają użytkownikom edytowanie chronionych sekcji dokumentu lub szablonu. Aby uzyskać więcej informacji, zobacz [ochrona części dokumentów za pomocą kontrolek zawartości](#Protection).

- Powiązanie danych ze źródłem danych. Aby uzyskać więcej informacji, zobacz temat [Powiązywanie danych z kontrolkami zawartości](#DataBinding).

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  ![link do wideo](../vsto/media/playvideo.gif "link do wideo") Aby zapoznać się z pokrewną prezentacją wideo, zobacz temat [Powiązywanie danych z kontrolkami zawartości programu Word 2007 przy użyciu Visual Studio Tools dla systemu Office (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="overview-of-content-controls"></a>Przegląd formantów zawartości
 Formanty zawartości udostępniają interfejs użytkownika zoptymalizowany pod kątem zarówno danych wejściowych użytkownika, jak i drukowania. Po dodaniu kontrolki zawartości do dokumentu formant jest identyfikowany za pomocą obramowania, tytułu i tekstu tymczasowego, który może dostarczyć użytkownikowi instrukcje. Obramowanie i tytuł kontrolki nie są wyświetlane w drukowanych wersjach dokumentu.

 Na przykład jeśli chcesz, aby użytkownik wprowadził datę w sekcji dokumentu, możesz dodać kontrolkę zawartości selektora dat do dokumentu. Po kliknięciu kontrolki przez użytkownika zostanie wyświetlony standardowy interfejs użytkownika selektora dat. Można również ustawić właściwości kontrolki, aby ustawić kalendarz regionalny, który jest wyświetlany, i określić format daty. Gdy użytkownik wybierze datę, interfejs użytkownika kontrolki jest ukryty i tylko data jest wyświetlana, jeśli użytkownik drukuje dokument.

 Formanty zawartości ułatwiają również wykonywanie następujących czynności:

- Uniemożliwiaj użytkownikom edytowanie lub usuwanie części dokumentu. Jest to przydatne, jeśli masz informacje w dokumencie lub szablonie, które użytkownicy powinni mieć możliwość odczytu, ale nie do edycji, lub jeśli chcesz, aby użytkownicy mogli edytować kontrolki zawartości, ale nie mogą ich usuwać.

- Powiąż części dokumentu lub szablonu z danymi. Można powiązać kontrolki zawartości z polami bazy danych, obiektami zarządzanymi w [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] elementach XML, które są przechowywane w dokumencie i innych źródłach danych.

  W projektach na poziomie dokumentu można dodawać kontrolki zawartości do dokumentu w czasie projektowania lub w czasie wykonywania. W projektach dodatku VSTO można dodać kontrolki zawartości do dowolnych otwartych dokumentów w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).

> [!NOTE]
> Kontrolki zawartości można używać tylko w dokumentach, które są zapisane w formacie Open XML. Nie można używać kontrolek zawartości w dokumentach, które są zapisane w formacie dokumentu programu Word 97-2003 (*doc*).

## <a name="types-of-content-controls"></a>Typy kontrolek zawartości
 Istnieją dziewięć różnych typów formantów zawartości, które można dodać do dokumentów. Większość formantów zawartości ma odpowiedni typ w <xref:Microsoft.Office.Tools.Word> przestrzeni nazw. Można również użyć generycznej <xref:Microsoft.Office.Tools.Word.ContentControl> , która może reprezentować dowolne dostępne kontrolki zawartości. Aby zapoznać się z przewodnikiem, który pokazuje, jak używać poszczególnych dostępnych kontrolek zawartości, zobacz [Przewodnik: Tworzenie szablonu za pomocą formantów zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

### <a name="build-block-gallery"></a>Galeria bloków kompilacji
 Galeria bloków konstrukcyjnych umożliwia użytkownikom wybranie z listy *bloków konstrukcyjnych dokumentów* do wstawienia do dokumentu. Blok konstrukcyjny dokumentu to fragment zawartości, który został utworzony do użycia wiele razy, na przykład wspólna strona tytułowa, sformatowana tabela lub nagłówek. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> Typ. Aby uzyskać więcej informacji na temat bloków konstrukcyjnych, zobacz [co nowego dla deweloperów w programie Word 2007](/previous-versions/office/developer/office-2007/bb266218(v=office.12)).

### <a name="check-box"></a>Pole wyboru
 Pole wyboru zawiera interfejs użytkownika, który reprezentuje stan binarny: wybrane lub wyczyszczone.

 W przeciwieństwie do innych typów kontrolek zawartości nie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zapewnia określonego typu, który reprezentuje kontrolkę zawartości pola wyboru. Innymi słowy, nie ma `CheckBoxContentControl` typu. Jednak nadal można utworzyć kontrolkę zawartości pola wyboru, dodając ogólny <xref:Microsoft.Office.Tools.Word.ContentControl> dokument do dokumentu. Aby uzyskać więcej informacji, zobacz [kontrolki zawartości pól wyboru w projektach programu Word](#checkbox).

### <a name="combo-box"></a>Pole kombi
 Pole kombi wyświetla listę elementów, które użytkownicy mogą wybrać. W przeciwieństwie do listy rozwijanej, pole kombi umożliwia użytkownikom dodawanie własnych elementów. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> Typ.

### <a name="date-picker"></a>Wybór daty
 Selektor daty zawiera interfejs użytkownika kalendarza służący do wybierania daty. Kalendarz pojawia się, gdy użytkownik końcowy kliknie strzałkę listy rozwijanej w kontrolce. Można użyć kalendarzy regionalnych i różnych formatów daty. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> Typ.

### <a name="drop-down-list"></a>Lista rozwijana
 Lista rozwijana zawiera listę elementów, które użytkownicy mogą wybrać. W przeciwieństwie do pola kombi, lista rozwijana nie zezwala użytkownikom na dodawanie i edytowanie elementów. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> Typ.

### <a name="group"></a>Group (Grupa)
 Kontrolka grupy definiuje chroniony region dokumentu, którego użytkownicy nie mogą edytować ani usuwać. Kontrolka grupy może zawierać dowolne elementy dokumentu, takie jak tekst, tabele, grafika i inne kontrolki zawartości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.GroupContentControl> Typ.

### <a name="picture"></a>Obraz
 Kontrolka obrazu wyświetla obraz. Możesz określić obraz w czasie projektowania lub w czasie wykonywania lub kliknąć ten formant, aby wybrać obraz do wstawienia do dokumentu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.PictureContentControl> Typ.

### <a name="rich-text"></a>Tekst sformatowany
 Kontrolka tekstu sformatowanego zawiera tekst lub inne elementy, takie jak tabele, obrazy lub inne kontrolki zawartości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.RichTextContentControl> Typ.

### <a name="plain-text"></a>Zwykły tekst
 Formant w postaci zwykłego tekstu zawiera tekst. Kontrolka zwykłego tekstu nie może zawierać innych elementów, takich jak tabele, obrazy ani inne kontrolki zawartości. Ponadto cały tekst w kontrolce zwykłego tekstu ma takie samo formatowanie. Na przykład, jeśli użytkownik ma kursywę jeden wyraz zdania, który znajduje się w kontrolce zwykłego tekstu, cały tekst wewnątrz kontrolki jest pisany kursywą. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> Typ.

### <a name="generic-content-control"></a>Ogólna kontrola zawartości
 Ogólny formant zawartości jest <xref:Microsoft.Office.Tools.Word.ContentControl> obiektem, który może reprezentować dowolny z dostępnych typów kontrolek zawartości. Można zmienić obiekt, <xref:Microsoft.Office.Tools.Word.ContentControl> Aby zachować taki jak inny typ kontrolki zawartości przy użyciu <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> właściwości. Na przykład jeśli utworzysz <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt, który reprezentuje kontrolkę zwykłego tekstu, możesz ją zmienić w czasie wykonywania, tak aby była zachowywać się jak pole kombi.

 Obiekty można tworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> tylko w czasie wykonywania, a nie w czasie projektowania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).

## <a name="common-features-of-content-controls"></a>Typowe funkcje formantów zawartości
 Większość formantów zawartości udostępnia zestaw elementów członkowskich, których można użyć do wykonywania typowych zadań. W poniższej tabeli opisano niektóre zadania, które można wykonać za pomocą tych elementów członkowskich.

|Dla tego zadania:|Wykonaj następujące czynności:|
|--------------------|--------------|
|Pobierz lub Ustaw tekst wyświetlany w kontrolce.|Użyj właściwości **Text** . **Uwaga:**  <xref:Microsoft.Office.Tools.Word.PictureContentControl> Typy i <xref:Microsoft.Office.Tools.Word.ContentControl> nie mają tej właściwości.|
|Pobieranie lub Ustawianie tymczasowego tekstu wyświetlanego w kontrolce do momentu, gdy użytkownik edytuje formant, formant zostanie wypełniony danymi ze źródła danych lub zawartość kontrolki zostanie usunięta.|Użyj właściwości **PlaceholderText** . **Uwaga:**  <xref:Microsoft.Office.Tools.Word.PictureContentControl> Typ nie ma tej właściwości.|
|Pobierz lub ustaw tytuł, który będzie wyświetlany w obramowaniu kontrolki zawartości, gdy użytkownik ją klika.|Użyj właściwości **title** .|
|Automatycznie Usuń kontrolkę z dokumentu po przeprowadzeniu edycji kontrolki przez użytkownika. (Tekst w kontrolce pozostanie w dokumencie).|Użyj właściwości **tymczasowej** .|
|Uruchamiaj kod, gdy użytkownik kliknie w kontrolce zawartości lub gdy kursor zostanie przesunięty do formantu zawartości programowo.|Obsłuż <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> zdarzenie formantu.|
|Uruchamiaj kod, gdy użytkownik kliknie poza kontrolką zawartości lub gdy kursor zostanie przesunięty poza formant zawartości programowo.|Obsłuż <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> zdarzenie formantu.|
|Uruchom kod po dodaniu kontrolki Content do dokumentu w wyniku operacji wykonaj ponownie lub Cofnij.|Obsłuż <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> zdarzenie formantu.|
|Uruchom kod tuż przed usunięciem formantu zawartości z dokumentu.|Obsłuż <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> zdarzenie formantu.|

## <a name="protect-parts-of-documents-by-using-content-controls"></a><a name="Protection"></a> Ochrona części dokumentów za pomocą kontrolek zawartości
 W przypadku ochrony części dokumentu uniemożliwiają użytkownikom zmianę lub usunięcie zawartości w tej części dokumentu. Istnieje kilka sposobów ochrony części dokumentu przy użyciu kontrolek zawartości.

 Jeśli obszar, który ma być chroniony, znajduje się wewnątrz kontrolki zawartości, można użyć właściwości kontrolki zawartość, aby uniemożliwić użytkownikom edytowanie lub usuwanie kontrolki:

- Właściwość **LockContents** uniemożliwia użytkownikom edytowanie zawartości.

- Właściwość **LockContentControl** uniemożliwia użytkownikom usuwanie kontrolek.

  Jeśli obszar, który ma zostać objęty ochroną, nie znajduje się w kontrolce zawartości, lub jeśli chcesz chronić obszar, który zawiera kontrolki zawartości i inne typy zawartości, możesz umieścić cały obszar w <xref:Microsoft.Office.Tools.Word.GroupContentControl> . W przeciwieństwie do innych kontrolek zawartości a <xref:Microsoft.Office.Tools.Word.GroupContentControl> nie oferuje interfejsu użytkownika, który jest widoczny dla użytkownika. Jedynym celem jest zdefiniowanie regionu, którego użytkownicy nie mogą edytować.

> [!NOTE]
> W przypadku utworzenia, <xref:Microsoft.Office.Tools.Word.GroupContentControl> który zawiera osadzone kontrolki zawartości, osadzone kontrolki zawartości nie są automatycznie chronione. Aby uniemożliwić użytkownikom edytowanie ich zawartości, należy użyć właściwości **LockContents** każdego osadzonego formantu.

 Aby uzyskać więcej informacji na temat używania formantów zawartości do ochrony części dokumentów, zobacz [jak: ochrona części dokumentów za pomocą kontrolek zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="bind-data-to-content-controls"></a><a name="DataBinding"></a> Powiązywanie danych z kontrolkami zawartości
 Dane można wyświetlać w dokumentach przez powiązanie kontrolki zawartości ze źródłem danych. Po zaktualizowaniu źródła danych kontrolka zawartości odzwierciedla zmiany. Możesz również zapisać zmiany w źródle danych.

 Formanty zawartości zapewniają następujące opcje powiązań danych:

- Formanty zawartości można powiązać z polami bazy danych lub obiektami zarządzanymi przy użyciu tego samego modelu powiązań danych co Windows Forms.

- Można powiązać kontrolki zawartości z elementami w fragmentach kodu XML (nazywanych również *niestandardowymi składnikami XML*), które są osadzone w dokumencie.

  Aby zapoznać się z omówieniem powiązań formantów hosta w rozwiązaniach pakietu Office do danych, zobacz temat [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="use-the-windows-forms-data-binding-model"></a>Użyj modelu powiązań danych Windows Forms
 Większość formantów zawartości obsługuje prosty model powiązań danych, którego Windows Forms używa. Proste powiązanie danych oznacza, że formant jest powiązany z pojedynczym elementem danych, takim jak wartość w kolumnie tabeli danych. Aby uzyskać więcej informacji, zobacz temat [powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 W projektach na poziomie dokumentu można powiązać dane z kontrolkami zawartości przy użyciu okna **źródła danych** w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Aby uzyskać więcej informacji na temat dodawania kontroli zawartości powiązanej z danymi do dokumentów, zobacz [How to: zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md) i [instrukcje: zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md).

 Poniższa tabela zawiera listę kontrolek zawartości, które można powiązać z każdym typem danych w oknie **źródła danych** .

|Typ danych|Domyślna kontrolka zawartości|Inne kontrolki zawartości, które mogą być powiązane z tym typem danych|
|---------------|-----------------------------|----------------------------------------------------------------|
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> macierzy|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Brak|

 W projektach z dodatkiem na poziomie dokumentu i narzędzi VSTO można w sposób programowy powiązać kontrolkę zawartości ze źródłem danych za pomocą <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> właściwości formantu. Jeśli to zrobisz, Przekaż **tekst** ciągu do parametru *PropertyName* <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody. Właściwość **Text** jest domyślną właściwością powiązania danych w kontrolkach zawartości.

 Formanty zawartości obsługują również dwukierunkowe powiązanie danych, w których zmiany w formancie są aktualizowane do źródła danych. Aby uzyskać więcej informacji, zobacz [jak: aktualizowanie źródła danych przy użyciu danych z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

> [!NOTE]
> Formanty zawartości nie obsługują złożonych powiązań danych. W przypadku powiązania a <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> lub <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> ze źródłem danych przy użyciu modelu danych Windows Forms użytkownicy będą widzieć tylko jedną wartość po kliknięciu kontrolki. Jeśli chcesz powiązać te kontrolki z zestawem wartości danych, z których użytkownicy mogą wybierać, możesz powiązać te kontrolki z elementami w niestandardowym składniku XML.

### <a name="bind-content-controls-to-custom-xml-parts"></a>Powiązywanie kontrolek zawartości z niestandardowymi częściami XML
 Niektóre kontrolki zawartości można powiązać z elementami w niestandardowych częściach XML, które są osadzone w dokumencie. Aby uzyskać więcej informacji na temat niestandardowych części XML, zobacz temat [niestandardowe składniki XML — Omówienie](../vsto/custom-xml-parts-overview.md).

 Aby powiązać formant zawartości z elementem w niestandardowej części XML, użyj właściwości **XMLMapping** formantu. Poniższy przykład kodu demonstruje sposób powiązania <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> `Price` elementu z elementem w `Product` węźle w niestandardowym składniku XML, który został już dodany do dokumentu.

```vb
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")
```

```csharp
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);
```

 Aby zapoznać się z przewodnikiem, który ilustruje sposób powiązania formantów zawartości z niestandardowymi częściami XML, zobacz [Przewodnik: Powiązywanie formantów zawartości z niestandardowymi częściami XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

 Gdy wiążesz formant zawartości z niestandardowym elementem XML, dwukierunkowe powiązanie danych jest automatycznie włączone. Jeśli użytkownik edytuje tekst w kontrolce, odpowiednie elementy XML są automatycznie aktualizowane. Podobnie, jeśli wartości elementów w niestandardowych częściach XML są zmieniane, formanty zawartości powiązane z elementami XML będą wyświetlały nowe dane.

 Można powiązać następujące typy kontrolek zawartości z niestandardowymi składnikami XML:

- <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>

- <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>

- <xref:Microsoft.Office.Tools.Word.PictureContentControl>

- <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>

### <a name="data-bind-events-for-content-controls"></a>Zdarzenia powiązane z danymi dla formantów zawartości
 Wszystkie kontrolki zawartości zapewniają zestaw zdarzeń, które można obsłużyć w celu wykonywania zadań związanych z danymi, takich jak sprawdzenie, czy tekst w kontrolce spełnia określone kryteria przed aktualizacją źródła danych. Poniższa tabela zawiera listę zdarzeń kontroli zawartości związanych z powiązaniem danych.

|Zadanie|Zdarzenie|
|----------|-----------|
|Uruchom kod tuż przed automatycznym zaktualizowaniem tekstu w kontrolce zawartości, która jest powiązana z niestandardowym składnikiem XML.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|
|Uruchamiaj kod tuż przed automatycznym aktualizowaniem danych w niestandardowej części XML, która jest powiązana z kontrolką zawartości (to jest po zmianie tekstu w kontrolce zawartości).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|
|Uruchom własny kod, aby zweryfikować zawartość kontrolki zgodnie z kryteriami niestandardowymi.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|
|Kod uruchomienia po pomyślnym sprawdzeniu poprawności zawartości kontrolki.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|

## <a name="limitations-of-content-controls"></a>Ograniczenia kontrolek zawartości
 Korzystając z formantów zawartości w projektach pakietu Office, należy pamiętać o następujących ograniczeniach.

### <a name="behavior-differences-between-design-time-and-runtime"></a>Różnice w zachowaniu czasu projektowania i środowiska uruchomieniowego
 Wiele ograniczeń, które Microsoft Office wyrazów nakładanych na kontrolki zawartości w czasie wykonywania, nie są wymuszane w czasie projektowania. Podczas projektowania interfejsu użytkownika rozwiązania na poziomie dokumentu w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Pamiętaj o modyfikacji formantów zawartości tylko w sposób, który jest obsługiwany w czasie wykonywania.

 Jeśli zmodyfikujesz kontrolkę zawartości w czasie projektowania w sposób, w jaki formant nie obsługuje w czasie wykonywania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projektant nie będzie powiadamiał o nieobsługiwanych zmianach. Jednak podczas debugowania lub uruchamiania projektu lub w przypadku zapisania i ponownego otwarcia projektu program Word wyświetli komunikat o błędzie i zażądaj uprawnień do naprawy dokumentu. Po naprawieniu dokumentu program Word usuwa całą nieobsługiwaną zawartość i formatowanie z formantu.

 Na przykład program Word nie zapobiega dodawaniu tabeli do i <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> w czasie projektowania. Jednak <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> obiekty nie mogą zawierać tabel w czasie wykonywania, podczas otwierania dokumentu program Word wyświetli komunikat o błędzie.

 Należy również zauważyć, że wiele właściwości definiujących zachowanie formantów zawartości nie ma wpływu w czasie projektowania. Na przykład jeśli ustawisz właściwość **LockContents** kontrolki Content na **true** w czasie projektowania, możesz nadal edytować tekst w kontrolce w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie. Ta właściwość uniemożliwia użytkownikom edytowanie kontrolki w czasie wykonywania.

### <a name="event-limitations"></a>Ograniczenia zdarzeń
 Formanty zawartości nie udostępniają zdarzenia, które jest zgłaszane, gdy użytkownik zmieni tekst lub inne elementy w formancie. Na przykład nie ma zdarzenia, które jest zgłaszane, gdy użytkownik wybierze inny element w <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> lub <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> .

 Aby określić, kiedy użytkownik edytuje zawartość kontrolki zawartości, można powiązać formant z niestandardowym składnikiem XML, a następnie obsłużyć <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> zdarzenie. To zdarzenie jest zgłaszane, gdy użytkownik zmieni zawartość kontrolki, która jest powiązana z niestandardowym elementem XML. Aby zapoznać się z przewodnikiem, który pokazuje, jak powiązać formant zawartości z niestandardowym składnikiem XML, zobacz [Przewodnik: Powiązywanie formantów zawartości z niestandardowymi częściami XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).

### <a name="check-box-content-controls-in-word-projects"></a><a name="checkbox"></a> Formanty zawartości pól wyboru w projektach programu Word
 W programie Word 2010 wprowadzono nowy typ kontrolki zawartości, który reprezentuje pole wyboru. Jednak program [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nie zapewnia odpowiedniego typu CheckBoxContentControl do użycia w projektach pakietu Office. Aby utworzyć kontrolkę zawartości pola wyboru w [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] projekcie programu lub Word 2010, użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> metody do utworzenia <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu i przekaż <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> wartość do metody, aby określić kontrolkę zawartość pola wyboru. Poniższy przykład kodu demonstruje, jak to zrobić.

 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Przewodnik: Tworzenie szablonu za pomocą kontrolek zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Powiązywanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
