---
title: W zestawie SDK programu Visual Studio | Microsoft Docs
description: Poznaj rozszerzenia zestawu SDK programu Visual Studio, w tym architekturę, składniki, usługi, schematy i narzędzia programu Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 73bbb1beb30677711b8b517262b48465e7529585
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205336"
---
# <a name="inside-the-visual-studio-sdk"></a>Wewnątrz zestawu Visual Studio SDK

Ta sekcja zawiera szczegółowe informacje na temat rozszerzeń programu Visual Studio, w tym architekturę programu Visual Studio, składniki, usługi, schematy, narzędzia i podobne.

## <a name="extensibility-architecture"></a>Architektura rozszerzalności
 Na poniższej ilustracji przedstawiono architekturę rozszerzalności programu Visual Studio. Pakietów VSPackage udostępniaj funkcje aplikacji, które są współużytkowane przez środowisko IDE jako usługi. Standardowe środowisko IDE oferuje także szeroką gamę usług, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , które zapewniają dostęp do funkcji okna IDE.

 ![Grafika architektury środowiska](../../extensibility/internals/media/environment.gif "środowisko") Widok uogólniony architektury programu Visual Studio

## <a name="vspackages"></a>Pakiety VSPackage
 Pakietów VSPackage to moduły oprogramowania, które tworzą i zwiększają program Visual Studio z elementami interfejsu użytkownika, usługami, projektami, edytorami i projektantami. Pakietów VSPackage jest centralną jednostką architektoniczną programu Visual Studio. Aby uzyskać więcej informacji, zobacz [pakietów VSPackage](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Powłoka programu Visual Studio zapewnia podstawowe funkcje i obsługuje komunikację między składnikami pakietów VSPackage i MEF. Aby uzyskać więcej informacji, zobacz [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Wskazówki dotyczące interfejsu użytkownika
 Jeśli planujesz projektowanie nowych funkcji dla programu Visual Studio, zapoznaj się z tymi wskazówkami dotyczącymi projektowania i porad dotyczących użyteczności: [wskazówki dotyczące środowiska użytkownika programu Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Polecenia
 Polecenia to funkcje wykonujące zadania, takie jak drukowanie dokumentu, odświeżanie widoku lub tworzenie nowego pliku.

 Rozszerzając program Visual Studio, można tworzyć polecenia i rejestrować je za pomocą powłoki programu Visual Studio. Możesz określić, jak te polecenia będą wyświetlane w środowisku IDE, na przykład w menu lub pasku narzędzi. Zwykle polecenie niestandardowe pojawia się w menu **Narzędzia** , a polecenie wyświetlania okna narzędzi pojawi się w innym podmenu **okna** menu **Widok** .

 Podczas tworzenia polecenia należy również utworzyć procedurę obsługi zdarzeń. Program obsługi zdarzeń określa, kiedy polecenie jest widoczne lub włączone, umożliwia zmodyfikowanie tekstu i gwarantuje, że polecenie reaguje odpowiednio po jego aktywowaniu. W większości wystąpień IDE obsługuje polecenia za pomocą <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Polecenia w programie Visual Studio są obsługiwane, zaczynając od wewnętrznego kontekstu poleceń, na podstawie wyboru lokalnego i przechodząc do zewnętrznego kontekstu, na podstawie zaznaczenia globalnego. Polecenia dodane do menu głównego są natychmiast dostępne dla skryptów.

 Aby uzyskać więcej informacji, zobacz [polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menu i paski narzędzi
 Menu i paski narzędzi umożliwiają użytkownikom Wywoływanie poleceń. Menu są wierszami lub kolumnami poleceń, które są zwykle wyświetlane jako pojedyncze elementy tekstowe w górnej części okna narzędzi. Podmenu są menu pomocnicze, które są wyświetlane, gdy użytkownik kliknie polecenia, które zawierają małą strzałkę. Menu kontekstowe pojawiają się, gdy użytkownik kliknie prawym przyciskiem myszy niektóre elementy interfejsu użytkownika. Niektóre typowe nazwy menu to **plik**, **Edycja**, **Widok** i **okno**. Aby uzyskać więcej informacji, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

 Paski narzędzi to wiersze lub kolumny przycisków oraz inne kontrolki, takie jak pola kombi, pola listy i pola tekstowe. Przyciski paska narzędzi zwykle mają obrazy ikon, takie jak ikona folderu dla polecenia **Otwórz plik** lub drukarka dla polecenia **Print** . Wszystkie elementy paska narzędzi są skojarzone z poleceniami. Po kliknięciu przycisku paska narzędzi zostanie uruchomione jego skojarzone polecenie. W przypadku kontrolki rozwijanej każdy element na liście rozwijanej jest skojarzony z innym poleceniem. Niektóre kontrolki paska narzędzi, takie jak kontrolka rozdzielacza, są hybrydowe. Jedna strona kontrolki jest przyciskiem paska narzędzi, a druga strona jest strzałką w dół, która wyświetla kilka poleceń po kliknięciu.

## <a name="tool-windows"></a>Okna narzędzi
 Okna narzędzi są używane w środowisku IDE do wyświetlania informacji. **Przybornik**, **Eksplorator rozwiązań**, okno **Właściwości** i **przeglądarka sieci Web** są przykładami okien narzędzi.

 Okna narzędzi zazwyczaj oferują różne kontrolki, z którymi użytkownik może korzystać. Na przykład okno **Właściwości** umożliwia użytkownikowi ustawianie właściwości obiektów, które obsługują określony cel. Okno **Właściwości** jest wyspecjalizowane w tym sensie, ale również ogólne, ponieważ może być używane w wielu różnych sytuacjach. Analogicznie, okno **danych wyjściowych** jest wyspecjalizowane, ponieważ zawiera dane wyjściowe na podstawie tekstu, ale ogólne, ponieważ wiele podsystemów w programie Visual Studio może używać go do dostarczania danych wyjściowych do użytkownika programu Visual Studio.

 Rozważmy następujący obraz programu Visual Studio, który zawiera kilka okien narzędzi:

 ![Zrzut ekranu](../../extensibility/internals/media/t1gui.png "T1gui")

 Niektóre okna narzędzi są zadokowane w jednym okienku, które wyświetla okno narzędzia Eksplorator rozwiązań i ukrywa inne okna narzędzi, ale udostępnia je przez klikanie kart. Obraz przedstawia dwa inne okna narzędzi, **Lista błędów** i **dane wyjściowe** , zadokowane razem w jednym okienku.

 Jest również pokazywany panel dokumentu głównego, który pokazuje kilka okien edytora. Chociaż system Windows ma zwykle tylko jedno wystąpienie (na przykład można otworzyć tylko jeden **Eksplorator rozwiązań**), okna edytora mogą mieć wiele wystąpień, z których każdy jest używany do edytowania oddzielnego dokumentu, ale wszystkie są zadokowane w tym samym okienku. Obraz pokazuje okienko dokumentu, które ma dwa okna edytora, jedno okno projektanta formularzy. Wszystkie okna w okienku dokumentu są dostępne po kliknięciu pozycji karty, ale okno edytora zawierające plik EditorPane.cs jest widoczny i aktywny.

 Po rozszerzeniu programu Visual Studio można utworzyć okna narzędzi, które umożliwiają użytkownikom programu Visual Studio współpracujące z Twoim rozszerzeniem. Można również tworzyć własne edytory, które umożliwiają użytkownikom programu Visual Studio edytowanie dokumentów. Ponieważ okna narzędzi i edytory zostaną zintegrowane z programem Visual Studio, nie ma potrzeby poprawnego programowania lub wyświetlania na karcie. Po poprawnym zarejestrowaniu w programie Visual Studio będą automatycznie korzystać z typowych funkcji okien narzędzi i okien dokumentów w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [rozszerzanie i dostosowywanie okien narzędzi](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Okna dokumentów
 Okno dokumentu jest oknem podrzędnym z ramką okna interfejsu wielu dokumentów (MDI). Okna dokumentów są zwykle używane do hostowania edytorów tekstu, edytorów formularzy (nazywanych również projektantami) lub edytowania kontrolek, ale mogą również hostować inne typy funkcjonalne. Okno dialogowe **nowy plik** zawiera przykładowe okna dokumentów dostępne w programie Visual Studio.

 Większość edytorów jest specyficzna dla języka programowania lub do typu pliku, na przykład stron HTML, zestawów ramek, plików C++ lub plików nagłówkowych. Po wybraniu szablonu w oknie dialogowym **nowy plik** użytkownik tworzy dynamicznie okno dokumentu dla edytora dla typu pliku, który jest skojarzony z szablonem. Okno dokumentu jest również tworzone, gdy użytkownik otworzy istniejący plik.

 Okna dokumentów są ograniczone do obszaru klienckiego MDI. Każde okno dokumentu ma kartę u góry, a kolejność tabulacji jest połączona z innymi oknami, które mogą być otwarte w obszarze MDI. Kliknięcie prawym przyciskiem myszy karty okna dokumentu powoduje wyświetlenie menu skrótów zawierającego opcje podziału obszaru MDI na wiele grup kart w poziomie lub w pionie. Dzielenie obszaru MDI umożliwia przeglądanie wielu plików w tym samym czasie. Aby uzyskać więcej informacji, zobacz [dokument Windows](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Edytory
 Edytor programu Visual Studio umożliwia dostosowanie go i użycie go do własnego typu zawartości za pomocą Managed Extensibility Framework (MEF). W wielu przypadkach nie trzeba tworzyć pakietu VSPackage, aby rozszerzać Edytor, ale jeśli chcesz dołączyć funkcje z powłoki (na przykład polecenie menu lub klawisz skrótu), możesz połączyć rozszerzenie MEF z pakietu VSPackage.

 Możesz również utworzyć niestandardowy Edytor, na przykład jeśli chcesz odczytywać i zapisywać dane w bazie danych, lub jeśli chcesz użyć projektanta. Można również użyć zewnętrznego edytora, takiego jak Notepad lub Microsoft WordPad. Aby uzyskać więcej informacji, zobacz [edytory i rozszerzenia usługi językowej](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Usługi językowe
 Jeśli chcesz, aby Edytor programu Visual Studio obsługiwał nowe słowa kluczowe programowania, a nawet nowy język programowania, tworzysz usługę języka. Każda usługa języka może implementować niektóre funkcje edytora w całości, częściowo lub wcale. W zależności od sposobu jego konfiguracji usługa języka może zapewniać wyróżnianie składni, dopasowywanie w nawiasach klamrowych, obsługę technologii IntelliSense i inne funkcje w edytorze.

 Na serca usługi językowej są parserem i skanerem. Skaner (lub Analizator leksykalny) dzieli plik źródłowy na elementy, które są znane jako tokeny, a Analizator tworzy relacje między tymi tokenami. Podczas tworzenia usługi językowej należy zaimplementować parser i skaner, aby program Visual Studio mógł zrozumieć tokeny i gramatykę języka. Można tworzyć zarządzane lub niezarządzane usługi językowe. Aby uzyskać więcej informacji, zobacz [rozszerzenia starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projekty

W programie Visual Studio projekty są kontenerami używanymi przez deweloperów do organizowania i kompilowania kodu źródłowego i innych zasobów. Projekty umożliwiają organizowanie, kompilowanie, debugowanie i wdrażanie kodu źródłowego, odwołań do usług sieci Web i baz danych oraz innych zasobów. Pakietów VSPackage może zwiększyć system projektu programu Visual Studio, dostarczając typy projektu, podtypy projektu i narzędzia niestandardowe.

Projekty mogą być również zbierane w *rozwiązaniu*, które jest grupą co najmniej jednego projektu, który współpracują ze sobą w celu utworzenia aplikacji. Informacje o projekcie i stanie, które odnoszą się do rozwiązania, są przechowywane w dwóch plikach rozwiązań, [pliku rozwiązania tekstowego (. sln)](solution-dot-sln-file.md) i [pliku opcji użytkownika rozwiązania binarnego (. suo)](solution-user-options-dot-suo-file.md). Te pliki są podobne do plików grupy (VBG), które były używane we wcześniejszych wersjach Visual Basic, oraz plików obszaru roboczego (. DSW) i opcji użytkownika (. opt), które były używane we wcześniejszych wersjach języka C++.

Aby uzyskać więcej informacji, zobacz [projekty](../../extensibility/internals/projects.md) i [rozwiązania](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Szablony projektów i elementów
 Program Visual Studio zawiera wstępnie zdefiniowane szablony projektów i szablony elementów projektu. Możesz również utworzyć własne szablony lub pobrać szablony ze społeczności, a następnie zintegrować je w programie Visual Studio. [Galeria kodu MSDN](https://code.msdn.microsoft.com/site/search?query=visual%20studio) jest miejscem, w którym można przejść do szablonów i rozszerzeń.

 Szablony zawierają strukturę projektu i pliki podstawowe, które są wymagane do kompilowania określonego rodzaju aplikacji, kontroli, biblioteki lub klasy. Aby opracować Oprogramowanie podobne do jednego z szablonów, należy utworzyć projekt oparty na szablonie, a następnie zmodyfikować pliki w tym projekcie.

> [!NOTE]
> Ta Architektura szablonu nie jest obsługiwana w [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektach.

 Aby uzyskać więcej informacji, zobacz [Dodawanie projektów i szablonów elementów projektów](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Właściwości i opcje
 W oknie **Właściwości** są wyświetlane właściwości jednego lub wielu zaznaczonych elementów: [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md) Opcje strony zawierają zestawy opcji, które odnoszą się do określonego składnika, takich jak język programowania lub pakietu VSPackage: [Opcje i strony opcji](../../extensibility/internals/options-and-options-pages.md). Ustawienia są zazwyczaj funkcjami związanymi z interfejsem użytkownika, które można importować i eksportować: [Obsługa ustawień użytkownika](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Usługi Visual Studio
 Usługa udostępnia określony zestaw interfejsów do użycia przez składniki. Program Visual Studio udostępnia zestaw usług, które mogą być używane przez dowolne składniki, w tym rozszerzenia. Na przykład usługi Visual Studio umożliwiają dynamiczne wyświetlanie lub ukrywanie okien narzędzi, zapewnianie dostępu do pomocy, paska stanu lub zdarzeń interfejsu użytkownika. Edytor programu Visual Studio udostępnia również usługi, które mogą być importowane przez rozszerzenia edytora. Aby uzyskać więcej informacji, zobacz [Używanie i świadczenie usług](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Debuger
 Debuger jest interfejsem użytkownika dla składników debugowania specyficznych dla języka. Jeśli utworzono nową usługę językową, musisz utworzyć konkretny aparat debugowania, aby podłączyć go do debugera. Aby uzyskać więcej informacji, zobacz [rozszerzalność debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Kontrola źródła
 Aby uzyskać informacje na temat implementowania wtyczki lub pakietu VSPackage kontroli źródła, zobacz [Kontrola źródła](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Kreatory
 Można utworzyć kreatora w połączeniu z nowym typem projektu, aby Kreator mógł pomóc użytkownikom w podejmowaniu właściwych decyzji podczas tworzenia nowego projektu tego typu. Aby uzyskać więcej informacji, zobacz [kreatorzy](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Narzędzia niestandardowe
 Narzędzia niestandardowe umożliwiają skojarzenie narzędzia z elementem w projekcie i uruchamianie tego narzędzia za każdym razem, gdy plik zostanie zapisany. Aby uzyskać więcej informacji, zobacz [narzędzia niestandardowe](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Narzędzia VSSDK
 VSSDK zawiera zestaw narzędzi, które mogą być potrzebne do pracy z różnymi aspektami pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [VSSDK Utilities](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Używanie Instalator Windows
 W niektórych przypadkach może być konieczne użycie Instalator Windows zamiast Instalatora VSIX: na przykład może być konieczne zapisanie w rejestrze. Aby uzyskać informacje o korzystaniu z Instalator Windows z rozszerzeniami, zobacz [Instalowanie pakietów VSPackage z Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Podgląd pomocy
 Możesz zintegrować własną pomoc i F1 strony w podglądzie pomocy. Aby uzyskać więcej informacji, zobacz [Podgląd pomocy firmy Microsoft SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
