---
title: Pisanie kodu w rozwiązaniach pakietu Office
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cead0569ae067fcc503f7f2074807c609e6eed75
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255046"
---
# <a name="write-code-in-office-solutions"></a>Pisanie kodu w rozwiązaniach pakietu Office
  Istnieją pewne aspekty pisania kodu w projektach pakietu Office, które różnią się od innych typów projektów w programie Visual Studio. Wiele z tych różnic jest związanych ze sposobem, w jaki modele obiektów pakietu Office są uwidocznione w kodzie zarządzanym. Inne różnice są związane z projektowaniem projektów pakietu Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>Kod zarządzany i Programowanie Office
 Kluczową technologią tworzenia zintegrowanego rozwiązania Microsoft Office jest Automatyzacja, która jest częścią technologii Component Object Model (COM). Automatyzacja umożliwia tworzenie i kontrolowanie obiektów oprogramowania narażonych przez dowolną aplikację, bibliotekę DLL lub kontrolkę ActiveX, która obsługuje odpowiednie interfejsy programistyczne.

### <a name="understand-primary-interop-assemblies"></a>Omówienie podstawowych zestawów międzyoperacyjnych
 Microsoft Office aplikacje uwidaczniają wiele funkcji do automatyzacji. Nie można jednak używać kodu zarządzanego (takiego jak Visual Basic lub C#) bezpośrednio do automatyzowania aplikacji pakietu Office. Aby zautomatyzować aplikacje pakietu Office za pomocą kodu zarządzanego, należy użyć podstawowych zestawów międzyoperacyjnych pakietu Office (zestawów PIA). Podstawowe zestawy międzyoperacyjności umożliwiają współdziałanie kodu zarządzanego z modelem obiektów opartym na modelu COM aplikacji pakietu Office.

 Każda aplikacja Microsoft Office ma PIA. Podczas tworzenia projektu pakietu Office w programie Visual Studio odwołanie do odpowiedniego PIA jest automatycznie dodawane do projektu. Aby zautomatyzować funkcje innych aplikacji pakietu Office z projektu, musisz ręcznie dodać odwołanie do odpowiedniego PIA. Aby uzyskać więcej informacji, zobacz [jak: Docelowa aplikacja pakietu Office przy](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)użyciu podstawowych zestawów międzyoperacyjnych.

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Używanie podstawowych zestawów międzyoperacyjnych w czasie projektowania i w czasie wykonywania
 Aby wykonywać większość zadań programistycznych, należy zainstalować i zarejestrować pakiet Office zestawów PIA w globalnej pamięci podręcznej zestawów na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

 Na komputerach użytkowników końcowych nie są wymagane w celu uruchamiania rozwiązań pakietu Office przeznaczonych dla programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="use-types-in-primary-interop-assemblies"></a>Użyj typów w podstawowych zestawach międzyoperacyjnych
 Zestawów PIA pakietu Office zawiera kombinację typów, które uwidaczniają model obiektów aplikacji pakietu Office i dodatkowe typy infrastruktury, które nie są przeznaczone do użycia bezpośrednio w kodzie. Aby zapoznać się z omówieniem typów w zestawów PIA pakietu Office, zobacz [Omówienie klas i interfejsów w podstawowych zestawach międzyoperacyjnych pakietu Office](/previous-versions/office/office-12/ms247299\(v\=office.12\)).

 Ponieważ typy w zestawów PIA pakietu Office odpowiadają typom w modelach obiektów opartych na modelu COM, sposób używania tych typów często różni się od innych typów zarządzanych. Na przykład sposób wywoływania metod, które mają opcjonalne parametry w podstawowym zestawie międzyoperacyjności pakietu Office, zależy od języka programowania, który jest używany w projekcie. Więcej informacji znajduje się w następujących tematach:

- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).

- [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).

## <a name="program-model-of-office-projects"></a>Model programu projektów pakietu Office
 Wszystkie projekty pakietu Office obejmują co najmniej jedną wygenerowaną klasę, która udostępnia punkt wejścia dla kodu. Te klasy zapewniają również dostęp do modelu obiektów aplikacji hosta i dostępu do funkcji, takich jak okienka Akcje i niestandardowe okienka zadań.

