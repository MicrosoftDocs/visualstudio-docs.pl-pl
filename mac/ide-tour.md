---
title: Visual Studio for Mac Tour
description: Visual Studio dla komputerów Mac udostępnia zintegrowane środowisko projektowe umożliwiające tworzenie aplikacji .NET w systemie macOS, w tym witryny sieci Web platformy ASP.NET Core oraz projekty Xamarin dla systemu iOS, Android, Mac i zestawu narzędzi Xamarin.Forms.
author: conceptdev
ms.author: crdun
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: e192f75508173cd4014e391168ab27e9abe2bc9a
ms.sourcegitcommit: da73f7a0cf1795d5d400c0897ae3326191435dd0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58573013"
---
# <a name="visual-studio-2019-for-mac-preview-tour"></a>Visual Studio 2019 r, aby zapoznać się z komputerów Mac (wersja zapoznawcza)

> [!NOTE]
> Visual Studio 2019 r dla komputerów Mac jest [udostępniono](installation.md) w wersji zapoznawczej na potrzeby testowania.

Program Visual Studio dla komputerów Mac jest .NET _zintegrowanego środowiska programistycznego_ na komputerze Mac, który może służyć do edycji, debugowania i kompilowanie kodu, a następnie opublikować aplikację. Oprócz oczekiwane funkcje, takie jak standardowy edytor i debugera Visual Studio for Mac obejmuje kompilatory, narzędzia uzupełniania kodu, projektanci graficzni i kontroli źródła do aparatu ese procesu tworzenia oprogramowania.

Program Visual Studio for Mac obsługuje wiele typów plików jako jego odpowiednika Windows, takich jak `.csproj`, `.fsproj`, lub `.sln` pliki i obsługuje funkcje, takie jak EditorConfig, co oznacza, użyć środowiska IDE, który w najlepszy dla siebie.
Tworzenia, otwierania i tworzenia aplikacji będzie pracę w znanym środowisku dla każdego, kto ma korzystał już z programu Visual Studio na Windows. Ponadto program Visual Studio for Mac wykorzystuje wiele zaawansowanych narzędzi, które jego odpowiednika Windows zaawansowane IDE. Platformę kompilatora programu Roslyn jest używana do refaktoryzacji i technologii IntelliSense. Silnik projektu systemu i kompilacji, użyj programu MSBuild, a jego Edytor źródła obsługuje pakiety TextMate. Używa tego samego aparatów debugera dla aplikacji platformy Xamarin i .NET Core i ten sam projektantów Xamarin.iOS i Xamarin.Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Co można zrobić w programie Visual Studio dla komputerów Mac

Program Visual Studio for Mac obsługuje następujące typy tworzenia:

- Aplikacje sieci web platformy ASP.NET Core za pomocą C#, F#i pomoc techniczna dla stron Razor, JavaScript i TypeScript
- Aplikacje konsoli .NET core za pomocą C# lubF#
- Gry Unity dla wielu platform i aplikacji przy użyciuC#
- Aplikacje systemu android, iOS, tvOS i watchOS w środowisku Xamarin za pomocą C# lub F# i XAML
- Cocoa aplikacje komputerowe w C# lubF#

W tym artykule przedstawiono różne części programu Visual Studio dla komputerów Mac, podając informacje o niektórych funkcji, które ułatwiają zaawansowane narzędzie do tworzenia tych aplikacji.

## <a name="ide-tour"></a>Samouczek środowiska IDE

Program Visual Studio for Mac jest podzielony na kilka sekcji do plików aplikacji i ustawień tworzenia kodu aplikacji i zarządzanie debugowania.

## <a name="new-start-window"></a>Nowe okno uruchamiania

Po uruchomieniu programu Visual Studio 2019 dla komputerów Mac w wersji zapoznawczej, nowi użytkownicy będą widzieć okno logowania. Zaloguj się przy użyciu konta Microsoft można aktywować płatnej licencji (jeśli istnieje) lub link do subskrypcji platformy Azure. Możesz nacisnąć przycisk **Pomiń** i zalogować się później za pomocą **programu Visual Studio > Zaloguj się** element menu:

![Zaloguj się do swojego konta Microsoft](media/ide-tour-2019-start-signin.png)

Zalogowanych użytkowników zostanie wyświetlony nowy _uruchomić okno_, które wyświetla listę ostatnich projektów i przycisków, aby otworzyć istniejący projekt lub Utwórz nową:

