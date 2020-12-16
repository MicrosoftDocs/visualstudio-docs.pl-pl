---
title: Pisanie kodu w rozwiązaniach pakietu Office
description: Dowiedz się, jak napisać kod w Microsoft Office rozwiązaniach i poznać sposób, w jaki modele obiektów pakietu Office są uwidocznione w kodzie zarządzanym.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 40ea589cb4406a383876b1f16721f18fc48ebadd
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526029"
---
# <a name="write-code-in-office-solutions"></a>Pisanie kodu w rozwiązaniach pakietu Office
  Istnieją pewne aspekty pisania kodu w projektach pakietu Office, które różnią się od innych typów projektów w programie Visual Studio. Wiele z tych różnic jest związanych ze sposobem, w jaki modele obiektów pakietu Office są uwidocznione w kodzie zarządzanym. Inne różnice są związane z projektowaniem projektów pakietu Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>Kod zarządzany i Programowanie Office
 Kluczową technologią tworzenia zintegrowanego rozwiązania Microsoft Office jest Automatyzacja, która jest częścią technologii Component Object Model (COM). Automatyzacja umożliwia tworzenie i kontrolowanie obiektów oprogramowania narażonych przez dowolną aplikację, bibliotekę DLL lub kontrolkę ActiveX, która obsługuje odpowiednie interfejsy programistyczne.

