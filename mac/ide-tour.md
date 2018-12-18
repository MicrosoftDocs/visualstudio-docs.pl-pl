---
title: Program Visual Studio for Mac samouczek
description: Visual Studio dla komputerów Mac udostępnia zintegrowane środowisko projektowe umożliwiające tworzenie aplikacji .NET w systemie macOS, w tym witryny sieci Web platformy ASP.NET Core oraz projekty Xamarin dla systemu iOS, Android, Mac i zestawu narzędzi Xamarin.Forms.
zone_pivot_groups: mac-ide-version
author: conceptdev
ms.author: crdun
ms.date: 11/03/2018
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.openlocfilehash: e1787f6d396121263d91633a4ee6d4dd8ed2c35f
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2018
ms.locfileid: "52895798"
---
# <a name="visual-studio-for-mac-tour"></a>Program Visual Studio for Mac samouczek

Program Visual Studio for Mac ewoluuje skoncentrowane na telefon komórkowy środowiska IDE platformy Xamarin, Xamarin Studio w środowisko programistyczne stawiana jest mobilność i chmurę na komputerze Mac. To narzędzie dla deweloperów, umożliwia korzystanie z możliwości platformy .NET do tworzenia aplikacji dla wszystkich platform wymaganych przez użytkowników.

Użytkownik środowiska programu Visual Studio dla komputerów Mac jest podobny do jego odpowiednika Windows, ale o działaniu natywnych systemu macOS. Tworzenia, otwierania i tworzenia aplikacji będzie pracę w znanym środowisku dla każdego, kto ma korzystał już z programu Visual Studio na Windows. Ponadto program Visual Studio for Mac wykorzystuje wiele zaawansowanych narzędzi, które jego odpowiednika Windows zaawansowane IDE. Platformę kompilatora programu Roslyn jest używana do refaktoryzacji i technologii IntelliSense. Silnik projektu systemu i kompilacji, użyj programu MSBuild, a jego Edytor źródła obsługuje pakiety TextMate. Używa tego samego aparatów debugera dla aplikacji platformy Xamarin i .NET Core i ten sam projektantów Xamarin.iOS i Xamarin.Android.

W tym artykule przedstawiono różne części programu Visual Studio dla komputerów Mac, podając informacje o niektórych funkcji, które ułatwiają zaawansowane narzędzie do tworzenia aplikacji dla wielu platform.

## <a name="ide-tour"></a>Samouczek środowiska IDE

Program Visual Studio for Mac jest podzielony na kilka sekcji do plików aplikacji i ustawień tworzenia kodu aplikacji i zarządzanie debugowania.

::: zone pivot="vsmac2019"

## <a name="visual-studio-for-mac-2019-start-window"></a>Program Visual Studio for Mac 2019 rozpoczęcia okna

> [!TIP]
> Wizualne 2019 Studio dla komputerów Mac (wersja zapoznawcza) jest [dostępne do pobrania](install-preview.md) i testowania.

Po uruchomieniu programu Visual Studio for Mac 2019 r w wersji zapoznawczej, nowi użytkownicy będą widzieć okno logowania. Zaloguj się przy użyciu konta Microsoft można aktywować płatnej licencji (jeśli istnieje) lub link do subskrypcji platformy Azure. Możesz nacisnąć przycisk **Pomiń** i zalogować się później za pomocą **programu Visual Studio > Zaloguj się** element menu:

![Zaloguj się do swojego konta Microsoft](media/ide-tour-2019-start-signin.png)

Zalogowanych użytkowników zostanie wyświetlony nowy _uruchomić okno_, które wyświetla listę ostatnich projektów i przycisków, aby otworzyć istniejący projekt lub Utwórz nową:

![Wybierz z ostatnich projektów lub stwórz coś nowego](media/ide-tour-2019-start-projects.png)

::: zone-end
::: zone pivot="vsmac2017"

## <a name="welcome-screen-in-visual-studio-for-mac-2017"></a>Ekran powitalny w programie Visual Studio dla komputerów Mac 2017

Gdy uruchomiony, Visual Studio for Mac Wyświetla *ekran powitalny*:

![Ekran powitalny](media/ide-tour-image1.png)

Ekran powitalny zawiera następujące sekcje:

- **Pasek narzędzi** — zapewnia szybki dostęp do pasku wyszukiwania. Po załadowaniu rozwiązania, pasek narzędzi jest używana do ustawiania konfiguracji aplikacji, debugowania i wyświetlania błędów.
- **Wprowadzenie do** — zapewnia szybki dostęp do przydatnych tematów dla deweloperów rozpoczynających pracę z programem Visual Studio dla komputerów Mac.
- **Ostatnio używane rozwiązania** — zapewnia szybki dostęp do ostatnio otwartych rozwiązań, a także wygodny przyciski próbę otwarcia lub utworzenia projektów.
- **Wiadomości dla deweloperów** -kanał aktualności, powiadamia Cię o najnowsze informacje o Microsoft Developer.