![Wybierz z ostatnich projektów lub stwórz coś nowego](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Na poniższej ilustracji przedstawiono program Visual Studio dla komputerów Mac z aplikacją, załadowano:

![Załadowano programu Visual Studio dla komputerów Mac z aplikacją](media/ide-tour-image17.png)

Poniższe sekcje zawierają omówienie głównych obszarów w programie Visual Studio dla komputerów Mac.

## <a name="solution-pad"></a>Konsola rozwiązania

W konsoli rozwiązania organizuje projekty w rozwiązaniu:

![Projekty zorganizowane w konsoli rozwiązania](media/ide-tour-image18.png)

Jest to, gdzie plików kodu źródłowego, zasobów, interfejs użytkownika i zależności są zorganizowane w projektach specyficzne dla platformy.

Aby uzyskać więcej informacji na temat korzystania z projektów i rozwiązań w programie Visual Studio dla komputerów Mac, zobacz [projekty i rozwiązania](/visualstudio/mac/projects-and-solutions) artykułu.

## <a name="assembly-references"></a>Odwołania do zestawów

Odwołania do zestawów dla każdego projektu są dostępne w folderze odwołania:

![Folder odwołań w konsoli rozwiązania](media/ide-tour-image19.png)

Dodatkowe informacje są dodawane przy użyciu **Edytuj odwołania** okno dialogowe, która jest wyświetlana, klikając dwukrotnie plik w folderze odwołania lub wybierając **Edytuj odwołania** na jego akcje menu kontekstowe:

![Okno dialogowe odwołania do edycji](media/ide-tour-image20.png)

Aby uzyskać więcej informacji na temat korzystania z odwołań w programie Visual Studio dla komputerów Mac, zobacz [Zarządzanie odwołaniami w projekcie](/visualstudio/mac/managing-references-in-a-project) artykułu.

## <a name="dependencies--packages"></a>Zależności / pakietów

Wszystkie zależności zewnętrznych używanych w aplikacji są przechowywane w folderze zależności lub pakietów, w zależności od tego, czy jesteś w.Net Core lub Xamarin.iOS/Xamarin.Android projektu. Te zwykle znajdują się w formularzu NuGet.

NuGet jest najbardziej popularnych Menedżer pakietów dla programowania na platformie .NET. Obsługę pakietów NuGet dla programu Visual Studio można łatwo wyszukiwać i dodawanie pakietów do projektu do aplikacji.

Aby dodać zależności do aplikacji, kliknij prawym przyciskiem myszy zależności / pakiety folder, a następnie wybierz **Dodawanie pakietów**:

![Dodawanie pakietu NuGet](media/ide-tour-image21.png)

Informacje na temat korzystania z pakietu NuGet w aplikacji można znaleźć w [projektu w tym NuGet w projekcie](/visualstudio/mac/nuget-walkthrough) artykułu.

## <a name="refactoring"></a>Refaktoryzacja

Visual Studio dla komputerów Mac udostępnia dwa sposoby użyteczne, jakie możesz refaktoryzować swój kod: Kontekst akcji, a analiza źródła. Możesz dowiedzieć się więcej o nich w [Refactoring](/visualstudio/mac/refactoring) artykułu.

## <a name="debugging"></a>Debugowanie

Visual Studio dla komputerów Mac ma debuger natywny umożliwiająca obsługę debugowania dla aplikacji platformy Xamarin.iOS, Xamarin.Mac i projektami interfejsu Xamarin.Android. Program Visual Studio for Mac używa platformy Mono nietrwałego debugera, która została wdrożona do środowiska uruchomieniowego Mono, dzięki czemu środowisko IDE do debugowania kodu zarządzanego na wszystkich platformach. Aby uzyskać dodatkowe informacje na temat debugowania, odwiedź stronę [debugowanie](/visualstudio/mac/debugging) artykułu.

Debuger zawiera bogaty wizualizatorów dla typów specjalnych, takich jak ciągi, kolory, adresy URL, tak jak rozmiarów, współrzędne i krzywych Beziera.

Aby uzyskać więcej informacji na temat wizualizacji danych funkcji debugera, odwiedź stronę [wizualizacje danych](/visualstudio/mac/data-visualizations) artykułu.

## <a name="version-control"></a>Kontrola wersji

Program Visual Studio for Mac integruje się z usługą Git i Subversion systemów kontroli źródła. Projektów pod kontrolą źródła są oznaczone symbolem gałęzi, na liście obok nazwy rozwiązania:

![Nazwa gałęzi, aby wskazać projektu objętego kontrolą źródła](media/ide-tour-image22.png)

Pliki bez wprowadzania zmian mają adnotacji na ich ikon w okienku rozwiązania, jak pokazano na poniższej ilustracji:

![Niezatwierdzone pliki w konsoli rozwiązania](media/ide-tour-image23.png)

Aby uzyskać więcej informacji na temat korzystania z systemu kontroli wersji w programie Visual Studio, zobacz [kontroli wersji](/visualstudio/mac/version-control) artykułu.

## <a name="next-steps"></a>Następne kroki

- [Zainstaluj program Visual Studio dla komputerów Mac](installation.md)
- [Przejrzyj dostępne obciążeń](/visualstudio/mac/workloads/)

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Zobacz także

- [Visual Studio IDE (na Windows)](/visualstudio/ide/visual-studio-ide)
