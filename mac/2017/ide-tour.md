---
title: Przewodnik po programie Visual Studio dla komputerów Mac
description: Program Visual Studio dla komputerów Mac zapewnia zintegrowane środowisko programistyczne do tworzenia aplikacji platformy .NET w systemie macOS, w tym ASP.NET witrynach sieci Web core i projektów platformy Xamarin dla systemów iOS, Android, Mac i Xamarin.Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 3d25fced1e9c9dd6431f4056b5b561f476eecb28
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "74984985"
---
# <a name="visual-studio-2017-for-mac-tour"></a>Przewodnik po programie Visual Studio 2017 dla komputerów Mac

> [!NOTE]
> Visual Studio 2019 dla [komputerów](installation.md)Mac jest już dostępny .

Visual Studio dla komputerów Mac to _zintegrowane środowisko programistyczne_ platformy .NET na komputerze Mac, które może służyć do edytowania, debugowania i tworzenia kodu, a następnie publikowania aplikacji. Oprócz oczekiwanych funkcji, takich jak standardowy edytor i debuger, visual studio dla komputerów Mac zawiera kompilatory, narzędzia do uzupełniania kodu, projektantów graficznych i kontrolę źródła, aby opracować proces tworzenia oprogramowania.

Visual Studio dla komputerów Mac obsługuje wiele z tych `.csproj` `.fsproj`samych `.sln` typów plików, jak jego odpowiednik systemu Windows, takich jak , lub plików i obsługuje funkcje, takie jak EditorConfig, co oznacza, że można użyć IDE, który działa najlepiej dla Ciebie.
Tworzenie, otwieranie i tworzenie aplikacji będzie znanym doświadczeniem dla każdego, kto wcześniej korzystał z programu Visual Studio w systemie Windows. Ponadto program Visual Studio dla komputerów Mac wykorzystuje wiele zaawansowanych narzędzi, które sprawiają, że jego odpowiednik systemu Windows jest tak zaawansowanym IDE. Platforma kompilatora Roslyn służy do refaktoryzacji i IntelliSense. Jego system projektu i aparat kompilacji używać MSBuild, a jego edytor źródłowy obsługuje pakiety TextMate. Używa tych samych aparatów debugera dla aplikacji Platformy Xamarin i .NET Core i tych samych projektantów dla xamarin.iOS i Xamarin.Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Co można zrobić w programie Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac obsługuje następujące typy programów:

- ASP.NET podstawowych aplikacji sieci Web z c#, F#i obsługą stron Razor, JavaScript i TypeScript
- Aplikacje konsoli .NET Core z językami C# lub F #
- Wieloplatformowe gry i aplikacje Unity z C #
- Aplikacje dla systemów Android, iOS, tvOS i watchOS w języku Xamarin z językami C# lub F# i XAML
- Aplikacje klasyczne Kakao w języku C# lub F #

W tym artykule przedstawiono różne sekcje programu Visual Studio dla komputerów Mac, zapewniając spojrzenie na niektóre funkcje, które sprawiają, że jest to zaawansowane narzędzie do tworzenia tych aplikacji.

## <a name="ide-tour"></a>Przewodnik po środowisku IDE

Visual Studio dla komputerów Mac jest podzielony na kilka sekcji do zarządzania plikami aplikacji i ustawieniami, tworzenia kodu aplikacji i debugowania.

## <a name="welcome-screen"></a>Ekran powitalny

Po uruchomieniu program Visual Studio dla komputerów Mac wyświetla *ekran powitalny:*

![Ekran powitalny](media/ide-tour-image1.png)

Ekran powitalny zawiera następujące sekcje:

- **Pasek narzędzi** — zapewnia szybki dostęp do paska wyszukiwania. Po załadowaniu rozwiązania pasek narzędzi służy do ustawiania konfiguracji aplikacji, debugowania i wyświetlania błędów.
- **Wprowadzenie** — zapewnia szybki dostęp do przydatnych tematów dla deweloperów wprowadzenie do programu Visual Studio dla komputerów Mac.
- **Najnowsze rozwiązania** — zapewnia szybki dostęp do ostatnio otwieranych rozwiązań, a także wygodne przyciski do otwierania lub tworzenia projektów.
- **Wiadomości dla deweloperów** — kanał informacyjny, który zapewnia aktualną informacje o najnowszych informacjach o programie Microsoft Developer.

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Na poniższej ilustracji przedstawiono program Visual Studio dla komputerów Mac z załadowaną aplikacją:

![Visual Studio dla komputerów Mac z załadowaną aplikacją](media/ide-tour-image17.png)

Poniższe sekcje zawierają omówienie głównych obszarów w programie Visual Studio dla komputerów Mac.

