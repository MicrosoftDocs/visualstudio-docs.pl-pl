---
title: Tworzenie regionów formularzy programu Outlook
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- MICROSOFT.OFFICE.TOOLS.OUTLOOK.FORMREGION
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio]
- form regions [Office development in Visual Studio], creating
- Outlook [Office development in Visual Studio], form regions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8a999ca11427533690628fb92f28e93d22cf0971
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255912"
---
# <a name="create-outlook-form-regions"></a>Tworzenie regionów formularzy programu Outlook
  Za pomocą regionów formularza można dostosowywać Microsoft Office formularzy programu Outlook. Program Visual Studio udostępnia zaawansowane narzędzia, które ułatwiają projektowanie, opracowywanie i debugowanie regionów formularzy.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Ten temat zawiera następujące informacje:

- [Zalety korzystania z regionów formularzy](#Enhance)

- [Dodawanie regionu formularza programu Outlook do projektu](#Adding)

- [Korzystanie z projektanta regionów formularza](#UsingFormRegionDesigner)

- [Używanie regionu formularza zaprojektowanego w programie Outlook](#UsingFormRegionDesignedOutlook)

- [Dodawanie niestandardowego kodu do regionu formularza](#AddingCustomCode)

- [Kompilowanie projektu](#Building)

- [Debugowanie regionu formularza](#Debugging)

- [Wdróż region formularza](#Deploying)

## <a name="advantages-of-using-form-regions"></a><a name="Enhance"></a> Zalety korzystania z regionów formularzy
 Regiony formularzy oferują wiele ulepszeń w porównaniu z tradycyjnym programowaniem formularzy programu Outlook:

- Dostosuj stronę domyślną w dowolnym formularzu standardowym.

- Dodaj do 12 dodatkowych stron do dowolnej standardowej formy.

- Zastąp lub Popraw dowolny formularz standardowy.

- Wyświetlanie niestandardowego interfejsu użytkownika w okienku odczytywanie i inspektorów.

  Aby uzyskać więcej informacji, zobacz [Dostosowywanie stron formularzy i regionów formularzy](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions).

## <a name="add-an-outlook-form-region-to-your-project"></a><a name="Adding"></a> Dodawanie regionu formularza programu Outlook do projektu
 Za pomocą kreatora **nowego regionu formularza programu Outlook** można zaprojektować nowy region formularza lub zaimportować region formularza, który został zaprojektowany w programie Outlook. Ponadto, jeśli masz region formularza, który został użyty w innym projekcie dodatku VSTO programu Outlook, możesz ponownie użyć istniejącego regionu formularza.

### <a name="create-a-new-form-region-by-using-the-wizard"></a><a name="CreatingFormRegion"></a> Tworzenie nowego regionu formularza przy użyciu kreatora
 Aby utworzyć region formularza, Dodaj element **regionu formularza programu Outlook** do projektu dodatku VSTO dla programu Outlook. Spowoduje to uruchomienie kreatora **nowego regionu formularza programu Outlook** .

 Użyj kreatora, aby określić, czy chcesz zaprojektować nowy region formularza, czy zaimportować region formularza, który został zaprojektowany w programie Outlook. Aby uzyskać więcej informacji na temat projektowania nowego regionu formularza, zobacz [Korzystanie z projektanta regionów formularza](#UsingFormRegionDesigner). Aby uzyskać więcej informacji na temat korzystania z regionu formularza zaprojektowanego w programie Outlook, zobacz [Importowanie regionu formularza zaprojektowanego w programie Outlook](#UsingFormRegionDesignedOutlook).

 Użyj kreatora, aby określić typ regionu formularza, który chcesz utworzyć. W poniższej tabeli opisano każdy typ regionu formularza.

|Typ regionu|Opis|
|-----------------|-----------------|
|Poszczególne|Dodaje region formularza jako nową stronę w formularzu programu Outlook.|
|Sąsiadujące|Dołącza region formularza do dolnej części strony domyślnej formularza programu Outlook.|
|Funkcja zastępująca|Dodaje region formularza jako nową stronę zastępującą domyślną stronę formularza programu Outlook.|
|Zamień wszystko|Zamienia cały formularz programu Outlook na region formularza.|

 Można również użyć kreatora, aby określić warunki wyświetlania i wybrać typ formularza do rozszerania. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Wybór dokonany w Kreatorze ma wpływ na opcje dostępne na innych stronach kreatora. Na przykład jeśli wybierzesz **sąsiadujące** lub **oddziel** na stronie **Utwórz nowy region formularza programu Outlook** , pola **tytuł** i **Opis** są niedostępne w **tekście opisowym i wybierz stronę Preferencje wyświetlania** . Jest to spowodowane tym, że program Outlook nie używa tych pól, gdy wyświetla sąsiedni lub oddzielony region formularza.

#### <a name="form-region-files"></a>Pliki regionów formularza
 Po zakończeniu pracy kreatora **nowego regionu formularza programu Outlook** program Visual Studio automatycznie dodaje do projektu następujące pliki:

- Plik kodu regionu formularza. Ten plik ma nazwę określoną dla elementu **region formularza programu Outlook** w oknie dialogowym **Dodaj nowy element** . Dodaj kod obsługujący zdarzenia regionu formularza do tego pliku.

- Plik kodu projektanta regionów formularza. Ten plik zawiera kod wygenerowany przez projektanta regionów formularzy i nie powinien być edytowany bezpośrednio.

- Plik magazynu formularzy programu Outlook (*. ofs*).

    > [!NOTE]
    > Ten plik jest dodawany tylko do projektu, Jeśli zaimportowano region formularza, który został zaprojektowany w programie Outlook.

#### <a name="form-region-factory-class"></a>Klasa fabryki regionów formularza
 Plik kodu regionu formularza zawiera klasę częściową, która implementuje <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> interfejs. Jest to klasa fabryki regionów formularza. Klasa fabryki regionów formularza jest odpowiedzialna za tworzenie nowych wystąpień regionu formularza.

 Tę klasę można znaleźć, rozwijając region **fabryki region formularza** .

 Kreator **nowego regionu formularza programu Outlook** dodaje do tej klasy atrybuty, które określają wewnętrzną nazwę regionu formularza i klasy komunikatów, w których jest wyświetlany region formularza. Te atrybuty można modyfikować ręcznie po dodaniu pliku do projektu.

 Większość klas fabryk regionów formularza jest zaimplementowana w pliku projektanta regionów formularza. Jednak `FormRegionInitializing` program obsługi zdarzeń jest uwidoczniony w pliku kodu regionu formularza. Możesz użyć tego programu obsługi zdarzeń, aby określić, czy program Outlook powinien wyświetlać region formularza. Aby uzyskać więcej informacji, zobacz [Obsługa zdarzeń regionów formularza](#HandlingFormRegionEvents).

### <a name="add-an-existing-form-region-to-your-project"></a><a name="AddingExistingFormRegion"></a> Dodawanie istniejącego regionu formularza do projektu
 Jeśli masz region formularza programu Outlook używany w innym projekcie programu Outlook, możesz użyć go ponownie w bieżącym projekcie dodatku VSTO programu Outlook przy użyciu okna dialogowego **Dodaj istniejący element** .

 Istniejący region formularza musi mieć plik kodu (*. vb* lub *. cs*); nie można dodać plików magazynu formularzy programu Outlook (*OFS*) za pomocą okna dialogowego **Dodaj istniejący element** . Można jednak utworzyć nowy region formularza przez zaimportowanie pliku magazynu formularza programu Outlook. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

## <a name="use-the-form-region-designer"></a><a name="UsingFormRegionDesigner"></a> Korzystanie z projektanta regionów formularza
 Projektant regionów formularza ułatwia projektowanie układu i wyglądu regionu formularza. Formanty zarządzane można przeciągnąć na powierzchnię projektanta, dwukrotnie klikając kontrolki, aby otworzyć programy obsługi zdarzeń, a następnie ustawić właściwości w oknie **Właściwości** .

> [!NOTE]
> Właściwości, które mają wpływ na sposób wyświetlania regionu formularza w programie Outlook, można znaleźć pod węzłem **manifestu** w oknie **Właściwości** .

 Projektant regionów formularza jest dostępny tylko w przypadku wybrania opcji **Projektuj nowy region formularza** na stronie **Wybierz, jak chcesz utworzyć region formularza** w kreatorze **nowego regionu formularza programu Outlook** .

 Istnieją trzy sposoby otwierania projektanta regionów formularza:

- W **Eksplorator rozwiązań**kliknij dwukrotnie plik kodu regionu formularza.

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik kodu regionu formularza, a następnie kliknij pozycję **Projektant widoków**.

- W **Eksplorator rozwiązań**wybierz plik kodu regionu formularza, a następnie w menu **Widok** kliknij polecenie **Projektant**.

  Projektant regionów formularza obsługuje tylko formanty zarządzane. Nie można dodać natywnych kontrolek programu Outlook.

## <a name="import-a-form-region-designed-in-outlook"></a><a name="UsingFormRegionDesignedOutlook"></a> Importowanie regionu formularza zaprojektowanego w programie Outlook
 Podczas projektowania w programie Outlook można dodać natywne kontrolki programu Outlook do regionu formularza. Natywne kontrolki programu Outlook umożliwiają powiązanie z danymi programu Outlook w czasie projektowania. Nie można jednak używać projektanta regionów formularza do dodawania formantów zarządzanych lub zmiany projektu regionu formularza.

 Można zaimportować regiony formularzy do projektu dodatku VSTO programu Outlook przy użyciu **nowego kreatora regionu formularza programu Outlook** . Na stronie **Wybierz, w jaki sposób chcesz utworzyć region formularza** wybierz opcję **Importuj plik magazynu formularzy programu Outlook (ofs)**. Następnie można przejść do lokalizacji pliku magazynu formularza programu Outlook (*OFS*). (Program Outlook zapisuje regiony formularzy jako pliki *. ofs* ).

 Kreator **nowego regionu formularza programu Outlook** kopiuje plik *. ofs* do katalogu projektu i dodaje odwołania kontroli do pliku projektanta regionów formularza. Następnie można obsłużyć zdarzenia kontroli w pliku kodu regionu formularza.

 Aby obsłużyć zdarzenia w projekcie Visual Basic, wybierz zdarzenie z listy Nazwa metody w górnej części edytora kodu.

 Aby obsłużyć zdarzenia w projekcie w języku C#, Subskrybuj zdarzenia w <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> metodzie. Aby uzyskać więcej informacji, zobacz [How to: subskrybowanie i anulowanie subskrypcji zdarzeń &#40;C&#35; Przewodnik programowania&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).

 Właściwości regionu formularza można zmienić w `InitializeManifest` metodzie klasy fabryki regionów formularza.

> [!NOTE]
> Aby zaimportować region formularza, musisz pracować w projekcie, który jest przeznaczony dla tej samej wersji programu Outlook zainstalowanej na komputerze deweloperskim. Na przykład jeśli masz zainstalowany program Outlook 2010, importowanie regionu formularza będzie działało tylko w projekcie, który został utworzony przy użyciu szablonu projektu **dodatku programu Outlook 2010** .

### <a name="update-an-imported-form-regions-design"></a>Aktualizowanie projektu importowanego regionu formularza
 Możesz dodawać, usuwać lub zmieniać kontrolki w regionie formularza. Przed wykonaniem tej czynności należy wykonać kopię zapasową dowolnego kodu, który został dodany do pliku kodu regionu formularza. Następnie otwórz plik *. ofs* w programie Outlook, zmodyfikuj region formularza, a następnie Zapisz zmiany. Zaimportuj zmodyfikowany plik *OFS* za pomocą kreatora **nowego regionu formularza programu Outlook** . Następnie można wkleić kod do nowego pliku kodu regionu formularza.

## <a name="add-custom-code-to-a-form-region"></a><a name="AddingCustomCode"></a> Dodawanie niestandardowego kodu do regionu formularza
 <xref:Microsoft.Office.Tools.Outlook>Przestrzeń nazw zapewnia dostęp do klas, które reprezentują region formularza, element programu Outlook, który wyświetla region formularza, oraz inne przydatne elementy. Element **regionu formularza programu Outlook** automatycznie dodaje odwołanie do tego zestawu w projekcie i wstawia odpowiednią instrukcję **using** lub **Imports** w górnej części pliku kodu regionu formularza.

 Możesz użyć klas, metod i właściwości w `Microsoft.Office.Interop.Outlook` przestrzeni nazw, aby osiągnąć większość zadań programistycznych programu Outlook. Aby uzyskać więcej informacji na temat modelu obiektów programu Outlook, zobacz temat [Omówienie modelu obiektów programu Outlook](../vsto/outlook-object-model-overview.md). Przykłady typowych zadań, które wykorzystują model obiektów programu Outlook, można znaleźć w temacie [rozwiązania programu Outlook](../vsto/outlook-solutions.md).

### <a name="handle-form-region-events"></a><a name="HandlingFormRegionEvents"></a> Obsługa zdarzeń regionów formularza
 Element **regionu formularza programu Outlook** automatycznie dodaje następujące trzy procedury obsługi zdarzeń do pliku kodu regionu formularza.

|Wydarzenie|Opis|
|-----------|-----------------|
|FormRegionInitializing|Występuje przed zainicjowaniem regionu formularza. Możesz sprawdzić warunki w tym programie obsługi zdarzeń, aby określić, czy program Outlook powinien wyświetlać region formularza. Aby uzyskać więcej informacji, zobacz [How to: zapobieganie wyświetlaniu regionu formularza w programie Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|
|FormRegionShowing|Występuje po utworzeniu wystąpienia obszaru formularza, ale przed pojawieniem się obszaru formularza.|
|FormRegionClosed|Występuje przed zamknięciem obszaru formularza.|

## <a name="build-the-project"></a><a name="Building"></a> Kompilowanie projektu
 Podczas tworzenia projektu dodatku programu Outlook VSTO zawierającego region formularza program Visual Studio dodaje do rejestru następujące informacje:

- Klucz dla każdej klasy komunikatów, która jest skojarzona z co najmniej jednym regionem formularza.

- Wpis dla każdego regionu formularza i skojarzona wartość, która reprezentuje nazwę dodatku narzędzi VSTO dla programu Outlook.

  Program Outlook używa tych informacji do załadowania regionów formularza.

## <a name="debug-a-form-region"></a><a name="Debugging"></a> Debugowanie regionu formularza
 Można debugować dodatek VSTO programu Outlook, który zawiera region formularza tak samo jak debugowanie innych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów. Po uruchomieniu debugera program [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Visual Studio automatycznie uruchamia program Outlook.

 Aby wyświetlić region formularza, musisz otworzyć odpowiedni element programu Outlook. Na przykład, jeśli sąsiadujący region formularza jest dołączany na końcu elementu poczty, Otwórz element poczty.

## <a name="deploy-a-form-region"></a><a name="Deploying"></a> Wdróż region formularza
 Regiony formularzy są wdrażane automatycznie przy użyciu skojarzonego dodatku VSTO programu Outlook. W związku z tym nie trzeba wykonywać żadnych specjalnych zadań w celu wdrożenia regionu formularza. Aby uzyskać więcej informacji o wdrażaniu dodatków VSTO, zobacz [wdrażanie rozwiązania pakietu Office](../vsto/deploying-an-office-solution.md).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Zawiera informacje, które mogą pomóc zoptymalizować regiony formularzy i uniknąć potencjalnych problemów.|
|[Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Pokazuje, w jaki sposób utworzyć region formularza w celu rozciągnięcia standardowego lub niestandardowego formularza Microsoft Office Outlook przy użyciu **nowego kreatora regionu formularza programu Outlook** .|
|[Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Wyjaśnia, jak określić, które Microsoft Office elementy programu Outlook wyświetlają region formularza, kojarząc region formularza z klasą wiadomości każdego elementu.|
|[Przewodnik: Projektowanie regionu formularza programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)|Pokazuje, jak zaprojektować niestandardowy region formularza, który pojawia się jako nowa strona w oknie Inspektora elementu kontaktu.|
|[Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Pokazuje, jak zaprojektować region formularza w programie Microsoft Office Outlook, a następnie zaimportować region formularza do projektu dodatku VSTO programu Outlook przy użyciu nowego kreatora **regionu formularza programu Outlook** .|
|[Dostęp do regionu formularza w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)|Opisuje, jak napisać kod, aby pokazać, ukryć lub zmodyfikować kontrolki w regionie formularza i umożliwić użytkownikom uruchamianie kodu z innych obszarów w projekcie przy użyciu `Globals` klasy.|
|[Instrukcje: zapobieganie wyświetlaniu regionu formularza przez program Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Pokazuje, jak zapobiec wyświetlaniu przez program Microsoft Office regionu formularza dla określonego elementu.|
|Pokazuje, w jaki sposób uzyskać dostęp do elementu programu Outlook, w którym pojawia się region formularza.|
|[Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|Opisuje, jak umożliwić użytkownikom reagowanie na element programu Outlook.|