### <a name="understand-the-generated-classes"></a>Zrozumienie wygenerowanych klas
 W projektach na poziomie dokumentu dla programów Excel i Word wygenerowana Klasa jest podobna do obiektu najwyższego poziomu w modelu obiektów aplikacji. Na przykład wygenerowana `ThisDocument` Klasa w projekcie dokumentu programu Word zawiera te same elementy członkowskie <xref:Microsoft.Office.Interop.Word.Document> co Klasa w modelu obiektów programu Word. Aby uzyskać więcej informacji na temat wygenerowanych klas w projektach na poziomie dokumentu, zapoznaj się z tematem [Dostosowywanie na poziomie dokumentu](../vsto/programming-document-level-customizations.md).

 Projekty dodatków VSTO zapewniają wygenerowaną klasę o nazwie `ThisAddIn`. Ta klasa nie jest podobna do klasy w modelu obiektów aplikacji hosta. Zamiast tego Klasa ta reprezentuje dodatek VSTO i udostępnia elementy członkowskie, których można użyć w celu uzyskania dostępu do modelu obiektów aplikacji hosta i uzyskiwania dostępu do innych funkcji dostępnych dla dodatków narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

 Wszystkie wygenerowane klasy w projektach pakietu `Startup` Office `Shutdown` obejmują programy obsługi zdarzeń i. Aby rozpocząć pisanie kodu, zazwyczaj Dodaj kod do tych programów obsługi zdarzeń. Aby zainicjować dodatek narzędzi VSTO, można dodać kod do `Startup` programu obsługi zdarzeń. Aby wyczyścić zasoby używane przez dodatek VSTO, można dodać kod do `Shutdown` programu obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="access-the-generated-classes-at-run-time"></a>Uzyskiwanie dostępu do wygenerowanych klas w czasie wykonywania
 Po załadowaniu [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rozwiązania pakietu Office tworzy ono wystąpienie każdego z wygenerowanych klas w projekcie. Możesz uzyskać dostęp do tych obiektów z dowolnego kodu w projekcie za pomocą `Globals` klasy. Na przykład można użyć `Globals` klasy do wywołania kodu `ThisAddIn` w klasie z procedury obsługi zdarzeń wstążki w dodatku VSTO.

 Aby uzyskać więcej informacji, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="namespace-considerations-in-office-solutions"></a>Zagadnienia dotyczące przestrzeni nazw w rozwiązaniach pakietu Office
 Po utworzeniu projektu nie można zmienić *domyślnej przestrzeni nazw* (lub *głównego obszaru nazw* w Visual Basic) projektu pakietu Office. Domyślna przestrzeń nazw będzie zawsze zgodna z nazwą projektu określoną podczas tworzenia projektu. W przypadku zmiany nazwy projektu domyślna przestrzeń nazw nie zostanie zmieniona. Aby uzyskać więcej informacji o domyślnej przestrzeni nazw w projektach, zobacz [Strona aplikacji, Projektant &#40;projektu&#35; C](../ide/reference/application-page-project-designer-csharp.md) i [Strona aplikacji, Projektant &#40;projektu&#41;Visual Basic](../ide/reference/application-page-project-designer-visual-basic.md).

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>Zmień przestrzeń nazw klas elementów hosta w C# projektach
 Klasy elementów `ThisAddIn`hosta (na przykład `ThisWorkbook`,, lub `ThisDocument` klasy) mają własne przestrzenie nazw w projektach pakietu C# Visual Office. Domyślnie przestrzeń nazw dla elementów hosta w projekcie jest zgodna z nazwą projektu określoną podczas tworzenia projektu.

 Aby zmienić przestrzeń nazw elementów hosta w projekcie programu Visual C# Office, użyj **przestrzeni nazw dla właściwości element hosta** . Aby uzyskać więcej informacji, zobacz [właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md).

## <a name="supported-programming-languages-in-office-projects"></a>Obsługiwane języki programowania w projektach pakietu Office
 Szablony projektów pakietu Office w programie Visual Studio obsługują tylko języki programowania Visual Basic C# i wizualizacji. W związku z tym te szablony projektu są dostępne tylko w **Visual Basic** i w węzłach  **C# wizualizacji** okna dialogowego **Nowy projekt** w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Utwórz projekty pakietu Office w programie](../vsto/how-to-create-office-projects-in-visual-studio.md)Visual Studio.

## <a name="language-choice-and-office-programming"></a>Wybór języka i Programowanie Office
 Microsoft Office i Visual Basic for Applications (VBA) zostały opracowane do współdziałania w celu zoptymalizowania przepływu pracy dostosowywania aplikacji. Visual Basic dziedziczył niektóre z tych zmian. Na przykład Visual Basic obsługuje parametry opcjonalne, co oznacza, że można napisać mniej kodu podczas wywoływania niektórych metod w Microsoft Office podstawowych zestawach międzyoperacyjnych, niż w przypadku C#używania wizualizacji.

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Program z Visual Basic a Wizualizacja C# w rozwiązaniach pakietu Office
 Możesz tworzyć rozwiązania pakietu Office przy użyciu Visual Basic lub wizualizacji C#. Ponieważ Microsoft Office modele obiektów zostały zaprojektowane do użycia z programem Microsoft Visual Basic for Applications (VBA), Visual Basic deweloperzy mogą wygodnie współpracować z obiektami udostępnianymi przez aplikacje Microsoft Office. Deweloperzy C# wizualni mogą korzystać z większości tych samych funkcji co Visual Basic deweloperów, ale zdarzają się sytuacje, w których muszą napisać dodatkowy kod, aby korzystać z modeli obiektów pakietu Office. Istnieją także pewne różnice między podstawowymi funkcjami programistycznymi w programowaniu pakietu Office i kodem zarządzanym, C#które są zapisywane w Visual Basic i.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Kluczowe różnice między Visual Basic i wizualizacjąC#
<!-- markdownlint-enable MD003 MD020 -->

W poniższej tabeli przedstawiono kluczowe różnice między Visual Basic i wizualizacją C# w programowaniu pakietu Office.

|Funkcja|Opis|Obsługa Visual Basic|Obsługa C# wizualizacji|
|-------------|-----------------|--------------------------|------------------------|
|Parametry opcjonalne|Wiele metod Microsoft Office ma parametry, które nie są wymagane w przypadku wywołania metody. Jeśli dla parametru nie jest przenoszona żadna wartość, zostanie użyta wartość domyślna.|Visual Basic obsługuje parametry opcjonalne.|Wizualizacja C# w większości przypadków obsługuje parametry opcjonalne. Aby uzyskać więcej informacji, zobacz [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).|
|Przekazywanie parametrów według odwołania|Parametry opcjonalne w większości Microsoft Office podstawowych zestawów międzyoperacyjnych mogą być przesyłane przez wartość. Jednak w niektórych podstawowych zestawach międzyoperacyjnych parametry opcjonalne, które akceptują typy odwołań, muszą być przesyłane przez odwołanie.<br /><br /> Aby uzyskać więcej informacji na temat parametrów typu wartości i odwołania, zobacz [przekazywanie argumentów według wartości i &#40;przez&#41; odwołanie Visual Basic](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic) i [przekazywanie &#40;parametrów&#35; C Przewodnik&#41;programowania](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Do przekazywania parametrów przez odwołanie nie są konieczne żadne dodatkowe prace. Kompilator Visual Basic automatycznie przekazuje parametry przez odwołanie, jeśli jest to konieczne.|W większości przypadków kompilator wizualny C# automatycznie przekazuje parametry przez odwołanie, jeśli jest to konieczne. Aby uzyskać więcej informacji, zobacz [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).|
|Właściwości sparametryzowane|Niektóre właściwości akceptują parametry i działają jako funkcje tylko do odczytu.|Visual Basic obsługuje właściwości, które akceptują parametry.|Wizualizacja C# obsługuje właściwości, które akceptują parametry.|
|Późne wiązanie|Późne wiązanie polega na określeniu właściwości obiektów w czasie wykonywania zamiast rzutowania zmiennych na typ obiektu w czasie projektowania.|Visual Basic wykonuje późne wiązanie, gdy **opcja Strict** jest wyłączona. Gdy **opcja Strict** jest włączona, należy jawnie skonwertować obiekty i użyć typów w <xref:System.Reflection> przestrzeni nazw w celu uzyskania dostępu do późnych elementów członkowskich. Aby uzyskać więcej informacji, zobacz [późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).|Wizualizacja C# wykonuje późne powiązania w projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Aby uzyskać więcej informacji, zobacz [późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).|

## <a name="key-differences-between-office-development-and-managed-code"></a>Kluczowe różnice między programowaniem pakietu Office i kodem zarządzanym
 W poniższej tabeli przedstawiono kluczowe różnice między programowaniem pakietu Office i kodem zarządzanym, które C#są zapisywane w Visual Basic lub wizualizacji.

|Funkcja|Opis|Obsługa Visual Basic i C# wizualizacji|
|-------------|-----------------|-----------------------------------------|
|Indeksy tablicy|Dolna granica tablicy dla kolekcji w aplikacjach Microsoft Office rozpoczyna się od 1. Visual Basic i wizualizacje C# wykorzystują 0 macierzy. Aby uzyskać więcej informacji, [Zobacz &#40;tablice&#35; &#41; Podręcznik programowania C](/dotnet/csharp/programming-guide/arrays/index) i [tablice w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Aby uzyskać dostęp do pierwszego elementu kolekcji w modelu obiektów aplikacji Microsoft Office, Użyj indeksu 1 zamiast 0.|

## <a name="see-also"></a>Zobacz także

- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md)
- [Instrukcje: Docelowa aplikacja pakietu Office za poorednictwem zestawów podstawowych międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)
- [Programowanie zespołowe rozwiązań pakietu Office](../vsto/collaborative-development-of-office-solutions.md)