### <a name="understand-primary-interop-assemblies"></a>Omówienie podstawowych zestawów międzyoperacyjnych
 Microsoft Office aplikacje uwidaczniają wiele funkcji do automatyzacji. Nie można jednak używać kodu zarządzanego (takiego jak Visual Basic lub C#) bezpośrednio do automatyzowania aplikacji pakietu Office. Aby zautomatyzować aplikacje pakietu Office za pomocą kodu zarządzanego, należy użyć podstawowych zestawów międzyoperacyjnych pakietu Office (zestawów PIA). Podstawowe zestawy międzyoperacyjności umożliwiają współdziałanie kodu zarządzanego z modelem obiektów opartym na modelu COM aplikacji pakietu Office.

 Każda aplikacja Microsoft Office ma PIA. Podczas tworzenia projektu pakietu Office w programie Visual Studio odwołanie do odpowiedniego PIA jest automatycznie dodawane do projektu. Aby zautomatyzować funkcje innych aplikacji pakietu Office z projektu, musisz ręcznie dodać odwołanie do odpowiedniego PIA. Aby uzyskać więcej informacji, zobacz [jak: docelowa aplikacja pakietu Office za poorednictwem podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Używanie podstawowych zestawów międzyoperacyjnych w czasie projektowania i w czasie wykonywania
 Aby wykonywać większość zadań programistycznych, należy zainstalować i zarejestrować pakiet Office zestawów PIA w globalnej pamięci podręcznej zestawów na komputerze deweloperskim. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

 Na komputerach użytkowników końcowych nie są wymagane w celu uruchamiania rozwiązań pakietu Office przeznaczonych dla programu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszych. Aby uzyskać więcej informacji, zobacz [projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="use-types-in-primary-interop-assemblies"></a>Użyj typów w podstawowych zestawach międzyoperacyjnych
 Zestawów PIA pakietu Office zawiera kombinację typów, które uwidaczniają model obiektów aplikacji pakietu Office i dodatkowe typy infrastruktury, które nie są przeznaczone do użycia bezpośrednio w kodzie. Aby zapoznać się z omówieniem typów w zestawów PIA pakietu Office, zobacz [Omówienie klas i interfejsów w podstawowych zestawach międzyoperacyjnych pakietu Office](/previous-versions/office/office-12/ms247299\(v\=office.12\)).

 Ponieważ typy w zestawów PIA pakietu Office odpowiadają typom w modelach obiektów opartych na modelu COM, sposób używania tych typów często różni się od innych typów zarządzanych. Na przykład sposób wywoływania metod, które mają opcjonalne parametry w podstawowym zestawie międzyoperacyjności pakietu Office, zależy od języka programowania, który jest używany w projekcie. Aby uzyskać więcej informacji, zobacz następujące tematy:

- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).

- [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).

## <a name="program-model-of-office-projects"></a>Model programu projektów pakietu Office
 Wszystkie projekty pakietu Office obejmują co najmniej jedną wygenerowaną klasę, która udostępnia punkt wejścia dla kodu. Te klasy zapewniają również dostęp do modelu obiektów aplikacji hosta i dostępu do funkcji, takich jak okienka Akcje i niestandardowe okienka zadań.

### <a name="understand-the-generated-classes"></a>Zrozumienie wygenerowanych klas
 W projektach na poziomie dokumentu dla programów Excel i Word wygenerowana Klasa jest podobna do obiektu najwyższego poziomu w modelu obiektów aplikacji. Na przykład wygenerowana `ThisDocument` Klasa w projekcie dokumentu programu Word zawiera te same elementy członkowskie co <xref:Microsoft.Office.Interop.Word.Document> Klasa w modelu obiektów programu Word. Aby uzyskać więcej informacji na temat wygenerowanych klas w projektach na poziomie dokumentu, zapoznaj się z tematem [Dostosowywanie na poziomie dokumentu](../vsto/programming-document-level-customizations.md).

 Projekty dodatków VSTO zapewniają wygenerowaną klasę o nazwie `ThisAddIn` . Ta klasa nie jest podobna do klasy w modelu obiektów aplikacji hosta. Zamiast tego Klasa ta reprezentuje dodatek VSTO i udostępnia elementy członkowskie, których można użyć w celu uzyskania dostępu do modelu obiektów aplikacji hosta i uzyskiwania dostępu do innych funkcji dostępnych dla dodatków narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

 Wszystkie wygenerowane klasy w projektach pakietu Office obejmują `Startup` `Shutdown` programy obsługi zdarzeń i. Aby rozpocząć pisanie kodu, zazwyczaj Dodaj kod do tych programów obsługi zdarzeń. Aby zainicjować dodatek narzędzi VSTO, można dodać kod do `Startup` programu obsługi zdarzeń. Aby wyczyścić zasoby używane przez dodatek VSTO, można dodać kod do `Shutdown` programu obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="access-the-generated-classes-at-run-time"></a>Uzyskiwanie dostępu do wygenerowanych klas w czasie wykonywania
 Po załadowaniu rozwiązania pakietu Office tworzy ono [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wystąpienie każdego z wygenerowanych klas w projekcie. Możesz uzyskać dostęp do tych obiektów z dowolnego kodu w projekcie za pomocą `Globals` klasy. Na przykład można użyć `Globals` klasy do wywołania kodu w `ThisAddIn` klasie z procedury obsługi zdarzeń wstążki w dodatku VSTO.

 Aby uzyskać więcej informacji, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="namespace-considerations-in-office-solutions"></a>Zagadnienia dotyczące przestrzeni nazw w rozwiązaniach pakietu Office
 Po utworzeniu projektu nie można zmienić *domyślnej przestrzeni nazw* (lub *głównego obszaru nazw* w Visual Basic) projektu pakietu Office. Domyślna przestrzeń nazw będzie zawsze zgodna z nazwą projektu określoną podczas tworzenia projektu. W przypadku zmiany nazwy projektu domyślna przestrzeń nazw nie zostanie zmieniona. Aby uzyskać więcej informacji o domyślnej przestrzeni nazw w projektach, zobacz [Strona aplikacji, Projektant projektu &#40;C&#35;&#41;](../ide/reference/application-page-project-designer-csharp.md) i [Strona aplikacji, projektant projektu &#40;Visual Basic&#41;](../ide/reference/application-page-project-designer-visual-basic.md).

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>Zmień przestrzeń nazw klas elementów hosta w projektach C#
 Klasy elementów hosta (na przykład, `ThisAddIn` `ThisWorkbook` , lub `ThisDocument` klasy) mają własne przestrzenie nazw w projektach pakietu Office w języku Visual C#. Domyślnie przestrzeń nazw dla elementów hosta w projekcie jest zgodna z nazwą projektu określoną podczas tworzenia projektu.

 Aby zmienić przestrzeń nazw elementów hosta w projekcie pakietu Visual C#, użyj **przestrzeni nazw dla właściwości element hosta** . Aby uzyskać więcej informacji, zobacz [właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md).

## <a name="supported-programming-languages-in-office-projects"></a>Obsługiwane języki programowania w projektach pakietu Office
 Szablony projektów pakietu Office w programie Visual Studio obsługują tylko języki programowania Visual Basic i Visual C#. W związku z tym te szablony projektu są dostępne tylko w węzłach **Visual Basic** i **Visual C#** okna dialogowego **Nowy projekt** w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="language-choice-and-office-programming"></a>Wybór języka i Programowanie Office
 Microsoft Office i Visual Basic for Applications (VBA) zostały opracowane do współdziałania w celu zoptymalizowania przepływu pracy dostosowywania aplikacji. Visual Basic dziedziczył niektóre z tych zmian. Na przykład Visual Basic obsługuje parametry opcjonalne, co oznacza, że można napisać mniej kodu podczas wywoływania niektórych metod w Microsoft Office podstawowych zestawów międzyoperacyjnych, niż w przypadku używania języka Visual C#.

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Program z Visual Basic a Visual C# w rozwiązaniach pakietu Office
 Możesz tworzyć rozwiązania pakietu Office przy użyciu programu Visual Basic lub Visual C#. Ponieważ Microsoft Office modele obiektów zostały zaprojektowane do użycia z programem Microsoft Visual Basic for Applications (VBA), Visual Basic deweloperzy mogą wygodnie współpracować z obiektami udostępnianymi przez aplikacje Microsoft Office. Deweloperzy języka Visual C# mogą korzystać z większości tych samych funkcji co Visual Basic deweloperów, ale zdarzają się sytuacje, w których muszą napisać dodatkowy kod, aby korzystać z modeli obiektów pakietu Office. Istnieją także pewne różnice między podstawowymi funkcjami programistycznymi w programowaniu pakietu Office i kodem zarządzanym, które są zapisywane w Visual Basic i C#.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Kluczowe różnice między Visual Basic i Visual C #
<!-- markdownlint-enable MD003 MD020 -->

W poniższej tabeli przedstawiono kluczowe różnice między Visual Basic i Visual C# w programie Office Development.

|Cechy|Opis|Obsługa Visual Basic|Obsługa języka Visual C#|
|-------------|-----------------|--------------------------|------------------------|
|Parametry opcjonalne|Wiele metod Microsoft Office ma parametry, które nie są wymagane w przypadku wywołania metody. Jeśli dla parametru nie jest przenoszona żadna wartość, zostanie użyta wartość domyślna.|Visual Basic obsługuje parametry opcjonalne.|Visual C# obsługuje parametry opcjonalne w większości przypadków. Aby uzyskać więcej informacji, zobacz [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).|
|Przekazywanie parametrów według odwołania|Parametry opcjonalne w większości Microsoft Office podstawowych zestawów międzyoperacyjnych mogą być przesyłane przez wartość. Jednak w niektórych podstawowych zestawach międzyoperacyjnych parametry opcjonalne, które akceptują typy odwołań, muszą być przesyłane przez odwołanie.<br /><br /> Aby uzyskać więcej informacji na temat parametrów typu wartości i odwołania, zobacz [przekazywanie argumentów według wartości i przez odwołanie &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (dla Visual Basic) i [parametrów Pass &#40;C&#35; Przewodnik programowania&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Do przekazywania parametrów przez odwołanie nie są konieczne żadne dodatkowe prace. Kompilator Visual Basic automatycznie przekazuje parametry przez odwołanie, jeśli jest to konieczne.|W większości przypadków kompilator Visual C# automatycznie przekazuje parametry przez odwołanie, jeśli jest to konieczne. Aby uzyskać więcej informacji, zobacz [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).|
|Właściwości sparametryzowane|Niektóre właściwości akceptują parametry i działają jako funkcje tylko do odczytu.|Visual Basic obsługuje właściwości, które akceptują parametry.|Visual C# obsługuje właściwości, które akceptują parametry.|
|Późne wiązanie|Późne wiązanie polega na określeniu właściwości obiektów w czasie wykonywania zamiast rzutowania zmiennych na typ obiektu w czasie projektowania.|Visual Basic wykonuje późne wiązanie, gdy **opcja Strict** jest wyłączona. Gdy **opcja Strict** jest włączona, należy jawnie skonwertować obiekty i użyć typów w <xref:System.Reflection> przestrzeni nazw w celu uzyskania dostępu do późnych elementów członkowskich. Aby uzyskać więcej informacji, zobacz [późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).|Visual C# wykonuje późne powiązania w projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Aby uzyskać więcej informacji, zobacz [późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).|

## <a name="key-differences-between-office-development-and-managed-code"></a>Kluczowe różnice między programowaniem pakietu Office i kodem zarządzanym
 W poniższej tabeli przedstawiono kluczowe różnice między programowaniem pakietu Office i kodem zarządzanym w Visual Basic lub Visual C#.

|Cechy|Opis|Obsługa Visual Basic i Visual C#|
|-------------|-----------------|-----------------------------------------|
|Indeksy tablicy|Dolna granica tablicy dla kolekcji w aplikacjach Microsoft Office rozpoczyna się od 1. Visual Basic i Visual C# używają tablic opartych na protokole 0. Aby uzyskać więcej informacji, zobacz [tablice &#40;C&#35; Przewodnik programowania&#41;](/dotnet/csharp/programming-guide/arrays/index) i [tablic w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Aby uzyskać dostęp do pierwszego elementu kolekcji w modelu obiektów aplikacji Microsoft Office, Użyj indeksu 1 zamiast 0.|

## <a name="see-also"></a>Zobacz też

- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md)
- [Jak: docelowa aplikacja pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)
- [Programowanie zespołowe rozwiązań pakietu Office](../vsto/collaborative-development-of-office-solutions.md)
