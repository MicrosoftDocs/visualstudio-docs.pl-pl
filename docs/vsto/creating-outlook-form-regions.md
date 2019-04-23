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
ms.openlocfilehash: ea3f72a26938a50cddbb622565173be603436ba3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60092763"
---
# <a name="create-outlook-form-regions"></a>Tworzenie regionów formularzy programu Outlook
  Regiony formularzy służy do dostosowywania formularzy programu Microsoft Office Outlook. Visual Studio zapewnia zaawansowane narzędzia, które ułatwiają służących do projektowania, opracowywania i debugowania regionów formularza.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Ten temat zawiera następujące informacje:

- [Zalety korzystania z regionów formularzy](#Enhance)

- [Dodawanie regionów formularzy programu Outlook do projektu](#Adding)

- [Użyj projektanta regionów formularza](#UsingFormRegionDesigner)

- [Użyj regionów formularzy zaprojektowanych w programie Outlook](#UsingFormRegionDesignedOutlook)

- [Dodaj kod niestandardowy do regionu formularza](#AddingCustomCode)

- [Skompiluj projekt](#Building)

- [Debugowanie regionu formularza](#Debugging)

- [Wdrażanie regionów formularzy](#Deploying)

## <a name="Enhance"></a> Zalety korzystania z regionów formularzy
 Regiony formularzy oferuje wiele udoskonaleń za pośrednictwem tradycyjnych tworzeniu formularzy programu Outlook:

- Dostosowywanie domyślnej strony jakiejkolwiek formy standardowych.

- Dodaj do 12 dodatkowych stron do żadnych standardowych formularza.

- Zastąp lub poprawić wszelkie formularza standardowego.

- Wyświetl niestandardowy interfejs użytkownika, w okienku odczytu i inspektorzy.

  Aby uzyskać więcej informacji, zobacz [dostosowywanie stron formularza i regionów formularzy w](/office/vba/outlook/Concepts/Forms/customizing-form-pages-and-form-regions).

## <a name="Adding"></a> Dodawanie regionów formularzy programu Outlook do projektu
 Możesz użyć **nowy Region formularza programu Outlook** kreatora w celu zaprojektowania nowego regionu formularza lub zaimportować regionu formularza zaprojektowanego w programie Outlook. Ponadto jeśli region formularza, które było używane w innym projekcie dodatku narzędzi VSTO dla programu Outlook, można ponownie użyć Twojego istniejącego regionu formularza.

### <a name="CreatingFormRegion"></a> Utwórz nowy region formularza za pomocą Kreatora
 Aby utworzyć regionu formularza, Dodaj **Region formularza programu Outlook** elementu do projektu dodatku narzędzi VSTO dla programu Outlook. Spowoduje to uruchomienie **nowy Region formularza programu Outlook** kreatora.

 Użyj kreatora, aby wskazać, czy użytkownik chce zaprojektować nowy region formularza lub zaimportować regionu formularza zaprojektowanego w programie Outlook. Aby uzyskać więcej informacji na temat projektowania nowy region formularza, zobacz [użyć projektanta regionów formularza](#UsingFormRegionDesigner). Aby uzyskać więcej informacji na temat korzystania z regionów formularzy zaprojektowanych w programie Outlook, zobacz [importowanie regionów formularzy zaprojektowanych w programie Outlook](#UsingFormRegionDesignedOutlook).

 Użyj kreatora, aby określić typ regionu formularza, który chcesz utworzyć. W poniższej tabeli opisano każdy typ regionu formularza.

|Typ regionu|Opis|
|-----------------|-----------------|
|Oddzielne|Dodaje regionu formularza jako nową stronę w formularzu programu Outlook.|
|Sąsiadujące|Dołącza regionu formularza do dolnej części strony domyślnego formularza programu Outlook.|
|Zastępczy|Dodaje regionu formularza jako nową stronę, która zastępuje domyślną stronę formularza programu Outlook.|
|Zamień wszystkie|Zastępuje cały formularz programu Outlook z regionu formularza.|

 Można także użyć kreatora, aby określają warunki, wyświetlania i wybrać typ formularza, aby rozszerzyć. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

 Wybrane opcje, które wprowadzasz w Kreatorze wpływają na opcje, które są dostępne na innych stronach kreatora. Na przykład w przypadku wybrania **sąsiedniego** lub **oddzielnych** w **utworzyć nowy Region formularza programu Outlook** strony, a następnie **tytuł** i **Opis** pola są niedostępne w **tekst opisu i wybierz preferencje wyświetlania** strony. Jest to spowodowane programu Outlook nie używa tych pól podczas Wyświetla sąsiednimi ani oddzielna regionu formularza.

#### <a name="form-region-files"></a>Pliki regionu formularza
 Po zakończeniu **nowy Region formularza programu Outlook** kreatora, Visual Studio automatycznie dodaje następujące pliki do projektu:

- Plik kodu regionu formularza. Ten plik ma nazwę określoną dla **Region formularza programu Outlook** pozycja **Dodaj nowy element** okno dialogowe. Dodaj kod do obsługi zdarzeń regionu formularza do tego pliku.

- Plik kodu projektanta regionów formularza. Ten plik zawiera kod generowany przez projektanta regionów formularza i nie należy bezpośrednio edytować.

- Magazynu formularzy programu Outlook (*OFS*) pliku.

    > [!NOTE]
    >  Ten plik zostanie dodany do projektu tylko, Jeśli importujesz regionu formularza zaprojektowanego w programie Outlook.

#### <a name="form-region-factory-class"></a>Klasa fabryka regionów formularza
 Plik kodu regionu formularza zawiera częściową klasą, która implementuje <xref:Microsoft.Office.Tools.Outlook.IFormRegionFactory> interfejsu. Jest to klasa fabryka regionów formularza. Klasa fabryka regionów formularza jest odpowiedzialny za tworzenie nowych wystąpień regionu formularza.

 Ta klasa można znaleźć, rozwijając **fabryka regionów formularza** regionu.

 **Nowy Region formularza programu Outlook** Kreator dodaje atrybuty do tej klasy, która umożliwia określenie nazwy wewnętrznej regionu formularza i klasy wiadomości, które wyświetlania regionu formularza. Należy ręcznie modyfikować te atrybuty, po dodaniu pliku do projektu.

 Większość klas fabryki region formularza jest zaimplementowana w pliku projektanta regionów formularza. Jednak `FormRegionInitializing` program obsługi zdarzeń jest widoczna w pliku kodu regionu formularza. Ta procedura obsługi zdarzeń służy do określenia, czy region formularza powinien być wyświetlany programu Outlook. Aby uzyskać więcej informacji, zobacz [obsługi zdarzeń regionu formularza](#HandlingFormRegionEvents).

### <a name="AddingExistingFormRegion"></a> Dodawanie istniejącego regionu formularza do projektu
 W przypadku regionów formularzy programu Outlook, które było używane w innym projekcie programu Outlook może używać go w bieżącym projekcie dodatku narzędzi VSTO dla programu Outlook przy użyciu **Dodaj istniejący element** okno dialogowe.

 Istniejącego regionu formularza, musisz mieć plik kodu (*.vb* lub *.cs*); nie można dodać magazynu formularzy programu Outlook (*OFS*) plików za pomocą **Dodaj istniejący element** okno dialogowe. Można jednak utworzyć nowy region formularza, importując plik magazynu formularzy programu Outlook. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

## <a name="UsingFormRegionDesigner"></a> Użyj projektanta regionów formularza
 Projektanta regionów formularza ułatwia projektowanie układ i wygląd regionu formularza. Przeciągnij zarządzane formanty do powierzchni projektanta, kliknij dwukrotnie ikonę kontrolki, można otworzyć procedury obsługi zdarzeń i ustawianie właściwości w **właściwości** okna.

> [!NOTE]
>  Można znaleźć właściwości, które wpływają na sposób wyświetlania regionu formularza programu Outlook pod **manifestu** w węźle **właściwości** okna.

 Projektanta regionów formularza jest dostępna tylko w przypadku wybrania **projektowania nowy Region formularza** w **wybierz sposób tworzenia regionu formularza** strony **nowy Region formularza programu Outlook** Kreator.

 Istnieją trzy sposoby otwierania projektanta regionów formularza:

- W **Eksploratora rozwiązań**, kliknij dwukrotnie plik kodu regionu formularza.

- W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik kodu regionu formularza, a następnie kliknij **Projektant widoków**.

- W **Eksploratora rozwiązań**, wybierz plik kodu regionu formularza, a następnie na **widoku** menu, kliknij przycisk **projektanta**.

  Obsługuje projektanta regionów formularza tylko zarządzane formanty. Nie można dodać kontrolki natywne programu Outlook.

## <a name="UsingFormRegionDesignedOutlook"></a> Importowanie regionów formularzy zaprojektowanych w programie Outlook
 Podczas projektowania w programie Outlook, można dodać kontrolki natywne programu Outlook do regionu formularza. Natywne kontrolki programu Outlook umożliwia powiązanie z danymi programu Outlook w czasie projektowania. Jednak nie można następnie użyć projektanta regionów formularza dodać zarządzane formanty lub zmienić wygląd regionu formularza.

 Można zaimportować regionów formularzy w projekcie dodatku narzędzi VSTO dla programu Outlook przy użyciu **nowy Region formularza programu Outlook** kreatora. Na **wybierz sposób tworzenia regionu formularza** wybierz **Importuj plik magazynu formularzy programu Outlook (ofs)**. Następnie możesz przejść do lokalizacji pliku magazynu formularzy programu Outlook (*OFS*) pliku. (Outlook zapisuje regionów formularza jako *OFS* pliki.)

 **Nowy Region formularza programu Outlook** Kreatora kopii *OFS* plik do katalogu projektu i dodaje formant odwołania do pliku projektanta regionów formularza. Następnie można obsługiwać zdarzenia formantu w pliku kodu regionu formularza.

 Do obsługi zdarzeń w projektach Visual Basic, wybierz zdarzenie z listy Nazwa metody u góry strony edytora kodu.

 Do obsługi zdarzeń w C# projektu, należy subskrybować zdarzenia obiektu Controls w <xref:Microsoft.Office.Tools.Outlook.FormRegionControl.FormRegionShowing> metody. Aby uzyskać więcej informacji, zobacz [jak: Subskrybowanie i anulowanie subskrypcji zdarzeń &#40;C&#35; Podręcznik programowania&#41;](/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events).

 Można zmienić właściwości regionu formularza w `InitializeManifest` metody klasy fabryka regionów formularza.

> [!NOTE]
>  Aby zaimportować regionu formularza, jest możliwe w projektach przeznaczonych tę samą wersję programu Outlook, który jest zainstalowany na komputerze deweloperskim. Na przykład, jeśli masz zainstalowany program Outlook 2010, importowanie formularza region będzie działają tylko w projekcie został utworzony przy użyciu **programu Outlook 2010 dodatków** szablonu projektu.

### <a name="update-an-imported-form-regions-design"></a>Aktualizowanie projektu z regionu formularza zaimportowany
 Możesz dodać, usunąć ani zmienić formantów na region formularza. Zanim to zrobisz, Utwórz kopię zapasową jakiegokolwiek kodu, który został dodany do pliku kodu regionu formularza. Następnie otwórz *OFS* pliku w programie Outlook, zmodyfikuj regionu formularza, a następnie zapisz zmiany. Użyj **nowy Region formularza programu Outlook** kreatora do zaimportowania zmodyfikowanego *OFS* pliku. Następnie można wkleić kod do nowego pliku kodu regionu formularza.

## <a name="AddingCustomCode"></a> Dodaj kod niestandardowy do regionu formularza
 <xref:Microsoft.Office.Tools.Outlook> Przestrzeń nazw zapewnia dostęp do klas, które reprezentują regionu formularza, elementu programu Outlook, który wyświetla regionu formularza i inne przydatne elementy. **Region formularza programu Outlook** elementu automatycznie dodaje odwołanie do tego zestawu w projekcie i wstawia odpowiednią **przy użyciu** lub **Importy** instrukcji na górze plik kodu regionu formularza.

 Można użyć klas, metod i właściwości w `Microsoft.Office.Interop.Outlook` przestrzeni nazw do wykonywania większości programem Outlook zadania programowania. Aby uzyskać więcej informacji na temat modelu obiektów programu Outlook, zobacz [model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md). Przykłady typowych zadań, które korzystać z modelu obiektów programu Outlook, zobacz [rozwiązania programu Outlook](../vsto/outlook-solutions.md).

### <a name="HandlingFormRegionEvents"></a> Obsługa zdarzeń regionu formularza
 **Region formularza programu Outlook** elementu automatycznie dodaje następujące obsługi trzech zdarzeń do pliku kodu regionu formularza.

|Zdarzenie|Opis|
|-----------|-----------------|
|FormRegionInitializing|Występuje, zanim region formularza zostanie zainicjowany. Możesz sprawdzić warunki w tej obsługi zdarzeń, aby ustalić, czy region formularza powinien być wyświetlany programu Outlook. Aby uzyskać więcej informacji, zobacz [jak: Ochrona programu Outlook przed wyświetlaniem regionów formularzy](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).|
|FormRegionShowing|Występuje po utworzeniu wystąpienia obszaru formularza, ale przed pojawieniem się obszaru formularza.|
|FormRegionClosed|Występuje przed zamknięciem obszaru formularza.|

## <a name="Building"></a> Skompiluj projekt
 Podczas tworzenia projektu dodatku narzędzi VSTO dla programu Outlook zawierający regionu formularza programu Visual Studio dodaje następujące informacje do rejestru:

- Klucz dla każdej klasy wiadomości, który jest skojarzony z co najmniej jeden region formularza.

- Wpis dla każdego regionu formularza i skojarzoną wartość, która reprezentuje nazwę dodatku narzędzi VSTO dla programu Outlook.

  Program Outlook używa tych informacji do załadowania regionów formularza.

## <a name="Debugging"></a> Debugowanie regionu formularza
 Można debugować dodatku narzędzi VSTO dla programu Outlook zawiera region formularza tak samo, jak debuguje się inne [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] projektów. Po uruchomieniu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] debugera programu Visual Studio automatycznie uruchamia program Outlook.

 Aby wyświetlić regionu formularza, należy otworzyć odpowiednią elementu programu Outlook. Na przykład jeśli przylegającym regionie formularza jest dołączany na końcu elementu poczty, otwórz element poczty.

## <a name="Deploying"></a> Wdrażanie regionów formularzy
 Regiony formularzy są wdrażane automatycznie przy użyciu skojarzonego dodatku narzędzi VSTO dla programu Outlook. W związku z tym nie masz do wykonywania zadań specjalnych, aby wdrożyć regionu formularza. Aby uzyskać więcej informacji dotyczących wdrażania dodatków narzędzi VSTO dla programów, zobacz [wdrożyć rozwiązanie Office](../vsto/deploying-an-office-solution.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wytyczne dotyczące tworzenia regionów formularzy programu Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)|Zawiera informacje, które mogą pomóc w optymalizacji regionów formularzy w sieci i uniknąć potencjalnych problemów.|
|[Instrukcje: Dodawanie regionu formularza do projektu dodatku programu Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)|Przedstawiono sposób tworzenia regionu formularza, aby rozszerzyć standardowy lub niestandardowy formularz programu Microsoft Office Outlook za pomocą **nowy Region formularza programu Outlook** kreatora.|
|[Kojarzenie regionu formularza z klasą wiadomości programu Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)|Wyjaśnia, jak określić elementy, które program Microsoft Office Outlook wyświetlania regionu formularza przez kojarzenie regionu formularza z klasą wiadomości dla każdego elementu.|
|[Przewodnik: Projektowanie regionów formularzy programu Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)|Pokazuje, jak projektować region formularza niestandardowego, który jest wyświetlany jako nową stronę w oknie Inspektora, skontaktuj się z elementu.|
|[Przewodnik: Importowanie regionów formularzy zaprojektowanych w programie Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)|Pokazuje, jak projektowanie regionów formularzy w programie Microsoft Office Outlook, a następnie zaimportuj regionu formularza w projekcie dodatku narzędzi VSTO dla programu Outlook, za pomocą **nowy Region formularza programu Outlook** kreatora.|
|[Dostęp do regionów formularzy w czasie wykonywania](../vsto/accessing-a-form-region-at-run-time.md)|W tym artykule opisano jak napisać kod, aby Pokazywanie, ukrywanie i modyfikowania formantów na region formularza i umożliwienie użytkownikom uruchomić kod z innych obszarów w projekcie za pomocą `Globals` klasy.|
|[Instrukcje: Ochrona programu Outlook przed wyświetlaniem regionów formularzy](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)|Przedstawia sposób zapobiec programu Microsoft Office Outlook przed wyświetlaniem regionów formularzy dla konkretnego elementu.|
|Pokazuje, jak dostęp do elementu programu Outlook, w którym wyświetlania regionu formularza.|
|[Niestandardowe akcje w regionach formularzy programu Outlook](../vsto/custom-actions-in-outlook-form-regions.md)|W tym artykule opisano, jak umożliwić użytkownikom reagowanie na elementu programu Outlook.|
