---
title: Formanty zawartości
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a837aec3c5f87b51c5874f2fa7bd3f155479b6c2
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54868852"
---
# <a name="content-controls"></a>Formanty zawartości
  Formanty zawartości umożliwiają dla Ciebie dokumentów projektów i szablonów, które mają następujące funkcje:  
  
- Interfejs użytkownika (UI), który jest kontrolowany dane wejściowe, takich jak formularz.  
  
- Ograniczenia, które uniemożliwiają użytkownikom edytowanie chronionych sekcji dokumentu lub szablonu. Aby uzyskać więcej informacji, zobacz [ochrona części dokumentów za pomocą formantów zawartości](#Protection).  
  
- Wiązanie danych do źródła danych. Aby uzyskać więcej informacji, zobacz [wiązanie danych z kontrolkami zawartości](#DataBinding).  
  
  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
  ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [powiązywanie danych do programu Word 2007 zawartości kontrolki przy użyciu programu Visual Studio Tools dla pakietu Office (3.0)](http://go.microsoft.com/fwlink/?LinkId=136785).  
  
## <a name="overview-of-content-controls"></a>Omówienie kontrolek zawartości  
 Formanty zawartości zapewniają interfejs użytkownika, który jest zoptymalizowany dla obu użytkownika, danych wejściowych i drukowania. Po dodaniu kontrolki zawartości do dokumentu, kontrolka jest identyfikowana przez obramowanie, tytuł i tymczasowe tekst, który można dołączyć instrukcje dla użytkownika. Obramowania i tytułu formantu nie są wyświetlane w drukowanej wersji dokumentu.  
  
 Na przykład chcąc użytkownikowi wprowadź datę w sekcji w dokumencie, można dodać kontrolkę zawartości selektora daty do dokumentu. Gdy użytkownik kliknie kontrolkę, zostanie wyświetlony selektor daty standardowego interfejsu użytkownika. Można również ustawić właściwości formantu, aby ustawić regionalnych kalendarza, który jest wyświetlany i określić format daty. Po wybraniu daty interfejsu użytkownika formantu jest ukryta i tylko data jest wyświetlana, jeśli użytkownik drukuje dokument.  
  
 Zawartość pomagają w zapobieganiu naruszeniom również należy wykonać następujące czynności:  
  
- Uniemożliwianie użytkownikom edytowanie lub usuwanie części dokumentu. Jest to przydatne, jeśli informacje w dokumencie lub szablon, który użytkownicy powinni być w stanie odczytane, ale nie edytować, lub jeśli chcesz, aby użytkownicy mogli edytować formanty zawartości, ale nie ich usuwać.  
  
- Powiąż części dokumentu lub szablonu z danymi. Formanty zawartości można powiązać obiekty zarządzane w polach bazy danych [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)], elementy XML, które są przechowywane w dokumencie i innych źródeł danych.  
  
  W projektach na poziomie dokumentu można dodać kontrolek zawartości do dokumentu w czasie projektowania lub w czasie wykonywania. W projektach dodatku narzędzi VSTO formanty zawartości można dodać do dowolnego otwartego dokumentu w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
> [!NOTE]  
>  Formanty zawartości można użyć tylko w dokumentach, które są zapisane w formacie Open XML. Formanty zawartości nie można używać w dokumentach, które są zapisane w dokumencie programu Word 97 – 2003 (*doc*) format.  
  
## <a name="types-of-content-controls"></a>Typy kontrolek zawartości  
 Istnieje dziewięciu różne rodzaje formantów zawartości, które można dodać do dokumentów. Większość formanty zawartości mają odpowiedni typ w <xref:Microsoft.Office.Tools.Word> przestrzeni nazw. Możesz również użyć ogólnego <xref:Microsoft.Office.Tools.Word.ContentControl>, który może reprezentować jedną z dostępnych kontrolek zawartości. Aby uzyskać wskazówki, który demonstruje sposób używania każdego z dostępnych kontrolek zawartości, zobacz [instruktażu: Tworzenie szablonu za pomocą formantów zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).  
  
### <a name="build-block-gallery"></a>Tworzenie galerii bloku  
 Galeria modułów konstrukcyjnych umożliwia użytkownikom wybranie z listy *bloki konstrukcyjne dokumentu* do wstawienia do dokumentu. Blok konstrukcyjny dokumentu jest zawartość, która została utworzona w celu można użyć wiele razy, takie jak wspólne stronę tytułową, sformatowania tabeli lub nagłówkiem. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> typu. Aby uzyskać więcej informacji na temat bloków konstrukcyjnych, zobacz [Nowości dla deweloperów w programie Word 2007](/previous-versions/office/developer/office-2007/bb266218(v=office.12)).  
  
### <a name="check-box"></a>Pole wyboru  
 Pole wyboru udostępnia interfejs użytkownika, który reprezentuje stan binarny: lub odznaczane.  
  
 W odróżnieniu od innych rodzajów formantów zawartości [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nie zawiera określonego typu, który reprezentuje kontrolkę zawartości pola wyboru. Innymi słowy, ma nie `CheckBoxContentControl` typu. Jednak nadal można utworzyć kontrolkę zawartości pola wyboru przez dodanie ogólnego elementu <xref:Microsoft.Office.Tools.Word.ContentControl> do dokumentu programowo. Aby uzyskać więcej informacji, zobacz [zawartości formanty pól wyboru w projektach programu Word](#checkbox).  
  
### <a name="combo-box"></a>Pole kombi  
 Pole kombi Wyświetla listę elementów, które użytkownicy mogą wybrać. W przeciwieństwie do menu rozwijanego pola kombi umożliwia użytkownikom dodawanie własnych elementów. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> typu.  
  
### <a name="date-picker"></a>Wybór daty  
 Wybór daty zawiera kalendarz interfejsu użytkownika do wybierania daty. Kalendarz jest wyświetlany, gdy użytkownik końcowy kliknie strzałkę listy rozwijanej w formancie. Można użyć regionalnych kalendarze i formaty daty innej. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> typu.  
  
### <a name="drop-down-list"></a>Listy rozwijanej  
 Listy rozwijanej Wyświetla listę elementów, które użytkownicy mogą wybrać. W przeciwieństwie do pola kombi listy rozwijanej nie zezwala użytkownikom na dodawanie lub edytowanie elementów. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> typu.  
  
### <a name="group"></a>Grupa  
 Formant grupy definiuje region chroniony dokument, który użytkownicy nie można edytować ani usunąć. Formant grupa może zawierać żadnych elementów dokumentu, takich jak tekst, tabel, graficznych i inne formanty zawartości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.GroupContentControl> typu.  
  
### <a name="picture"></a>Obraz  
 Formant obrazu wyświetla obraz. Można określić obrazu w czasie projektowania lub czas wykonywania lub użytkownicy będą mogli kliknąć ten formant, aby wybrać obraz do wstawienia w dokumencie. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.PictureContentControl> typu.  
  
### <a name="rich-text"></a>Tekst sformatowany  
 Kontrolki tekstu sformatowanego zawiera tekst lub inne elementy, takie jak tabele, obrazów i inne formanty zawartości. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.RichTextContentControl> typu.  
  
### <a name="plain-text"></a>Zwykły tekst  
 Kontrolka zwykłego tekstu zawiera tekst. Kontrolka zwykłego tekstu nie może zawierać innych elementów, takich jak tabele, obrazów i inne formanty zawartości. Ponadto zawiera cały tekst w kontrolce zwykłego tekstu, to samo formatowanie. Na przykład jeśli powoduje zastosowanie kursywy zdania w kontrolce zwykły tekst o jeden wyraz, cały tekst wewnątrz formantu jest pisany kursywą. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> typu.  
  
### <a name="generic-content-control"></a>Ogólny formantu zawartości  
 Jest ogólny formantu zawartości <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu, który może reprezentować dowolny z dostępnych typów formantów zawartości. Możesz zmienić <xref:Microsoft.Office.Tools.Word.ContentControl> obiekt, aby zachowywać się jak innego typu formantu zawartości przy użyciu <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> właściwości. Na przykład, jeśli tworzysz <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu, że reprezentuje zwykłego tekstu kontrolować, można zmienić jej w czasie wykonywania, aby zachowuje się jak pole kombi.  
  
 Możesz utworzyć <xref:Microsoft.Office.Tools.Word.ContentControl> obiektów tylko w czasie wykonywania, nie w czasie projektowania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
## <a name="common-features-of-content-controls"></a>Często używane funkcje kontrolek zawartości  
 Formanty najbardziej zawartości mają zestaw elementów członkowskich, które służą do wykonywania typowych zadań. W poniższej tabeli opisano niektóre zadania, które można wykonać przy użyciu tych elementów członkowskich.  
  
|Dla tego zadania:|wykonaj następujące czynności:|  
|--------------------|--------------|  
|Pobieranie lub ustawianie tekstu wyświetlanego w kontrolce.|Użyj **tekstu** właściwości. **Uwaga:**  <xref:Microsoft.Office.Tools.Word.PictureContentControl> i <xref:Microsoft.Office.Tools.Word.ContentControl> typów nie ma tej właściwości.|  
|Pobierz lub ustaw tymczasowe tekst, który jest wyświetlany w formancie, dopóki użytkownik nie dokona edycji formantu, formant jest wypełniony danymi ze źródła danych lub zawartość formantu są usuwane.|Użyj **PlaceholderText** właściwości. **Uwaga:**  <xref:Microsoft.Office.Tools.Word.PictureContentControl> Typ nie ma tej właściwości.|  
|Pobieranie lub Ustawianie tytułu, który jest wyświetlany w obramowania formantu zawartości, gdy użytkownik kliknie przycisk.|Użyj **tytuł** właściwości.|  
|Usuń kontrolki z dokumentu automatycznie po użytkownik dokona edycji formantu. (Tekst w kontrolce pozostaje w dokumencie).|Użyj **tymczasowe** właściwości.|  
|Uruchom kod, gdy użytkownik kliknie w formancie zawartości lub gdy kursor jest przenoszony do formantu zawartości programowo.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> zdarzeń formantu.|  
|Uruchom kod, gdy użytkownik kliknie poza kontrolą zawartości lub gdy kursor zostanie przeniesiony poza kontrolą zawartości programowo.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> zdarzeń formantu.|  
|Uruchomienia kodu po wykonaniu zawartości formant jest dodawany do dokumentu w wyniku ponawiania lub cofnąć operację.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> zdarzeń formantu.|  
|Uruchom kod tuż przed formantu zawartości zostanie usunięty z dokumentu.|Obsługa <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> zdarzeń formantu.|  
  
##  <a name="Protection"></a> Ochrona części dokumentów za pomocą formantów zawartości  
 W przypadku ochrony części dokumentu, można uniemożliwić użytkownikom zmienianie lub usuwanie zawartości w tej części dokumentu. Istnieje kilka sposobów, w części dokumentu można chronić za pomocą formantów zawartości.  
  
 Jeśli obszar, który ma być chroniony, znajduje się wewnątrz formantu zawartości, można użyć właściwości formantu zawartości, aby uniemożliwić użytkownikom edytowanie lub usuwanie kontrolki:  
  
- **LockContents** właściwość uniemożliwia użytkownikom edytowania zawartości.  
  
- **LockContentControl** właściwość uniemożliwia użytkownikom usunięcie formantu.  
  
  Jeśli obszar, który chcesz chronić nie znajduje się wewnątrz formantu zawartości lub jeśli chcesz chronić obszar, który zawiera formanty zawartości i inne typy zawartości, możesz umieścić cały obszar w <xref:Microsoft.Office.Tools.Word.GroupContentControl>. W przeciwieństwie do innych kontrolek zawartości <xref:Microsoft.Office.Tools.Word.GroupContentControl> zapewnia nie interfejsu użytkownika, który jest widoczny dla użytkownika. Jego służy wyłącznie do definiowania region, który użytkownicy nie mogą edytować.  
  
> [!NOTE]  
>  Jeśli tworzysz <xref:Microsoft.Office.Tools.Word.GroupContentControl> zawierającą osadzone formanty zawartości, embedded formanty zawartości nie są automatycznie chronione. Należy użyć **LockContents** właściwości każdego z osadzonych formantu, aby uniemożliwić użytkownikom edytowanie ich zawartości.  
  
 Aby uzyskać więcej informacji o jak ochrona części dokumentów za pomocą formantów zawartości, zobacz [jak: Ochrona części dokumentów za pomocą formantów zawartości](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).  
  
##  <a name="DataBinding"></a> Wiązanie danych z kontrolkami zawartości  
 Aby wyświetlić dane w dokumentach, powiązania kontrolki zawartości ze źródłem danych. Po zaktualizowaniu źródło danych zmiany zostały uwzględnione formantu zawartości. Można także zapisać zmiany do źródła danych.  
  
 Formanty zawartości zapewniają następujące opcje powiązania danych:  
  
- Możesz powiązać formanty zawartości pól bazy danych lub obiekty zarządzane przy użyciu tego samego modelu powiązania danych jako Windows Forms.  
  
- Formanty zawartości można powiązać elementy w częściach XML (o nazwie *niestandardowe elementy XML*), są osadzone w dokumencie.  
  
  Omówienie powiązanie kontrolki hosta w rozwiązaniach pakietu Office z danymi, zobacz [wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
### <a name="use-the-windows-forms-data-binding-model"></a>Przy użyciu modelu Windows Forms powiązania danych  
 Większość zawartości kontrolki obsługuje model powiązania proste dane, który korzysta z Windows Forms. Proste powiązanie danych oznacza, że kontrolka jest powiązana z elementu danych jednego, takiego jak wartość w kolumnie tabeli danych. Aby uzyskać więcej informacji, zobacz [powiązanie danych oraz Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).  
  
 W projektach na poziomie dokumentu, można powiązać danych z kontrolkami zawartości przy użyciu **źródeł danych** okna [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji na temat dodawania powiązanych z danymi kontrolek zawartości do dokumentów, zobacz [jak: Zapełnianie dokumentów danymi z bazy danych](../vsto/how-to-populate-documents-with-data-from-a-database.md) i [jak: Zapełnianie dokumentów danymi z obiektów](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
 W poniższej tabeli wymieniono formantami zawartości, które można powiązać danego typu danych w **źródeł danych** okna.  
  
|Typ danych|Domyślny formant zawartości|Inne formanty zawartości, które mogą być powiązane z tego typu danych|  
|---------------|-----------------------------|----------------------------------------------------------------|  
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|  
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> Tablica|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|Brak|  
  
 W poziomie dokumentu i projektów dodatku VSTO można powiązać kontrolki zawartości ze źródłem danych programowo przy użyciu <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> właściwości formantu. Jeśli to zrobisz, Przekaż w ciągu **tekstu** do *propertyName* parametru <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> metody. **Tekstu** właściwość jest domyślna właściwość wiązanie danych kontrolek zawartości.  
  
 Formanty zawartości obsługują także powiązanie dwukierunkowe danych, w którym zmiany w formancie są aktualizowane w źródle danych. Aby uzyskać więcej informacji, zobacz [jak: Aktualizowanie źródła danych danymi z kontrolki hosta](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
> [!NOTE]  
>  Formanty zawartości nie obsługują złożone powiązanie danych. Jeżeli powiążesz <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> lub <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> ze źródłem danych przy użyciu modelu danych programu Windows Forms, użytkownicy będą widzieć tylko jedną wartość, po kliknięciu formantu. Jeśli chcesz powiązać te kontrolki do zestawu wartości danych, które użytkownicy mogą wybierać spośród tych kontrolek można powiązać elementy w niestandardowym elementem XML.  
  
### <a name="bind-content-controls-to-custom-xml-parts"></a>Powiązywanie kontrolek zawartości do niestandardowych części XML  
 Niektóre formanty zawartości można powiązać elementy niestandardowe elementy XML, które są osadzone w dokumencie. Aby uzyskać więcej informacji na temat niestandardowych części XML, zobacz [przegląd części niestandardowy kod XML](../vsto/custom-xml-parts-overview.md).  
  
 Aby powiązać formant zawartości elementu w niestandardowym elementem XML, należy użyć **XMLMapping** właściwości formantu. Poniższy przykład kodu pokazuje, jak powiązać <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> do `Price` pod `Product` węzła w niestandardowym elementem XML, który został już dodany do dokumentu.  
  
```vb  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")  
```  
  
```csharp  
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);  
```  
  
 Aby uzyskać wskazówki, który demonstruje, jak powiązać formanty zawartości do niestandardowych części XML bardziej szczegółowo, zobacz [instruktażu: Powiązywanie kontrolek zawartości do niestandardowych części XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
 Gdy powiąże formant zawartości z niestandardowym elementem XML powiązanie dwukierunkowe danych jest automatycznie włączone. Jeśli użytkownik dokona edycji tekstu w kontrolce, odpowiednie elementy XML są automatycznie aktualizowane. Podobnie jeśli wartości elementów w niestandardowych części XML zostanie zmieniony, formanty zawartości, które są powiązane elementy XML wyświetli nowe dane.  
  
 Można powiązać następujące typy kontrolek zawartości do niestandardowych części XML:  
  
-   <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PictureContentControl>  
  
-   <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>  
  
### <a name="data-bind-events-for-content-controls"></a>Powiązanie danych zdarzeń dla formantów zawartości  
 Wszystkie formanty zawartości zapewniają zestaw zdarzeń, które może obsłużyć do wykonywania zadań związanych z danymi, takich jak sprawdzanie poprawności tekstu w kontrolce spełnia określone kryteria, zanim źródło danych zostanie zaktualizowane. W poniższej tabeli wymieniono zdarzenia kontroli zawartości, that are related to powiązanie danych.  
  
|Zadanie|Zdarzenie|  
|----------|-----------|  
|Uruchom kod, po prostu, zanim program Word automatycznie aktualizuje tekstu w formancie zawartości, który jest powiązany z niestandardowym elementem XML.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|  
|Uruchomienia kodu przed Word automatycznie aktualizuje dane w niestandardowym elementem XML, który jest powiązany z kontrolować zawartość (po zmiany tekstu w formancie zawartości).|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|  
|Uruchomić kod do sprawdzania poprawności zawartości formantu zgodnie z kryteriami niestandardowych.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|  
|Uruchom kod po zawartości formantu został pomyślnie zweryfikowany.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|  
  
## <a name="limitations-of-content-controls"></a>Ograniczenia formantów zawartości  
 Gdy używasz kontrolek zawartości w projektach pakietu Office, należy pamiętać o następujących ograniczeniach.  
  
### <a name="behavior-differences-between-design-time-and-runtime"></a>Zachowanie różnice w czasie projektowania i środowiska uruchomieniowego  
 Wiele ograniczeń, które program Microsoft Office Word nakłada się na formanty zawartości w czasie wykonywania nie są wymuszane w czasie projektowania. Podczas projektowania interfejsu użytkownika rozwiązania poziomu dokumentu w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], pamiętaj zmodyfikować formanty zawartości tylko w sposób, które są obsługiwane w czasie wykonywania.  
  
 W przypadku zmodyfikowania zawartości formantu w czasie projektowania w sposób, który nie obsługuje formantu w czasie wykonywania, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Projektant nie wyśle alertu o nieobsługiwane zmiany. Jednak podczas debugowania i uruchomić projekt, czy zapisać, a następnie ponownie otwórz projekt, programu Word spowoduje wyświetlenie błędu wiadomości i zawnioskuj o uprawnienie do naprawy dokumentu. Podczas naprawiania dokumentu programu Word usuwa wszystkie nieobsługiwane zawartość i formatowanie w formancie.  
  
 Na przykład Word uniemożliwia Dodawanie tabeli do <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> w czasie projektowania. Jednak ponieważ <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> obiektów nie może zawierać tabele w czasie wykonywania, Word spowoduje wyświetlenie komunikatu o błędzie, po otwarciu dokumentu.  
  
 Należy również zauważyć, że wiele właściwości, które definiują zachowanie formanty zawartości nie mają wpływu w czasie projektowania. Na przykład jeśli ustawisz **LockContents** właściwości zawartości kontrolki **True** w czasie projektowania, nadal możesz edytować tekst w kontrolce [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektanta. Tej właściwości zapobiega tylko użytkownicy edycji formantu w czasie wykonywania.  
  
### <a name="event-limitations"></a>Zdarzenia ograniczenia  
 Formanty zawartości nie są oferowane zdarzenie, które jest wywoływane, gdy użytkownik zmieni tekst lub innych elementów w formancie. Na przykład, nie ma żadnego zdarzenia, które jest wywoływane, gdy użytkownik wybierze inny element w <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> lub <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>.  
  
 Aby określić, gdy użytkownik edytuje zawartość formantu zawartości, można powiązać kontrolkę z niestandardowym elementem XML i następnie obsłużyć <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> zdarzeń. To zdarzenie jest wywoływane, gdy użytkownik zmieni zawartości formantu, który jest powiązany z niestandardowym elementem XML. Aby uzyskać przewodnik pokazuje, jak powiązać kontrolkę zawartości do niestandardowych części XML, zobacz [instruktażu: Powiązywanie kontrolek zawartości do niestandardowych części XML](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
###  <a name="checkbox"></a> Formanty zawartości pól wyboru w projektach programu Word  
 Word 2010 wprowadzono nowy typ formantu zawartości, który reprezentuje pole wyboru. Jednak [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] nie zapewnia odpowiedni typ CheckBoxContentControl można ich używać w projektach pakietu Office. Aby utworzyć kontrolkę zawartości pola wyboru w [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] lub w projekcie programu Word 2010, użyj <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> metodę w celu utworzenia <xref:Microsoft.Office.Tools.Word.ContentControl> obiektu i przekaż <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> wartości do metody, aby określić kontrolkę zawartości pola wyboru. Poniższy przykład kodu pokazuje, jak to zrobić.  
  
 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]  
  
## <a name="see-also"></a>Zobacz także  
 [Automatyzowanie programu Word za pomocą obiektów rozszerzonych](../vsto/automating-word-by-using-extended-objects.md)   
 [Instrukcje: Dodawanie kontrolek zawartości do dokumentów programu Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Przewodnik: Tworzenie szablonu za pomocą formantów zawartości](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)   
 [Wiązanie danych do kontrolek w rozwiązaniach pakietu Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
