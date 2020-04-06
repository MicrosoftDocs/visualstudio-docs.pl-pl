---
title: Wewnątrz sdk programu Visual Studio | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e72020795bc3181e11f0f90eff580a2365d4000
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707577"
---
# <a name="inside-the-visual-studio-sdk"></a>Wewnątrz zestawu Visual Studio SDK

Ta sekcja zawiera szczegółowe informacje na temat rozszerzeń programu Visual Studio, w tym architektury programu Visual Studio, składniki, usługi, schematy, narzędzia i tym podobne.

## <a name="extensibility-architecture"></a>Architektura rozszerzalności
 Na poniższej ilustracji przedstawiono architekturę rozszerzalności programu Visual Studio. VsPackages zapewniają funkcje aplikacji, która jest współużytkowana przez IDE jako usługi. Standardowy IDE oferuje również szeroki zakres <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>usług, takich jak , które zapewniają dostęp do funkcji okien IDE.

 ![Grafika przedstawiająca architekturę środowiska](../../extensibility/internals/media/environment.gif "environment") Uogólniony widok architektury programu Visual Studio

## <a name="vspackages"></a>Pakiety VSPackage
 VSPackages to moduły oprogramowania, które tworzą i rozszerzają program Visual Studio za pomocą elementów interfejsu użytkownika, usług, projektów, edytorów i projektantów. VSPackages są centralną jednostką architektoniczną programu Visual Studio. Aby uzyskać więcej informacji, zobacz [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Powłoka programu Visual Studio zapewnia podstawowe funkcje i obsługuje komunikację krzyżową między jego składnikami VSPackages i rozszerzeniami MEF. Aby uzyskać więcej informacji, zobacz [Powłoka programu Visual Studio](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Wskazówki dotyczące interfejsu użytkownika
 Jeśli planujesz zaprojektować nowe funkcje dla programu Visual Studio, należy zapoznać się z tymi wskazówkami dotyczącymi projektowania i użyteczności: [Wskazówki dotyczące środowiska użytkownika programu Visual Studio.](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="commands"></a>Polecenia
 Polecenia to funkcje, które realizują zadania, takie jak drukowanie dokumentu, odświeżanie widoku lub tworzenie nowego pliku.

 Podczas rozszerzania programu Visual Studio można tworzyć polecenia i rejestrować je w powłoce programu Visual Studio. Można określić, jak te polecenia będą wyświetlane w IDE, na przykład w menu lub na pasku narzędzi. Zazwyczaj w menu **Narzędzia** pojawia się polecenie niestandardowe, a w podmenu **Inne menu** **Widok** pojawi się polecenie wyświetlania okna narzędzia.

 Podczas tworzenia polecenia, należy również utworzyć program obsługi zdarzeń dla niego. Program obsługi zdarzeń określa, kiedy polecenie jest widoczne lub włączone, umożliwia modyfikowanie jego tekstu i gwarantuje, że polecenie reaguje odpowiednio po jego aktywacji. W większości przypadków IDE obsługuje polecenia przy <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> użyciu interfejsu. Polecenia w programie Visual Studio są obsługiwane, począwszy od kontekstu polecenia najbardziej wewnętrznego, na podstawie lokalnego zaznaczenia i przechodząc do kontekstu zewnętrznego, na podstawie wyboru globalnego. Polecenia dodane do menu głównego są natychmiast dostępne do skryptów.

 Aby uzyskać więcej informacji, zobacz [Polecenia, Menu i Paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menu i paski narzędzi
 Menu i paski narzędzi umożliwiają użytkownikom wywoływanie poleceń. Menu to wiersze lub kolumny poleceń, które zazwyczaj są wyświetlane jako pojedyncze elementy tekstowe u góry okna narzędzia. Podmenu są menu pomocnicze, które pojawiają się, gdy użytkownik kliknie polecenia, które zawierają małą strzałkę. Menu kontekstowe są wyświetlane, gdy użytkownik klika prawym przyciskiem myszy niektóre elementy interfejsu użytkownika. Niektóre typowe nazwy menu **to Plik,** **Edycja,** **Widok**i **Okno**. Aby uzyskać więcej informacji, zobacz [Rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

 Paski narzędzi to wiersze lub kolumny przycisków i innych formantów, takich jak pola kombi, pola listy i pola tekstowe. Przyciski paska narzędzi zazwyczaj mają obrazy ikon, takie jak ikona folderu dla polecenia **Otwórz plik** lub drukarka polecenia **Drukuj.** Wszystkie elementy paska narzędzi są skojarzone z poleceniami. Po kliknięciu przycisku paska narzędzi zostanie ono uruchamiane. W przypadku formantu rozwijanego każdy element na liście rozwijanej jest skojarzony z innym poleceniem. Niektóre kontrolki paska narzędzi, takie jak formant rozdzielacza, są hybrydami. Jedna strona formantu jest przyciskiem paska narzędzi, a druga jest strzałką w dół, która wyświetla kilka poleceń po kliknięciu.

## <a name="tool-windows"></a>Narzędzie Windows
 Okna narzędzi są używane w IDE do wyświetlania informacji. **Przybornik**, **Eksplorator rozwiązań**, Okno **Właściwości** i **Przeglądarka sieci Web** są przykładami okien narzędzi.

 Okna narzędzi zazwyczaj oferują różne kontrolki, z którymi użytkownik może wchodzić w interakcje. Na przykład **właściwości** okna umożliwia użytkownikowi ustawić właściwości obiektów, które służą określonego celu. Okno **Właściwości** specjalizuje się w tym sensie, ale również ogólne, ponieważ może być używany w wielu różnych sytuacjach. Podobnie okno **Dane wyjściowe** jest wyspecjalizowane, ponieważ zapewnia dane wyjściowe oparte na tekście, ale ogólne, ponieważ wiele podsystemów w programie Visual Studio można go używać do dostarczania danych wyjściowych dla użytkownika programu Visual Studio.

 Należy wziąć pod uwagę następujący obraz programu Visual Studio, który zawiera kilka okien narzędzi:

 ![Zrzut ekranu](../../extensibility/internals/media/t1gui.png "T1gui ( T1gui )")

 Niektóre okna narzędzi są zadokowane razem w jednym okienku, w które wyświetla okno narzędzia Eksploratora rozwiązań i ukrywa inne okna narzędzi, ale udostępnia je, klikając karty. Obraz przedstawia dwa inne okna narzędzi, **listę błędów** i okno **Dane wyjściowe,** zadokowane razem w jednym okienku.

 Pokazano również główne okienko dokumentu, w którym znajduje się kilka okien edytora. Chociaż okna narzędzi zazwyczaj mają tylko jedno wystąpienie (na przykład można otworzyć tylko jedno **Eksploratora rozwiązań),** edytor windows może mieć wiele wystąpień, z których każdy jest używany do edycji oddzielnego dokumentu, ale wszystkie z nich są zadokowane w tym samym okienku. Obraz przedstawia okienko dokumentu, które ma dwa okna edytora, jedno okno projektanta formularzy. Wszystkie okna w okienku dokumentu są dostępne po kliknięciu kart, ale okno edytora zawierające EditorPane.cs plik jest widoczne i aktywne.

 Podczas rozszerzania programu Visual Studio można utworzyć okna narzędzi, które umożliwiają użytkownikom programu Visual Studio interakcję z rozszerzeniem. Można również utworzyć własne edytory, które umożliwiają użytkownikom programu Visual Studio edytowanie dokumentów. Ponieważ okna narzędzi i edytory zostaną zintegrowane z programem Visual Studio, nie trzeba programować ich dokowania lub pojawiać się na karcie poprawnie. Gdy są poprawnie zarejestrowane w programie Visual Studio, będą automatycznie miały typowe funkcje okien narzędzi i okien dokumentów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [Rozszerzanie i dostosowywanie narzędzia Windows](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Okna dokumentów
 Okno dokumentu jest oknom podrzędnym w ramce okna interfejsu wielu dokumentów (MDI). Okna dokumentów są zazwyczaj używane do hostowania edytorów tekstu, edytorów formularzy (nazywanych również projektantami) lub formantów edycji, ale mogą również obsługiwać inne typy funkcjonalne. Okno dialogowe **Nowy plik** zawiera przykłady okien dokumentów udostępnianych przez program Visual Studio.

 Większość edytorów jest specyficzna dla języka programowania lub typu pliku, takiego jak strony HTML, zestawy ramek, pliki języka C++ lub pliki nagłówkowe. Wybierając szablon w oknie dialogowym **Nowy plik,** użytkownik dynamicznie tworzy okno dokumentu dla edytora dla typu pliku skojarzonego z szablonem. Okno dokumentu jest również tworzone, gdy użytkownik otwiera istniejący plik.

 Okna dokumentów są ograniczone do obszaru klienta MDI. Każde okno dokumentu ma kartę u góry, a kolejność tabulatorów jest połączona z innymi oknami, które mogą być otwarte w obszarze MDI. Kliknięcie prawym przyciskiem myszy karty okna dokumentu powoduje wyświetlenie menu skrótów zawierającego opcje podziału obszaru MDI na wiele grup kart poziomych lub pionowych. Dzielenie obszaru MDI umożliwia wyświetlanie wielu plików w tym samym czasie. Aby uzyskać więcej informacji, zobacz [Dokument systemu Windows](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Edytory
 Edytor programu Visual Studio umożliwia dostosowanie go i używać go do własnego typu zawartości za pomocą managed extensibility framework (MEF). W wielu przypadkach nie trzeba będzie utworzyć VSPackage rozszerzyć edytora, chociaż jeśli chcesz dołączyć funkcje z powłoki (na przykład polecenie menu lub klawisz skrótu), można połączyć rozszerzenie MEF z VSPackage.

 Można również utworzyć edytor niestandardowy, na przykład, jeśli chcesz czytać i pisać w bazie danych lub jeśli chcesz użyć projektanta. Można również użyć zewnętrznego edytora, takiego jak Notatnik lub Microsoft WordPad. Aby uzyskać więcej informacji, zobacz [Edytor i rozszerzenia usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Usługi językowe
 Jeśli chcesz, aby edytor programu Visual Studio obsługiwał nowe słowa kluczowe programowania lub nawet nowy język programowania, utwórz usługę języka. Każda usługa językowa może implementować niektóre funkcje edytora w pełni, częściowo lub wcale. W zależności od sposobu skonfigurowania usługa języka może zapewnić podświetlanie składni, dopasowywanie nawiasów klamrowych, obsługę intellisense i inne funkcje w edytorze.

 Sercem usługi językowej są analizator i skaner. Skaner (lub lexer) dzieli plik źródłowy na elementy, które są znane jako tokeny, a analizator ustanawia relacje między tymi tokenami. Podczas tworzenia usługi języka, należy zaimplementować analizatora i skanera, aby visual studio może zrozumieć tokeny i gramatyki języka. Można tworzyć usługi języka zarządzanego lub niezarządzanego. Aby uzyskać więcej informacji, zobacz [Rozszerzalność usługi legacy language service](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projekty

W programie Visual Studio projekty są kontenerami używanymi przez deweloperów do organizowania i tworzenia kodu źródłowego i innych zasobów. Projekty umożliwiają organizowanie, tworzenie, debugowanie i wdrażanie kodu źródłowego, odwołania do usług sieci Web i baz danych oraz innych zasobów. Pakiety VSPackages można rozszerzyć system projektu Visual Studio, zapewniając typy projektów, podtypy projektu i narzędzia niestandardowe.

Projekty mogą być również zebrane razem w *rozwiązaniu,* które jest grupowanie jednego lub więcej projektów, które współpracują ze sobą w celu utworzenia aplikacji. Informacje o projekcie i stanie, które odnoszą się do rozwiązania, są przechowywane w dwóch plikach rozwiązania, pliku rozwiązania tekstowego [(.sln)](solution-dot-sln-file.md) i [pliku opcji użytkownika rozwiązania binarnego (.suo).](solution-user-options-dot-suo-file.md) Pliki te są podobne do plików grupy (.vbg), które były używane we wcześniejszych wersjach języka Visual Basic, oraz plików o obszarze roboczym (dsw) i opcjach użytkownika (.opt), które były używane we wcześniejszych wersjach języka C++.

Aby uzyskać więcej informacji, zobacz [Projekty](../../extensibility/internals/projects.md) i [rozwiązania](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Szablony projektów i elementów
 Program Visual Studio zawiera wstępnie zdefiniowane szablony projektów i szablony elementów projektu. Można również tworzyć własne szablony lub uzyskać szablony od społeczności, a następnie zintegrować je z programem Visual Studio. [Galeria kodów MSDN](https://code.msdn.microsoft.com/site/search?query=visual%20studio) to miejsce, w które można wybrać szablony i rozszerzenia.

 Szablony zawierają strukturę projektu i podstawowe pliki, które są wymagane do utworzenia określonego rodzaju aplikacji, kontroli, biblioteki lub klasy. Jeśli chcesz opracować oprogramowanie, które przypomina jeden z szablonów, utwórz projekt, który jest oparty na szablonie, a następnie zmodyfikuj pliki w tym projekcie.

> [!NOTE]
> Ta architektura szablonu [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] nie jest obsługiwana dla projektów.

 Aby uzyskać więcej informacji, zobacz [Dodawanie szablonów elementów projektu i projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Właściwości i opcje
 Okno **Właściwości** wyświetla właściwości pojedynczych lub wielu zaznaczonych elementów: [Rozszerzanie](../../extensibility/internals/extending-properties.md) opcji właściwości strony zawierają zestawy opcji, które odnoszą się do określonego składnika, takich jak język programowania lub VSPackage: [Opcje i Opcje Strony](../../extensibility/internals/options-and-options-pages.md). Ustawienia są zazwyczaj funkcjami związanymi z interfejsem użytkownika, które można zaimportować i wyeksportować: [Obsługa ustawień użytkownika](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Usługi programu Visual Studio
 Usługa udostępnia określony zestaw interfejsów dla składników do wykorzystania. Visual Studio udostępnia zestaw usług, które mogą być używane przez wszystkie składniki, w tym rozszerzenia. Na przykład usługi Visual Studio włączyć okna narzędzi, które mają być wyświetlane lub ukryte dynamicznie, włączyć dostęp do Pomocy, pasek stanu lub zdarzenia interfejsu użytkownika. Edytor programu Visual Studio udostępnia również usługi, które mogą być importowane przez rozszerzenia edytora. Aby uzyskać więcej informacji, zobacz [Korzystanie z usług i świadczenie usług](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Debuger
 Debuger jest interfejsem użytkownika do składników debugowania specyficzne dla języka. Jeśli utworzono nową usługę języka, należy utworzyć aparat debugowania określonego do podłączenia do debugera. Aby uzyskać więcej informacji, zobacz [Rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Kontrola źródła
 Aby uzyskać informacje na temat implementowania wtyczki kontroli źródła lub vspackage, zobacz [Formant źródła](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Kreatory
 Kreatora można utworzyć w połączeniu z nowym typem projektu, aby kreator mógł pomóc użytkownikom w podejmowaniu właściwych decyzji podczas tworzenia nowego projektu tego typu. Aby uzyskać więcej informacji, zobacz [Wizards](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Narzędzia niestandardowe
 Narzędzia niestandardowe umożliwiają skojarzenie narzędzia z elementem w projekcie i uruchomienie tego narzędzia za każdym razem, gdy plik jest zapisywany. Aby uzyskać więcej informacji, zobacz [Narzędzia niestandardowe](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Narzędzia VSSDK
 VSSDK zawiera zestaw narzędzi, które mogą być potrzebne do pracy z różnymi aspektami VSPackages. Aby uzyskać więcej informacji, zobacz [narzędzia vssdk](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Korzystanie z Instalatora Windows
 W niektórych przypadkach może być konieczne użycie Instalatora Windows, a nie instalatora VSIX: na przykład może być konieczne zapisanie w rejestrze. Aby uzyskać informacje dotyczące korzystania z Instalatora Windows z rozszerzeniami, zobacz [Instalowanie pakietów VSPackages z Instalatorem Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Podgląd pomocy
 Możesz zintegrować własne strony pomocy i F1 z Podglądem pomocy. Aby uzyskać więcej informacji, zobacz [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