::: zone-end

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Na poniższej ilustracji przedstawiono program Visual Studio dla komputerów Mac z aplikacją, załadowano:

![Załadowano programu Visual Studio dla komputerów Mac z aplikacją](media/ide-tour-image17.png)

Poniższe sekcje zawierają omówienie głównych obszarów w programie Visual Studio dla komputerów Mac.

## <a name="solution-pad"></a>Konsola rozwiązania

W konsoli rozwiązania organizuje projekty w rozwiązaniu:

![Projekty zorganizowane w konsoli rozwiązania](media/ide-tour-image18.png)

Jest to, gdzie plików kodu źródłowego, zasobów, interfejs użytkownika i zależności są zorganizowane w projektach specyficzne dla platformy.

Aby uzyskać więcej informacji na temat korzystania z projektów i rozwiązań w programie Visual Studio dla komputerów Mac, zobacz [projekty i rozwiązania](projects-and-solutions.md) artykułu.

## <a name="assembly-references"></a>Odwołania do zestawów

Odwołania do zestawów dla każdego projektu są dostępne w folderze odwołania:

![Folder odwołań w konsoli rozwiązania](media/ide-tour-image19.png)

Dodatkowe informacje są dodawane przy użyciu **Edytuj odwołania** okno dialogowe, która jest wyświetlana, klikając dwukrotnie plik w folderze odwołania lub wybierając **Edytuj odwołania** na jego akcje menu kontekstowe:

![Okno dialogowe odwołania do edycji](media/ide-tour-image20.png)

Aby uzyskać więcej informacji na temat korzystania z odwołań w programie Visual Studio dla komputerów Mac, zobacz [Zarządzanie odwołaniami w projekcie](managing-references-in-a-project.md) artykułu.

## <a name="dependencies--packages"></a>Zależności / pakietów

Wszystkie zależności zewnętrznych używanych w aplikacji są przechowywane w folderze zależności lub pakietów, w zależności od tego, czy jesteś w.Net Core lub Xamarin.iOS/Xamarin.Android projektu. Te zwykle znajdują się w formularzu NuGet.

NuGet jest najbardziej popularnych Menedżer pakietów dla programowania na platformie .NET. Obsługę pakietów NuGet dla programu Visual Studio można łatwo wyszukiwać i dodawanie pakietów do projektu do aplikacji.

Aby dodać zależności do aplikacji, kliknij prawym przyciskiem myszy zależności / pakiety folder, a następnie wybierz **Dodawanie pakietów**:

![Dodawanie pakietu NuGet](media/ide-tour-image21.png)

Informacje na temat korzystania z pakietu NuGet w aplikacji można znaleźć w [projektu w tym NuGet w projekcie](nuget-walkthrough.md) artykułu.

## <a name="refactoring"></a>Refaktoryzacja

Visual Studio dla komputerów Mac udostępnia dwa sposoby użyteczne, jakie możesz refaktoryzować swój kod: kontekstu akcji i analizy źródła. Możesz dowiedzieć się więcej o nich w [Refactoring](refactoring.md) artykułu.

## <a name="debugging"></a>Debugowanie

Visual Studio dla komputerów Mac ma debuger natywny umożliwiająca obsługę debugowania dla aplikacji platformy Xamarin.iOS, Xamarin.Mac i projektami interfejsu Xamarin.Android. Program Visual Studio for Mac używa platformy Mono nietrwałego debugera, która została wdrożona do środowiska uruchomieniowego Mono, dzięki czemu środowisko IDE do debugowania kodu zarządzanego na wszystkich platformach. Aby uzyskać dodatkowe informacje na temat debugowania, odwiedź stronę [debugowanie](debugging.md) artykułu.

Debuger zawiera bogaty wizualizatorów dla typów specjalnych, takich jak ciągi, kolory, adresy URL, tak jak rozmiarów, współrzędne i krzywych Beziera.

Aby uzyskać więcej informacji na temat wizualizacji danych funkcji debugera, odwiedź stronę [wizualizacje danych](data-visualizations.md) artykułu.

## <a name="version-control"></a>Kontrola wersji

Program Visual Studio for Mac integruje się z usługą Git i Subversion systemów kontroli źródła. Projektów pod kontrolą źródła są oznaczone symbolem gałęzi, na liście obok nazwy rozwiązania:

![Nazwa gałęzi, aby wskazać projektu objętego kontrolą źródła](media/ide-tour-image22.png)

Pliki bez wprowadzania zmian mają adnotacji na ich ikon w okienku rozwiązania, jak pokazano na poniższej ilustracji:

![Niezatwierdzone pliki w konsoli rozwiązania](media/ide-tour-image23.png)

Aby uzyskać więcej informacji na temat korzystania z systemu kontroli wersji w programie Visual Studio, zobacz [kontroli wersji](version-control.md) artykułu.

## <a name="see-also"></a>Zobacz także

- [Visual Studio IDE (na Windows)](/visualstudio/ide/visual-studio-ide)