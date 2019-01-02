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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 35c78f03cdb537ef5be2fd3b9004ca713485d3bc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942976"
---
# <a name="write-code-in-office-solutions"></a>Pisanie kodu w rozwiązaniach pakietu Office
  Istnieją pewne aspekty pisanie kodu w projektach pakietu Office, które różnią się od innych typów projektów w programie Visual Studio. Wiele z tych różnic odnoszą się do sposobu modele obiektów pakietu Office są widoczne dla kodu zarządzanego. Inne różnice są związane z projekt projektów Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>Kod zarządzany i programowaniu pakietu Office
 Technologii klucza, który ułatwia tworzenie zintegrowanych rozwiązań programu Microsoft Office jest automatyzacji, który jest częścią technologii Component Object Model (COM). Automatyzacji umożliwia tworzenie i kontrolowanie obiektów oprogramowania udostępniane przez dowolną aplikację, a Biblioteka DLL za pomocą kodu lub kontrolkę ActiveX, która obsługuje odpowiednich interfejsów programistycznych.

### <a name="understand-primary-interop-assemblies"></a>Zrozumienie podstawowych zestawów międzyoperacyjnych
 Aplikacje Microsoft Office uwidocznić większość ich funkcji w usłudze Automation. Nie można jednak użyć kodu zarządzanego (np. Visual Basic lub C#), bezpośrednio do automatyzowania aplikacji pakietu Office. Aby zautomatyzować aplikacje pakietu Office przy użyciu kodu zarządzanego, należy użyć podstawowe zestawy międzyoperacyjne pakietu Office (PIA). Podstawowe zestawy międzyoperacyjne umożliwienia kodowi zarządzanemu do interakcji z modelem obiektów opartym na modelu COM aplikacji pakietu Office.

 Każda aplikacja Microsoft Office zawiera podstawowy zestaw MIĘDZYOPERACYJNY. Podczas tworzenia projektu pakietu Office w Visual Studio, odwołania do odpowiednich PIA są automatycznie dodawane do projektu. Aby zautomatyzować funkcji innych aplikacjach pakietu Office z projektu, można ręcznie dodać odwołania do odpowiednich PIA. Aby uzyskać więcej informacji, zobacz [jak: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Użyj podstawowe zestawy międzyoperacyjne w czasie projektowania i środowiska uruchomieniowego
 Konieczne jest posiadanie zestawów Office PIA zainstalowany i zarejestrowany w globalnej pamięci podręcznej na komputerze deweloperskim do wykonywania większości zadań programistycznych. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

 Zestawy PIA pakietu Office nie są wymagane na komputerach użytkowników końcowych do uruchamiania rozwiązań pakietu Office przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub nowszej. Aby uzyskać więcej informacji, zobacz [projektowania i tworzenia rozwiązań dla pakietu Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="use-types-in-primary-interop-assemblies"></a>Używanie typów w podstawowych zestawów międzyoperacyjnych
 Zestawy PIA pakietu Office zawierają kombinację typów, które uwidaczniają model obiektów aplikacji pakietu Office i typów dodatkowej infrastruktury, które nie są przeznaczone do użycia bezpośrednio w kodzie. Aby uzyskać przegląd typów w zestawy PIA pakietu Office, zobacz [Przegląd klasy i interfejsy podstawowe zestawy międzyoperacyjne pakietu Office](/previous-versions/office/office-12/ms247299\(v\=office.12\)).

 Ponieważ typy w zestawy PIA pakietu Office odpowiadają typom modeli obiektów opartego na modelu COM, sposób, można użyć tych typów często różni się od innych typów zarządzanych. Na przykład sposób wywołania metody, które mają następujące parametry opcjonalne w Office podstawowy zestaw międzyoperacyjny zależy od języka programowania, którego używasz w projekcie. Więcej informacji znajduje się w następujących tematach:

-   [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).

-   [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).

## <a name="program-model-of-office-projects"></a>Program modelu projektów pakietu Office
 Wszystkie projekty pakietu Office zawierają co najmniej jeden wygenerowanej klasy, które zapewnia punkt wejścia dla kodu. Te klasy oferują również dostępu do modelu obiektu aplikacji hosta oraz dostęp do funkcji, takich jak okienka akcji i niestandardowych okienek zadań.

### <a name="understand-the-generated-classes"></a>Zrozumienie wygenerowanych klas
 W projektach na poziomie dokumentu dla programów Excel i Word wygenerowana klasa przypomina obiekt najwyższego poziomu w modelu obiektu aplikacji. Na przykład wygenerowanego `ThisDocument` klasy w projekcie dokumentu programu Word zawiera te same elementy członkowskie jako <xref:Microsoft.Office.Interop.Word.Document> klasy w modelu obiektów programu Word. Aby uzyskać więcej informacji na temat wygenerowanych klas w projektach na poziomie dokumentu, zobacz [Program dostosowań poziomu dokumentu](../vsto/programming-document-level-customizations.md).

 Projekty dodatków narzędzi VSTO dla programów zapewniają wygenerowanej klasy o nazwie `ThisAddIn`. Ta klasa wygląda inaczej niż klasa w modelu obiektów aplikacji hosta. Zamiast tego należy ta klasa reprezentuje dodatku narzędzi VSTO sam i udostępnia elementy członkowskie, które umożliwia dostęp do modelu obiektów w aplikacji hosta i dostęp do innych funkcji, które są dostępne dla dodatków narzędzi VSTO. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).

 Obejmują wszystkie wygenerowanych klas w projektach pakietu Office `Startup` i `Shutdown` procedury obsługi zdarzeń. Aby rozpocząć pisanie kodu, zazwyczaj Dodaj kod do tych programów obsługi zdarzeń. Aby zainicjować dodatku narzędzi VSTO dla programów, możesz dodać kod do `Startup` programu obsługi zdarzeń. Aby wyczyścić zasoby używane przez dodatku narzędzi VSTO dla programów, należy dodać kod, aby `Shutdown` programu obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="access-the-generated-classes-at-runtime"></a>Dostęp do wygenerowanych klas w czasie wykonywania
 Po załadowaniu rozwiązania do pakietu Office, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] tworzy wygenerowanych klas w projekcie. Dostępne obiekty z dowolnego kodu w projekcie za pomocą `Globals` klasy. Na przykład, można użyć `Globals` klasy w celu wywołania kodu w `ThisAddIn` klasy z programu obsługi zdarzeń przycisk na Wstążce w dodatku VSTO.

 Aby uzyskać więcej informacji, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="namespace-considerations-in-office-solutions"></a>Namespace zagadnienia w rozwiązaniach pakietu Office
 Nie można zmienić *domyślny obszar nazw* (lub *głównej przestrzeni nazw* w języku Visual Basic) z projektu pakietu Office, po utworzeniu projektu. Domyślna przestrzeń nazw będzie zawsze zgodna Nazwa projektu, które zostały określone podczas tworzenia projektu. W przypadku zmiany nazwy projektu, nie powoduje zmiany domyślnej przestrzeni nazw. Aby uzyskać więcej informacji na temat domyślny obszar nazw w projektach, zobacz [strona aplikacji, Projektant projektu &#40;C&#35; &#41; ](../ide/reference/application-page-project-designer-csharp.md) i [strona aplikacji, Projektant projektu &#40;języka Visual Basic&#41; ](../ide/reference/application-page-project-designer-visual-basic.md).

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>Zmienianie przestrzeni nazw klas elementów hosta w projektach C#
 Hostowanie klas pozycji (na przykład `ThisAddIn`, `ThisWorkbook`, lub `ThisDocument` klasy) mają własne przestrzenie nazw w projektach Visual C# pakietu Office. Domyślnie przestrzeń nazw dla elementów hosta w projekcie, jest zgodna z nazwą projektu, określone podczas tworzenia projektu.

 Aby zmienić nazw elementów hosta w projekcie Visual C# pakietu Office, należy użyć **Namespace dla elementu hosta** właściwości. Aby uzyskać więcej informacji, zobacz [właściwości w projektach pakietu Office](../vsto/properties-in-office-projects.md).

## <a name="supported-programming-languages-in-office-projects"></a>Obsługiwane języki programowania w projektach pakietu Office
 Szablony projektów pakietu Office w programie Visual Studio obsługuje tylko Visual Basic i Visual C# języków programowania. Dlatego te szablony projektów są dostępne tylko w ramach **języka Visual Basic** i **Visual C#** węzłów **nowy projekt** okno dialogowe w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

## <a name="language-choice-and-office-programming"></a>Wybór języka i programowaniu pakietu Office
 Microsoft Office i programu Visual Basic for Applications (VBA) zostały zaprojektowane w celu współpracują ze sobą w celu zoptymalizowania przepływu pracy dostosowywania aplikacji. Visual Basic odziedziczył niektóre z tych wydarzeń. Na przykład Visual Basic obsługuje opcjonalnych parametrów, co oznacza, że piszesz mniejszej ilości kodu podczas wywoływania niektóre metody w Microsoft Office podstawowe zestawy międzyoperacyjne niż w przypadku użycia programu Visual C#.

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Program za pomocą programu vs w języku Visual Basic. Visual C# w rozwiązaniach pakietu Office
 Rozwiązania dla pakietu Office można utworzyć za pomocą języka Visual Basic lub Visual C#. Ponieważ modele obiektów Microsoft Office zostały zaprojektowane do użycia przy użyciu programu Microsoft Visual Basic for Applications (VBA), deweloperów programu Visual Basic można pracować wygodnie obiekty udostępniane przez aplikacje pakietu Microsoft Office. Visual C# deweloperzy mogą korzystać z większości te same funkcje, deweloperów programu Visual Basic, ale istnieją przypadki, gdzie należy napisać dodatkowy kod w celu użycia modele obiektów pakietu Office. Istnieją pewne różnice między podstawowe funkcje programowania, w rozwój pakietu Office i zarządzanego kodu napisanego w języku Visual Basic i C#.

## <a name="key-differences-between-visual-basic-and-visual-c"></a>Podstawowe różnice między języka Visual Basic i Visual C#
 Poniższej tabeli przedstawiono podstawowe różnice między języka Visual Basic i Visual C# w rozwój pakietu Office.

|Funkcja|Opis|Obsługa języka Visual Basic|Obsługa Visual C#|
|-------------|-----------------|--------------------------|------------------------|
|Następujące parametry opcjonalne|Wiele metod programu Microsoft Office ma parametry, które nie są wymagane w przypadku wywołania metody. Jeśli nie przekazano żadnej wartości dla parametru, wartość domyślna jest używana.|Visual Basic obsługuje następujące parametry opcjonalne.|Visual C# obsługuje następujące parametry opcjonalne w większości przypadków. Aby uzyskać więcej informacji, zobacz [parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).|
|Przekazywanie parametrów przez odwołanie|Parametry opcjonalne w większości podstawowych zestawów międzyoperacyjnych programu Microsoft Office może być przekazywany przez wartość. Jednak w niektórych podstawowych zestawów międzyoperacyjnych parametry opcjonalne, które akceptują typów referencyjnych muszą być przekazywane przez odwołanie.<br /><br /> Aby uzyskać więcej informacji na temat parametrów typu wartości i odwołań, zobacz [przekazywanie argumentów według wartości i według odwołania &#40;języka Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (dla języka Visual Basic) i [parametry są przekazywane &#40;C&#35; Podręcznik programowania&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Żadne dodatkowe czynności, konieczne są parametry są przekazywane przez odwołanie. Kompilator Visual Basic automatycznie przekazuje parametry przez odwołanie, gdy jest to konieczne.|W większości przypadków kompilator Visual C# automatycznie przekazuje parametry przez odwołanie, gdy jest to konieczne. Aby uzyskać więcej informacji, zobacz [parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md).|
|Właściwości sparametryzowane|Niektóre właściwości akceptują parametry i pełnią funkcje tylko do odczytu.|Visual Basic obsługuje właściwości, które akceptują parametry.|Visual C# obsługuje właściwości, które akceptują parametry.|
|Późne powiązania|Późne wiązanie obejmuje określenie właściwości obiektów w czasie wykonywania, zamiast zmiennych Rzutowanie na typ object w czasie projektowania.|Visual Basic wykonuje późne wiązanie podczas **Option Strict** jest wyłączona. Gdy **Option Strict** jest włączona, jawnie przekonwertuj obiektów i typy użycia w <xref:System.Reflection> przestrzeni nazw na dostęp do elementów członkowskich z późnym wiązaniem. Aby uzyskać więcej informacji, zobacz [późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).|Visual C# wykonuje późne powiązania w projektach przeznaczonych [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Aby uzyskać więcej informacji, zobacz [późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md).|

## <a name="key-differences-between-office-development-and-managed-code"></a>Podstawowe różnice między rozwoju pakietu Office i kodu zarządzanego
 Poniższej tabeli przedstawiono podstawowe różnice między środowiskiem deweloperskim pakietu Office i zarządzanego kodu napisanego w języku Visual Basic lub Visual C#.

|Funkcja|Opis|Obsługa języka Visual Basic i Visual C#|
|-------------|-----------------|-----------------------------------------|
|Indeksy tablicy|Dolnej granicy tablicy kolekcje aplikacji pakietu Microsoft Office rozpoczyna się od 1. Visual Basic i Visual C# należy używać tablic oparty na 0. Aby uzyskać więcej informacji, zobacz [tablic &#40;C&#35; Podręcznik programowania&#41; ](/dotnet/csharp/programming-guide/arrays/index) i [tablice w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Aby uzyskać dostęp do pierwszego elementu w kolekcji w modelu obiektów aplikacji Microsoft Office, zamiast indeks 1 na 0.|

## <a name="see-also"></a>Zobacz także

- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md)
- [Instrukcje: Konfigurowanie pod kątem aplikacji pakietu Office przy użyciu podstawowych zestawów międzyoperacyjnych](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Instrukcje: Tworzenie obsługi zdarzeń w projektach pakietu Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)
- [Programowanie zespołowe rozwiązań pakietu Office](../vsto/collaborative-development-of-office-solutions.md)
