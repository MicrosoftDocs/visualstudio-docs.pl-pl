---
title: W programie Visual Studio SDK | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c386fb7f9fb57abccf7d7bc3c9cec900a65d883a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54978272"
---
# <a name="inside-the-visual-studio-sdk"></a>Wewnątrz zestawu Visual Studio SDK
Ta sekcja zawiera szczegółowe informacje na temat rozszerzenia programu Visual Studio, w tym architektury programu Visual Studio, składniki, usługi, schematów, narzędzia i podobne.

## <a name="extensibility-architecture"></a>Rozszerzalność architektury
 Na poniższej ilustracji przedstawiono architekturę rozszerzalności programu Visual Studio. Pakietów VSPackage udostępniają funkcjonalności aplikacji, który jest współużytkowany przez IDE jako usługi. Standardowe środowisko IDE również oferuje szeroki zakres usług, takich jak <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, które zapewniają dostęp do funkcji obsługi okien środowiska IDE.

 ![Grafika przedstawiająca architekturę środowiska](../../extensibility/internals/media/environment.gif "środowiska") uogólniony widok architektury programu Visual Studio

## <a name="vspackages"></a>Pakiety VSPackage
 Pakietów VSPackage są modułów oprogramowania, które tworzą i rozszerzanie programu Visual Studio przy użyciu elementów, usług, projekty, edytorów i projektantów interfejsu użytkownika. Pakietów VSPackage są jednostki centralnej architektury programu Visual Studio. Aby uzyskać więcej informacji, zobacz [pakietów VSPackage](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Visual Studio shell zapewnia podstawowe funkcje i obsługują cross komunikacji między jego rozszerzenia pakietów VSPackage i MEF składnika. Aby uzyskać więcej informacji, zobacz [programu Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Wskazówki dotyczące interfejsu użytkownika
 Jeśli planowane jest projektowania nowych funkcji programu Visual Studio, powinno zająć się wskazówek, aby uzyskać wskazówki dotyczące projektowania i użyteczność: [Wskazówki dotyczące interfejsu użytkownika programu Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Polecenia
 Polecenia są funkcje, które wykonywania zadań, takich jak drukowanie dokumentu, odświeżyć widok lub tworzenia nowego pliku.

 Podczas rozszerzania programu Visual Studio można tworzyć polecenia i zarejestrować ich przy użyciu powłoki programu Visual Studio. Można określić, jak te polecenia pojawi się w IDE, na przykład w menu lub paska narzędzi. Zazwyczaj polecenie niestandardowe pojawia się na **narzędzia** menu i polecenia do wyświetlania okna narzędzi, które było wyświetlane na **Windows inne** podmenu **widoku** menu.

 Podczas tworzenia polecenia, należy także utworzyć program obsługi zdarzeń dla niego. Program obsługi zdarzeń określa, kiedy polecenie jest widoczny, czy włączona, umożliwia modyfikowanie jego tekstu i gwarantuje, że polecenie odpowiednio reaguje po aktywowaniu. W większości przypadków środowiska IDE programu obsługi poleceń przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu. Polecenia w programie Visual Studio są obsługiwane, począwszy od najbardziej polecenia w kontekście, na podstawie wybranych lokalnych i kontynuowanie prowadzące kontekstu, w oparciu o wybór globalnego. Polecenia dodane do menu głównego są natychmiast dostępne dla skryptów.

 Aby uzyskać więcej informacji, zobacz [polecenia, menu i paski narzędzi](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menu i paski narzędzi
 Menu i pasków zadań umożliwiają użytkownikom wywoływanie polecenia. Menu są wiersze lub kolumny poleceń, które zwykle są wyświetlane jako elementy poszczególnych tekst u góry okna narzędzi. Podmenu są menu podrzędne, które są wyświetlane, gdy użytkownik kliknie poleceń zawierających małą strzałkę. Menu kontekstowe są wyświetlane, gdy użytkownik kliknie prawym przyciskiem myszy niektórych elementów interfejsu użytkownika. Niektóre typowe nazwy menu są **pliku**, **Edytuj**, **widoku**, i **okna**. Aby uzyskać więcej informacji, zobacz [rozszerzanie menu i poleceń](../../extensibility/extending-menus-and-commands.md).

 Paski narzędzi są wiersze lub kolumny przycisków i inne formanty, takie jak pola kombi, pola listy i pola tekstowe. Przyciski paska narzędzi zwykle mają obrazy ikon, takich jak ikona folderu **Otwórz plik** polecenia lub drukarki dla **drukowania** polecenia. Wszystkie elementy paska narzędzi są skojarzone z poleceniami. Po kliknięciu przycisku paska narzędzi, jego skojarzony polecenie zostanie uruchomione. W przypadku kontrolkę listy rozwijanej każdy element na liście rozwijanej jest skojarzony z innego polecenia. Niektóre formanty paska narzędzi, takich jak Splitter — formant, są hybrydy. Obok kontrolki jest przycisku paska narzędzi, a druga strona jest strzałkę w dół, która wyświetla kilka poleceń, po kliknięciu.

## <a name="tool-windows"></a>Narzędzie Windows
 Narzędzia systemu windows są używane w środowisku IDE do wyświetlania informacji. **Przybornik**, **Eksploratora rozwiązań**, **właściwości** oknie i **przeglądarki sieci Web** to przykłady okien narzędzi.

 Okna narzędzi oferują zazwyczaj różne formanty, z którymi użytkownik może wchodzić w interakcje. Na przykład **właściwości** okna zezwala użytkownikowi na ustawianie właściwości obiektów, które służą do określonego celu. **Właściwości** okno jest wyspecjalizowane w tym sensie, ale także ogólne, ponieważ mogą być używane w wielu różnych sytuacjach. Podobnie **dane wyjściowe** okna jest przeznaczone, ponieważ zawiera ono tekst wyjściowy w formacie, ale ogólne, ponieważ wiele podsystemów w programie Visual Studio służy do zapewnienia dane wyjściowe użytkownika programu Visual Studio.

 Należy wziąć pod uwagę następujące obrazu programu Visual Studio, który zawiera kilka okien narzędzi.

 ![Zrzut ekranu przedstawiający](../../extensibility/internals/media/t1gui.png "T1gui")

 Niektóre okna narzędzi są zadokowane razem jedną taflę, który wyświetla okna narzędzi w Eksploratorze rozwiązań i ukrywa innymi oknami narzędzi, ale udostępnia, klikając karty. Na ilustracji przedstawiono dwie innymi oknami narzędzi **lista błędów** i **dane wyjściowe** okno zadokowane w jednym okienku.

 Również wyświetlany jest okienko głównego dokumentu, które zawiera kilka okien edytora. Mimo że narzędzia windows mają zwykle tylko jedno wystąpienie (na przykład, można otworzyć tylko jeden **Eksploratora rozwiązań**), okna edytora może mieć wiele wystąpień, z których każdy jest używany do edytowania oddzielny dokument, ale które są zadokowane w okienko. Na rysunku przedstawiono panel dokumentu, który ma dwa okna edytora, jedno okno projektanta formularza i okna przeglądarki, który pokazuje strony początkowej. Wszystkie okna w panelu dokumentu są dostępne po kliknięciu karty, ale okno edytora, który zawiera plik EditorPane.cs jest widoczne i aktywne.

 Po rozszerzeniu programu Visual Studio można utworzyć narzędzie systemu windows, które pozwalają użytkownikom programu Visual Studio wchodzić w interakcje z rozszerzeniem. Można również utworzyć własne edytory, które pozwalają użytkownikom programu Visual Studio, edytowanie dokumentów. Ponieważ Twoje okien narzędzi i edytory zostanie zintegrowana z programu Visual Studio, nie masz program je, aby zadokować lub są prawidłowo wyświetlane na karcie. Są one poprawnie zarejestrowany w programie Visual Studio, zostanie automatycznie mają typowe funkcje okna narzędzi i okna dokumentu w programie Visual Studio. Aby uzyskać więcej informacji, zobacz [rozszerzanie i dostosowywanie narzędzi Windows](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Okna dokumentów
 Okno dokumentu jest oknem podrzędnym ramce okna interfejsu wielu dokumentów (MDI). Okna dokumentów są zazwyczaj używane do hostowania, edytory tekstu, edytory formularza (znany także jako projektantów) lub formantów edycji, ale może to również obsługiwać inne typy funkcjonalności. **Nowy plik** — okno dialogowe zawiera przykłady okien dokumentu, programu Visual Studio.

 Większość edytorów specyficznych języka programowania lub typ plików, np. strony HTML, ramek, pliki języka C++ lub plików nagłówkowych. Wybierając szablon w **nowy plik** okno dialogowe, użytkownik dynamicznie tworzy okno dokumentu edytora dla typu pliku, który jest skojarzony z szablonem. Okno dokumentu jest tworzona, gdy użytkownik otwiera istniejący plik.

 Okna dokumentów są ograniczone do obszaru klienta MDI. Każde okno dokumentu ma kartę w górnej części, a kolejność tabulacji jest połączony z innymi oknami, które można otworzyć w obszarze MDI. Kliknij prawym przyciskiem myszy na karcie okna dokumentu, wyświetla się menu skrótów, która obejmuje opcje do dzielenia obszaru MDI do wielu grup poziomej lub pionowej karcie. Dzielenie obszaru MDI umożliwia wielu plików do wyświetlenia w tym samym czasie. Aby uzyskać więcej informacji, zobacz [Windows dokumentu](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Edytory
 Edytor programu Visual Studio pozwala dostosować go i przy jego użyciu dla typu zawartości za pomocą Managed Extensibility Framework (MEF). W wielu przypadkach nie należy do utworzenia pakietu VSPackage w celu rozszerzenia edytora, jeśli chcesz uwzględnić funkcji z poziomu powłoki (na przykład polecenie menu lub klawisza skrótu), łącząc rozszerzenia MEF za pomocą pakietu VSPackage.

 Można również utworzyć niestandardowy edytor, na przykład, jeśli chcesz odczytu i zapisu do bazy danych lub jeśli chcesz użyć projektanta. Można również użyć zewnętrznego edytora, takiego jak Notatnik lub Microsoft WordPad. Aby uzyskać więcej informacji, zobacz [edytora i rozszerzenia usługi w języka](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Usługi języka
 Edytor programu Visual Studio, aby zapewnić obsługę nowych słów kluczowych programowania lub nawet nowy język programowania, można utworzyć usługi językowej. Każda usługa języka może wdrożyć niektóre funkcje edytora w pełni, częściowo lub w ogóle nie. W zależności od sposobu jego konfiguracji usługa językowa umożliwia wyróżnianie składni, parowanie nawiasów klamrowych, obsługę funkcji IntelliSense i inne funkcje w edytorze.

 W ramach usługi w języka są analizator i skaner. Skaner (lub analizator leksykalny) dzieli pliku źródłowego na elementy, które są znane jako tokenów i analizatorem ustanawia relacje tych tokenów. Podczas tworzenia usługi językowej musi implementować analizator i skaner tak, aby zrozumieć tokenów i gramatyki języka programu Visual Studio. Można utworzyć usługi zarządzane lub niezarządzane języka. Aby uzyskać więcej informacji, zobacz [rozszerzalność usługi w języka starsza wersja](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Projekty
 W programie Visual Studio projekty są kontenerami, używanych przez deweloperów do organizowania i kompilacji kodu źródłowego i innych zasobów. Projekty umożliwiają organizowanie, kompilowanie, debugowanie i wdróż kod źródłowy, odwołuje się do usługi sieci Web i baz danych i innych zasobów. Pakietów VSPackage można rozszerzyć system projektu programu Visual Studio, zapewniając typów projektów, podtypy projektów i narzędzi niestandardowych.

 Projekty mogą również zbierać do rozwiązania, która to grupa jeden lub więcej projektów, które współpracują ze sobą, aby utworzyć aplikację. Projektu i stan informacje, które odnoszą się do rozwiązania są przechowywane w dwa pliki rozwiązań, plik tekstowy rozwiązania (.sln) i plik opcji (suo) użytkownika binarne rozwiązania. Te pliki są podobne do pliki grupy (.vbg), które były używane w starszych wersjach [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], i obszar roboczy (.dsw) i opcje plików (.opt), które były używane w starszych wersjach [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

 Aby uzyskać więcej informacji, zobacz [projektów](../../extensibility/internals/projects.md) i [rozwiązania](../../extensibility/internals/solutions.md).

## <a name="project-and-item-templates"></a>Szablony projektów i elementów
 Program Visual Studio obejmuje szablony projektów wstępnie zdefiniowanych i szablonów elementów projektów. Można również tworzyć własne szablony lub pobrać szablony od społeczności i zintegrować je do programu Visual Studio. [Galerii kodu MSDN](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) jest miejscem, aby przejść do szablonów i rozszerzenia.

 Szablony zawierają struktury projektu i podstawowe pliki, które są wymagane do utworzenia określonego rodzaju aplikacji, kontrolki, biblioteki lub klas. Do tworzenia oprogramowania, podobny do jednego z szablonów, należy utworzyć projekt, który jest oparty na szablonie, a następnie zmodyfikować pliki, w tym projekcie.

> [!NOTE]
> Ta architektura szablonu nie jest obsługiwana dla [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektów.

 Aby uzyskać więcej informacji, zobacz [Dodawanie projektu i szablonów elementów projektów](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Właściwości i opcje
 **Właściwości** oknie zostaną wyświetlone właściwości jednego lub wielu wybranych elementów: [Rozszerzanie właściwości](../../extensibility/internals/extending-properties.md) strony opcje zawierają zestawy opcji, które odnoszą się do określonego składnika, takiego jak język programowania lub pakietu VSPackage: [Opcje i strony opcji](../../extensibility/internals/options-and-options-pages.md). Ustawienia są zwykle interfejsu użytkownika funkcjach, które mogą być importowane i wyeksportowane: [Obsługa ustawień użytkowników](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Visual Studio Services
 Usługa zawiera zbiór interfejsów składników z. Program Visual Studio udostępnia zestaw usług, które mogą być używane przez wszystkie składniki, włącznie z rozszerzeniami. Na przykład usługi Visual Studio umożliwiają okien narzędziowych, aby wyświetlony lub ukryty dynamicznie, Włącz dostęp do pomocy i pasek stanu, w tym także zdarzenia interfejsu użytkownika. Edytor programu Visual Studio udostępnia również usługi, które mogą być importowane przez rozszerzenia edytora. Aby uzyskać więcej informacji, zobacz [Using i dostarczanie usług](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Debuger
 Debuger jest interfejsem użytkownika ze składnikami debugowania specyficznych dla języka. Jeśli utworzono nową usługę językową, należy utworzyć aparatu debugowania określone podłączyć w do debugera. Aby uzyskać więcej informacji, zobacz [rozszerzeń debugera programu Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Kontrola źródła
 Aby uzyskać informacje o implementowaniu wtyczka do kontroli źródła lub pakietu VSPackage, zobacz [kontroli źródła](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Kreatory
 Można utworzyć kreatora w połączeniu z nowym typem projektu, tak, aby Kreator może pomóc użytkownikom podjęcie właściwych decyzji, podczas tworzenia nowego projektu tego typu. Aby uzyskać więcej informacji, zobacz [kreatorów](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Narzędzia niestandardowe
 Narzędzia niestandardowe umożliwiają kojarzenie narzędzie za pomocą elementu w projekcie i uruchomienia tego narzędzia, zawsze wtedy, gdy plik jest zapisywany. Aby uzyskać więcej informacji, zobacz [narzędzia niestandardowe](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Narzędzia VSSDK
 VSSDK obejmuje zestaw narzędzi, które mogą wymagać, aby pracować z różnych aspektów korzystania z pakietów VSPackage. Aby uzyskać więcej informacji, zobacz [narzędzia VSSDK](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Za pomocą Instalatora Windows
 W niektórych przypadkach może być konieczne użycie Instalatora Windows zamiast Instalator VSIX: na przykład, konieczne może być zapisu w rejestrze. Aby dowiedzieć się, jak za pomocą Instalatora Windows przy użyciu rozszerzeń, zobacz [instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Podgląd pomocy
 Możesz zintegrować swoje własne Pomoc i F1 strony podglądu pomocy. Aby uzyskać więcej informacji, zobacz [zestaw SDK podglądu pomocy firmy Microsoft](../../extensibility/internals/microsoft-help-viewer-sdk.md).