## <a name="solution-pad"></a>Podkładka rozrachowa

Solution Pad organizuje projekt(y) w rozwiązaniu:

![Projekty organizowane w Solution Pad](media/ide-tour-image18.png)

Jest to, gdzie pliki dla kodu źródłowego, zasoby, interfejs użytkownika i zależności są zorganizowane w projekty specyficzne dla platformy.

Aby uzyskać więcej informacji na temat korzystania z projektów i rozwiązań w programie Visual Studio dla [komputerów](/visualstudio/mac/projects-and-solutions) Mac, zobacz projekty i rozwiązania artykułu.

## <a name="assembly-references"></a>Odwołania do złożenia

Odwołania do zestawu dla każdego projektu są dostępne w folderze Odwołania:

![Folder Odwołania w konsoli rozwiązania](media/ide-tour-image19.png)

Dodatkowe odwołania są dodawane za pomocą okna dialogowego **Edytuj odwołania,** które jest wyświetlane przez dwukrotne kliknięcie folderu Odwołania lub wybranie opcji Edytuj odwołania w jego **akcjach** menu kontekstowego:

![Okno dialogowe Edytowanie odwołań](media/ide-tour-image20.png)

Aby uzyskać więcej informacji na temat korzystania z odwołań w programie Visual Studio dla komputerów Mac, zobacz [zarządzanie odwołaniami w](/visualstudio/mac/managing-references-in-a-project) artykule Project.

## <a name="dependencies--packages"></a>Zależności / Pakiety

Wszystkie zależności zewnętrzne używane w aplikacji są przechowywane w folderze Zależności lub Pakiety, w zależności od tego, czy jesteś w projekcie .Net Core lub Xamarin.iOS/Xamarin.Android. Są one zwykle dostarczane w formie NuGet.

NuGet jest najpopularniejszym menedżerem pakietów dla rozwoju platformy .NET. Za pomocą pomocy technicznej NuGet programu Visual Studio można łatwo wyszukiwać i dodawać pakiety do projektu do aplikacji.

Aby dodać zależność do aplikacji, kliknij prawym przyciskiem myszy folder Zależności / Pakiety, a następnie wybierz pozycję **Dodaj pakiety:**

![Dodawanie pakietu NuGet](media/ide-tour-image21.png)

Informacje na temat korzystania z pakietu NuGet w aplikacji można znaleźć w [Including projektu NuGet w](/visualstudio/mac/nuget-walkthrough) artykule projektu.

## <a name="refactoring"></a>Refaktoryzacja

Visual Studio dla komputerów Mac udostępnia dwa przydatne sposoby refaktoryzacji kodu: Akcje kontekstu i analiza źródła. Możesz przeczytać więcej o nich w [refaktoryzacji](/visualstudio/mac/refactoring) artykułu.

## <a name="debugging"></a>Debugging

Visual Studio dla komputerów Mac ma natywnego debugera umożliwiającego obsługę debugowania dla aplikacji Xamarin.iOS, Xamarin.Mac i Xamarin.Android. Visual Studio dla komputerów Mac używa debugera mono soft, który jest zaimplementowany w czasie wykonywania Mono, umożliwiając IDE do debugowania kodu zarządzanego na wszystkich platformach. Aby uzyskać dodatkowe informacje na temat debugowania, odwiedź artykuł [debugowania.](/visualstudio/mac/debugging)

Debuger zawiera zaawansowane wizualizatory dla typów specjalnych, takich jak ciągi, kolory, adresy URL, a także rozmiary, współrzędne i krzywe béziera.

Aby uzyskać więcej informacji na temat wizualizacji danych debugera, odwiedź artykuł [Wizualizacje danych.](/visualstudio/mac/data-visualizations)

## <a name="version-control"></a>Kontrola wersji

Visual Studio dla komputerów Mac integruje się z systemami kontroli źródła Git i Subversion. Projekty pod kontrolą źródła są oznaczane z gałęzi wymienionych obok nazwy rozwiązania:

![Nazwa oddziału wskazująca projekt pod kontrolą źródła](media/ide-tour-image22.png)

Pliki z niezatwierdzonych zmianami mają adnotację na swoich ikonach w okienku rozwiązania, jak pokazano na poniższej ilustracji:

![Niezatwierdzone pliki w konsoli rozwiązania](media/ide-tour-image23.png)

Aby uzyskać więcej informacji na temat korzystania z kontroli wersji w programie Visual Studio, zobacz [w artykule Kontrola wersji.](/visualstudio/mac/version-control)

## <a name="related-video"></a>Podobne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Zobacz też

- [Środowiska IDE programu Visual Studio (w systemie Windows)](/visualstudio/ide/visual-studio-ide)
