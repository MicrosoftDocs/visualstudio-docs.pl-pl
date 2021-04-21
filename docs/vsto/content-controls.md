---
title: Kontrolki zawartości
description: Poznaj kontrolki zawartości i dowiedz się, jak kontrolki zawartości zapewniają sposób projektowania dokumentów i szablonów.
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
ms.openlocfilehash: b0d55daba4dee07454a31fcb6fc5fa210e8bcc34
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825059"
---
# <a name="content-controls"></a>Kontrolki zawartości
  Kontrolki zawartości zapewniają sposób projektowania dokumentów i szablonów, które mają następujące funkcje:

- Interfejs użytkownika,który ma kontrolowane dane wejściowe, takie jak formularz.

- Ograniczenia, które uniemożliwiają użytkownikom edytowanie chronionych sekcji dokumentu lub szablonu. Aby uzyskać więcej informacji, zobacz [Protect parts of documents by using content controls (Ochrona części dokumentów za pomocą kontrolek zawartości).](#Protection)

- Powiązanie danych ze źródłem danych. Aby uzyskać więcej informacji, zobacz [Wiązanie danych z kontrolkami zawartości.](#DataBinding)

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  ![link do wideo](../vsto/media/playvideo.gif "link do wideo") Aby uzyskać powiązany pokaz wideo, zobacz Wiązanie danych z kontrolkami zawartości programu [Word 2007 przy użyciu Visual Studio Tools dla systemu office (3.0).](/previous-versions/office/developer/office-2007/bb967663(v=office.12))

## <a name="overview-of-content-controls"></a>Omówienie kontrolek zawartości
 Kontrolki zawartości zapewniają interfejs użytkownika zoptymalizowany pod kątem danych wejściowych użytkownika i drukowania. Po dodaniu kontrolki zawartości do dokumentu kontrolka jest identyfikowana za pomocą obramowania, tytułu i tekstu tymczasowego, który może dostarczyć użytkownikowi instrukcje. Obramowanie i tytuł kontrolki nie są wyświetlane w wydrukowanych wersjach dokumentu.

 Jeśli na przykład chcesz, aby użytkownik wprowadzał datę w sekcji dokumentu, możesz dodać do dokumentu kontrolkę zawartości s wyboru daty. Gdy użytkownicy klikną kontrolkę, zostanie wyświetlony standardowy interfejs użytkownika s wyboru daty. Można również ustawić właściwości kontrolki, aby ustawić wyświetlany kalendarz regionalny i określić format daty. Gdy użytkownik wybierze datę, interfejs użytkownika kontrolki zostanie ukryty i tylko data zostanie wyświetlona, jeśli użytkownik drukuje dokument.

 Kontrolki zawartości ułatwiają również:

- Uniemożliwiaj użytkownikom edytowanie lub usuwanie części dokumentu. Jest to przydatne, jeśli w dokumencie lub szablonie masz informacje, które użytkownicy powinni mieć możliwość odczytu, ale nie edytowania, lub jeśli chcesz, aby użytkownicy mogli edytować kontrolki zawartości, ale nie usuwać ich.

- Wiązanie części dokumentu lub szablonu z danymi. Kontrolki zawartości można powiązać z polami bazy danych, zarządzanymi obiektami w elementach , elementami XML przechowywanymi w dokumencie [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] i innymi źródłami danych.

  W projektach na poziomie dokumentu można dodawać kontrolki zawartości do dokumentu w czasie projektowania lub w czasie uruchamiania. W projektach dodatków VSTO można dodawać kontrolki zawartości do dowolnego otwartego dokumentu w czasie uruchamiania. Aby uzyskać więcej informacji, [zobacz Jak dodawać kontrolki zawartości do dokumentów programu Word.](../vsto/how-to-add-content-controls-to-word-documents.md)

> [!NOTE]
> Kontrolek zawartości można używać tylko w dokumentach zapisanych w formacie Open XML. Kontrolek zawartości nie można używać w dokumentach zapisywanych w formacie dokumentu programu Word 97-2003 *(doc).*

## <a name="types-of-content-controls"></a>Typy kontrolek zawartości
 Istnieje dziewięć różnych typów kontrolek zawartości, które można dodać do dokumentów. Większość kontrolek zawartości ma odpowiedni typ w przestrzeni <xref:Microsoft.Office.Tools.Word> nazw . Można również użyć ogólnego typu <xref:Microsoft.Office.Tools.Word.ContentControl> , który może reprezentować dowolną z dostępnych kontrolek zawartości. Aby uzyskać przewodnik, który pokazuje, jak używać każdej z dostępnych kontrolek zawartości, zobacz Przewodnik: tworzenie szablonu [przy użyciu kontrolek zawartości.](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)

### <a name="build-block-gallery"></a>Galeria bloków kompilacji
 Galeria bloków konstrukcyjnych umożliwia użytkownikom wybieranie z listy *bloków* konstrukcyjnych dokumentów w celu wstawiania ich do dokumentu. Blok blokowy tworzenia dokumentu to fragment zawartości, który został utworzony do wielokrotnego przetwarzania, na przykład wspólna strona okładki, sformatowana tabela lub nagłówek. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> typ . Aby uzyskać więcej informacji na temat bloków konstrukcyjnych, zobacz [Co nowego dla deweloperów w programie Word 2007.](/previous-versions/office/developer/office-2007/bb266218(v=office.12))

### <a name="check-box"></a>Pole wyboru
 Pole wyboru zawiera interfejs użytkownika, który reprezentuje stan binarny: zaznaczony lub wyczyszowany.

 W przeciwieństwie do innych typów kontrolek zawartości, typ nie zapewnia określonego typu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] reprezentującego kontrolkę zawartości pola wyboru. Innymi słowy, nie ma `CheckBoxContentControl` typu. Nadal można jednak utworzyć kontrolkę zawartości pola wyboru, dodając typ ogólny do <xref:Microsoft.Office.Tools.Word.ContentControl> dokumentu programowo. Aby uzyskać więcej informacji, zobacz [Kontrolki zawartości pola wyboru w projektach programu Word](#checkbox).

### <a name="combo-box"></a>Pole kombi
 Pole kombi wyświetla listę elementów, które użytkownicy mogą wybrać. W przeciwieństwie do listy rozwijanej pole kombi umożliwia użytkownikom dodawanie własnych elementów. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> typ .

### <a name="date-picker"></a>Wybór daty
 S wyboru daty udostępnia interfejs użytkownika kalendarza do wybierania daty. Kalendarz jest wyświetlany, gdy użytkownik końcowy kliknie strzałkę listy rozwijanej w kontrolce. Można używać kalendarzy regionalnych i różnych formatów dat. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> typ .

### <a name="drop-down-list"></a>Lista rozwijana
 Lista rozwijana zawiera listę elementów, które użytkownicy mogą wybrać. W przeciwieństwie do pola kombi lista rozwijana nie umożliwia użytkownikom dodawania ani edytowania elementów. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> typ .

### <a name="group"></a>Group (Grupa)
 Kontrolka grupy definiuje chroniony region dokumentu, który użytkownicy nie mogą edytować ani usuwać. Kontrolka grupy może zawierać dowolne elementy dokumentu, takie jak tekst, tabele, grafiki i inne kontrolki zawartości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.GroupContentControl> typ .

### <a name="picture"></a>Obraz
 Kontrolka obrazu wyświetla obraz. Obraz można określić w czasie projektowania lub w czasie uruchamiania albo użytkownicy mogą kliknąć tę kontrolkę, aby wybrać obraz do wstawienia do dokumentu. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.PictureContentControl> typ .

### <a name="rich-text"></a>Tekst sformatowany
 Kontrolka tekstu sformatowanego zawiera tekst lub inne elementy, takie jak tabele, obrazy lub inne kontrolki zawartości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.RichTextContentControl> typ .

### <a name="plain-text"></a>Zwykły tekst
 Kontrolka zwykłego tekstu zawiera tekst. Kontrolka zwykłego tekstu nie może zawierać innych elementów, takich jak tabele, obrazy ani inne kontrolki zawartości. Ponadto cały tekst w kontrolce zwykłego tekstu ma takie samo formatowanie. Jeśli na przykład italizujesz jeden wyraz zdania w kontrolce zwykłego tekstu, cały tekst wewnątrz kontrolki jest kursywą. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> typ .

### <a name="generic-content-control"></a>Ogólna kontrola zawartości
 Ogólna kontrolka zawartości to <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt, który może reprezentować dowolny z dostępnych typów kontrolek zawartości. Za pomocą właściwości można zmienić obiekt tak, aby zachowywał się jak inny typ kontroli <xref:Microsoft.Office.Tools.Word.ContentControl> <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> zawartości. Jeśli na przykład utworzysz obiekt reprezentujący kontrolkę w postaci zwykłego tekstu, możesz ją zmienić w czasie uruchamiania, aby zachowywał się jak <xref:Microsoft.Office.Tools.Word.ContentControl> pole kombi.

 Obiekty można <xref:Microsoft.Office.Tools.Word.ContentControl> tworzyć tylko w czasie uruchamiania, a nie w czasie projektowania. Aby uzyskać więcej informacji, [zobacz Jak dodawać kontrolki zawartości do dokumentów programu Word.](../vsto/how-to-add-content-controls-to-word-documents.md)

## <a name="common-features-of-content-controls"></a>Typowe funkcje kontrolek zawartości
 Większość kontrolek zawartości współużytkuje zestaw elementów członkowskich, których można użyć do wykonywania typowych zadań. W poniższej tabeli opisano niektóre zadania, które można wykonać przy użyciu tych elementów członkowskich.

|Dla tego zadania:|W tym celu:|
|--------------------|--------------|
|Pobierz lub ustaw tekst wyświetlany w kontrolce.|Użyj **właściwości** Text. **Uwaga:**  Typy <xref:Microsoft.Office.Tools.Word.PictureContentControl> i nie mają tej <xref:Microsoft.Office.Tools.Word.ContentControl> właściwości.|
|Pobierz lub ustaw tekst tymczasowy, który jest wyświetlany w kontrolce, dopóki użytkownik nie zedytuje kontrolki, kontrolka nie zostanie wypełniona danymi ze źródła danych lub zawartość kontrolki zostanie usunięta.|Użyj właściwości **PlaceholderText.** **Uwaga:**  Typ <xref:Microsoft.Office.Tools.Word.PictureContentControl> nie ma tej właściwości.|
|Pobierz lub ustaw tytuł wyświetlany na obramowanie kontrolki zawartości, gdy użytkownik kliknie ją.|Użyj **właściwości** Title.|
|Usuń kontrolkę z dokumentu automatycznie, gdy użytkownik zedytuje kontrolkę. (Tekst w kontrolce pozostaje w dokumencie).|Użyj właściwości **Temporary.**|
|Uruchom kod, gdy użytkownik kliknie kontrolkę zawartości lub gdy kursor zostanie przeniesiony programowo do kontrolki zawartości.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> zdarzenia kontrolki.|
|Uruchamiaj kod, gdy użytkownik kliknie poza kontrolkę zawartości lub gdy kursor zostanie przeniesiony programowo poza kontrolkę zawartości.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> zdarzenia kontrolki.|
|Uruchom kod po dodaniu kontrolki zawartości do dokumentu w wyniku operacji ponownego uruchomienia lub cofnięcia.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> zdarzenia kontrolki.|
|Uruchom kod tuż przed usunięciem kontrolki zawartości z dokumentu.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> zdarzenia kontrolki.|

## <a name="protect-parts-of-documents-by-using-content-controls"></a><a name="Protection"></a> Ochrona części dokumentów za pomocą kontrolek zawartości
 Ochrona części dokumentu uniemożliwia użytkownikom zmienianie lub usuwanie zawartości w tej części dokumentu. Istnieje kilka sposobów ochrony części dokumentu za pomocą kontrolek zawartości.

 Jeśli obszar, który chcesz chronić, znajduje się wewnątrz kontrolki zawartości, możesz użyć właściwości kontrolki zawartości, aby uniemożliwić użytkownikom edytowanie lub usuwanie kontrolki:

- Właściwość **LockContents** uniemożliwia użytkownikom edytowanie zawartości.

- Właściwość **LockContentControl** uniemożliwia użytkownikom usunięcie kontrolki.

  Jeśli obszar, który chcesz chronić, nie znajduje się w kontrolce zawartości lub jeśli chcesz chronić obszar zawierający kontrolki zawartości i inne typy zawartości, możesz umieścić cały obszar w obszarze <xref:Microsoft.Office.Tools.Word.GroupContentControl> . W przeciwieństwie do innych kontrolek zawartości, interfejs <xref:Microsoft.Office.Tools.Word.GroupContentControl> użytkownika nie jest widoczny dla użytkownika. Jej jedynym celem jest zdefiniowanie regionu, który użytkownicy nie mogą edytować.

> [!NOTE]
> W przypadku utworzenia <xref:Microsoft.Office.Tools.Word.GroupContentControl> kontrolki zawierającej osadzone kontrolki zawartości osadzone kontrolki zawartości nie są automatycznie chronione. Należy użyć właściwości **LockContents** każdej osadzonej kontrolki, aby uniemożliwić użytkownikom edytowanie ich zawartości.

 Aby uzyskać więcej informacji na temat używania kontrolek zawartości do ochrony części dokumentów, zobacz Jak chronić części dokumentów [przy użyciu kontrolek zawartości.](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)

## <a name="bind-data-to-content-controls"></a><a name="DataBinding"></a> Wiązanie danych z kontrolkami zawartości
 Dane można wyświetlać w dokumentach, wiążąc kontrolkę zawartości ze źródłem danych. Gdy źródło danych jest aktualizowane, kontrolka zawartości odzwierciedla zmiany. Możesz również zapisać zmiany z powrotem w źródle danych.

 Kontrolki zawartości oferują następujące opcje powiązania danych:

- Kontrolki zawartości można powiązać z polami bazy danych lub obiektami zarządzanymi przy użyciu tego samego modelu powiązania danych co Windows Forms.

- Kontrolki zawartości można powiązać z elementami w elementach XML (nazwanych również niestandardowymi częściami *XML),* które są osadzone w dokumencie.

  Omówienie powiązań kontrolek hosta w rozwiązaniach pakietu Office z danymi zawiera temat Wiązanie danych [z kontrolkami w rozwiązaniach pakietu Office.](../vsto/binding-data-to-controls-in-office-solutions.md)

### <a name="use-the-windows-forms-data-binding-model"></a>Korzystanie z Windows Forms powiązania danych
 Większość kontrolek zawartości obsługuje prosty model powiązania danych, który Windows Forms danych. Proste powiązanie danych oznacza, że kontrolka jest powiązana z pojedynczym elementem danych, takim jak wartość w kolumnie tabeli danych. Aby uzyskać więcej informacji, zobacz [Powiązanie danych i Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

 W projektach na poziomie dokumentu można powiązać dane z kontrolkami zawartości przy użyciu okna **Źródła** danych w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Aby uzyskać więcej informacji na temat dodawania kontrolek zawartości powiązanych z danymi do dokumentów, zobacz [Jak:](../vsto/how-to-populate-documents-with-data-from-a-database.md) wypełnianie dokumentów danymi z bazy danych i Jak wypełnić dokumenty danymi z [obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md).

 W poniższej tabeli wymieniono kontrolki zawartości, które można powiązać z każdym typem danych w **oknie Źródła** danych.

|Typ danych|Domyślna kontrolka zawartości|Inne kontrolki zawartości, które mogą być powiązane z tym typem danych|
|---------------|-----------------------------|----------------------------------------------------------------|
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> Tablicy|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Brak|

 W projektach dodatków na poziomie dokumentu i VSTO kontrolkę zawartości można powiązać programowo ze źródłem danych przy użyciu metody właściwości <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> kontrolki . Jeśli to zrobisz, przekaż ciąg **Text** do parametru *propertyName* <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody . Właściwość **Text** jest domyślną właściwością powiązania danych kontrolek zawartości.

 Kontrolki zawartości obsługują również dwukierunkowe powiązanie danych, w którym zmiany w kontrolce są aktualizowane do źródła danych. Aby uzyskać więcej informacji, zobacz How to: Update a data source with data from a host control (Jak [zaktualizować źródło danych przy użyciu danych z kontrolki hosta).](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)

> [!NOTE]
> Kontrolki zawartości nie obsługują złożonego powiązania danych. W przypadku powiązania typu lub ze źródłem danych przy użyciu modelu danych Windows Forms użytkownicy zobaczą tylko jedną wartość po <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> kliknięciu kontrolki. Jeśli chcesz powiązać te kontrolki z zestawem wartości danych, które użytkownicy mogą wybrać, możesz powiązać te kontrolki z elementami w niestandardowej części XML.

### <a name="bind-content-controls-to-custom-xml-parts"></a>Wiązanie kontrolek zawartości z niestandardowymi częściami XML
 Niektóre kontrolki zawartości można powiązać z elementami w niestandardowych częściach XML osadzonych w dokumencie. Aby uzyskać więcej informacji na temat niestandardowych części XML, zobacz [Niestandardowe części XML — omówienie](../vsto/custom-xml-parts-overview.md).

 Aby powiązać kontrolkę zawartości z elementem w niestandardowej części XML, użyj właściwości **XMLMapping** kontrolki. Poniższy przykład kodu pokazuje, jak powiązać element z elementem w węźle w niestandardowej części XML, która została <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> `Price` już `Product` dodana do dokumentu.

```vb
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")
```

```csharp
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);
```

 Aby uzyskać bardziej szczegółowy przewodnik, który przedstawia sposób powiązania kontrolek zawartości z niestandardowymi częściami XML, zobacz Przewodnik: wiązanie kontrolek zawartości z niestandardowymi [częściami XML.](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)

 W przypadku powiązania kontrolki zawartości z niestandardową częścią XML jest automatycznie włączane dwukierunkowe powiązanie danych. Jeśli użytkownik edytuje tekst w kontrolce, odpowiednie elementy XML są automatycznie aktualizowane. Podobnie jeśli wartości elementów w niestandardowych częściach XML zostaną zmienione, kontrolki zawartości powiązane z elementami XML będą wyświetlać nowe dane.

 Z niestandardowymi częściami XML można powiązać następujące typy kontrolek zawartości:

- <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>

- <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>

- <xref:Microsoft.Office.Tools.Word.PictureContentControl>

- <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>

### <a name="data-bind-events-for-content-controls"></a>Zdarzenia powiązania danych dla kontrolek zawartości
 Wszystkie kontrolki zawartości zapewniają zestaw zdarzeń, które można obsługiwać w celu wykonywania zadań związanych z danymi, takich jak sprawdzania, czy tekst w kontrolce spełnia określone kryteria przed zaktualizowaniem źródła danych. W poniższej tabeli wymieniono zdarzenia kontroli zawartości związane z powiązaniem danych.

|Zadanie|Zdarzenie|
|----------|-----------|
|Uruchom kod tuż przed programem Word, aby automatycznie aktualizuje tekst w kontrolce zawartości powiązanej z niestandardową częścią XML.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|
|Uruchom kod tuż przed programem Word, aby automatycznie aktualizuje dane w niestandardowej części XML powiązanej z kontrolką zawartości (czyli po zmianie tekstu w kontrolce zawartości).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|
|Uruchom własny kod, aby zweryfikować zawartość kontrolki zgodnie z kryteriami niestandardowymi.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|
|Uruchom kod po pomyślnym zweryfikowaniu zawartości kontrolki.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|

## <a name="limitations-of-content-controls"></a>Ograniczenia kontrolek zawartości
 W przypadku używania kontrolek zawartości w projektach pakietu Office należy pamiętać o następujących ograniczeniach.

### <a name="behavior-differences-between-design-time-and-runtime"></a>Różnice w zachowaniu między czasem projektowania a środowiskiem uruchomieniowym
 Wiele ograniczeń, które program Microsoft Office Word nakłada na kontrolki zawartości w czasie uruchamiania, nie jest wymuszanych w czasie projektowania. Podczas projektowania interfejsu użytkownika rozwiązania na poziomie dokumentu w programie należy zmodyfikować kontrolki zawartości tylko w sposób obsługiwany [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] w czasie uruchamiania.

 Jeśli zmodyfikujemy kontrolkę zawartości w czasie projektowania w taki sposób, że kontrolka nie będzie obsługiwana w czasie uruchamiania, projektant nie powiadomi Cię o [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nieobsługiwanych zmianach. Jednak podczas debugowania lub uruchamiania projektu lub w przypadku zapisania, a następnie ponownego otwarcia projektu program Word wyświetli komunikat o błędzie i zażąda uprawnienia do naprawy dokumentu. Podczas naprawy dokumentu program Word usuwa z kontrolki całą nieobsługiwaną zawartość i formatowanie.

 Na przykład program Word nie uniemożliwia dodawania tabeli do tabeli <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> w czasie projektowania. Jednak ponieważ obiekty nie mogą zawierać tabel w czasie uruchamiania, program Word wyświetli komunikat o błędzie <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> po otwarciu dokumentu.

 Należy również zauważyć, że wiele właściwości, które definiują zachowanie kontrolek zawartości, nie ma wpływu w czasie projektowania. Jeśli na przykład ustawisz właściwość **LockContents** kontrolki zawartości na wartość **True** w czasie projektowania, nadal możesz edytować tekst w kontrolce w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektancie. Ta właściwość uniemożliwia użytkownikom edytowanie kontrolki tylko w czasie uruchamiania.

### <a name="event-limitations"></a>Ograniczenia zdarzeń
 Kontrolki zawartości nie zapewniają zdarzenia, które jest wywoływane, gdy użytkownik zmieni tekst lub inne elementy w kontrolce. Na przykład nie ma żadnego zdarzenia, które jest wywoływane, gdy użytkownik wybierze inny element w <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> lub <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> .

 Aby określić, kiedy użytkownik edytuje zawartość kontrolki zawartości, można powiązać kontrolkę z niestandardową częścią XML, a następnie obsłużyć <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> zdarzenie. To zdarzenie jest wywoływane, gdy użytkownik zmienia zawartość kontrolki powiązanej z niestandardową częścią XML. Przewodnik, który pokazuje, jak powiązać kontrolkę zawartości z niestandardową częścią XML, zobacz Przewodnik: wiązanie kontrolek zawartości [z niestandardowymi częściami XML.](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)

### <a name="check-box-content-controls-in-word-projects"></a><a name="checkbox"></a> Kontrolki zawartości pola wyboru w projektach programu Word
 W programie Word 2010 wprowadzono nowy typ kontroli zawartości, który reprezentuje pole wyboru. Jednak nie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] zapewnia odpowiedniego typu CheckBoxContentControl do użycia w projektach pakietu Office. Aby utworzyć kontrolkę zawartości pola wyboru w projekcie programu Word 2010 lub , użyj metody w celu utworzenia obiektu i przekaż wartość do metody w celu określenia kontrolki zawartości [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> pola <xref:Microsoft.Office.Tools.Word.ContentControl> <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> wyboru. Poniższy przykład kodu pokazuje, jak to zrobić.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb" id="Snippet800":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs" id="Snippet800":::

## <a name="see-also"></a>Zobacz też
- [Automatyzowanie programu Word przy użyciu obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)
- [How to: Add content controls to Word documents (Jak dodać kontrolki zawartości do dokumentów programu Word)](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Przewodnik: tworzenie szablonu przy użyciu kontrolek zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)
- [Wiązanie danych z kontrolkami w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
