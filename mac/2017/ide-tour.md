---
title: Przewodnik Visual Studio dla komputerów Mac
description: Visual Studio dla komputerów Mac zapewnia zintegrowane środowisko programistyczne do kompilowania aplikacji .NET w systemie macOS, w tym ASP.NET Core witryn sieci Web i projektów platformy Xamarin dla systemów iOS, Android, Mac i Xamarin. Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 02/07/2019
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 3d25fced1e9c9dd6431f4056b5b561f476eecb28
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74984985"
---
# <a name="visual-studio-2017-for-mac-tour"></a>Przewodnik po programie Visual Studio 2017 for Mac

> [!NOTE]
> Program Visual Studio 2019 for Mac jest [teraz dostępny](installation.md).

Visual Studio dla komputerów Mac to _zintegrowane środowisko deweloperskie_ platformy .NET na komputerze Mac, które może służyć do edytowania, debugowania i kompilowania kodu, a następnie publikowania aplikacji. Oprócz oczekiwanych funkcji, takich jak standardowy Edytor i debuger, Visual Studio dla komputerów Mac obejmuje kompilatory, narzędzia do uzupełniania kodu, graficzne projektantów i kontrolę źródła w celu przetworzenia oprogramowania ESE.

Visual Studio dla komputerów Mac obsługuje wiele takich samych typów plików jak odpowiedniki systemu Windows, takie jak `.csproj` , `.fsproj` lub `.sln` pliki, i obsługuje funkcje takie jak EditorConfig, co oznacza, że można użyć środowiska IDE, które najlepiej działa.
Tworzenie, otwieranie i opracowywanie aplikacji jest znanym doświadczeniem dla każdej osoby, która wcześniej korzystała z programu Visual Studio w systemie Windows. Ponadto Visual Studio dla komputerów Mac korzysta z wielu zaawansowanych narzędzi, które sprawiają, że system Windows ma odpowiedni, wydajny IDE. Platforma kompilatora Roslyn jest używana do refaktoryzacji i IntelliSense. Jego system projektu i aparat kompilacji używają programu MSBuild, a jego Edytor źródła obsługuje zbiory deautomatyzuje. Używa tych samych aparatów debugera dla aplikacji Xamarin i .NET Core oraz tych samych projektantów dla Xamarin. iOS i Xamarin. Android.

## <a name="what-can-i-do-in-visual-studio-for-mac"></a>Co mogę zrobić w Visual Studio dla komputerów Mac

Visual Studio dla komputerów Mac obsługuje następujące typy rozwoju:

- ASP.NET Core aplikacji sieci Web przy użyciu języków C#, F # i obsługi stron Razor, JavaScript i TypeScript
- Aplikacje konsolowe platformy .NET Core w języku C# lub F #
- Wieloplatformowe gry Unity i aplikacje w języku C #
- Aplikacje dla systemów Android, iOS, systemu tvOS i systemu watchOS w oprogramowaniu Xamarin z C# lub F # i XAML
- Aplikacje klasyczne dla kakao w języku C# lub F #

Ten artykuł zawiera informacje o różnych sekcjach Visual Studio dla komputerów Mac, co zapewnia pewne funkcje, które sprawiają, że jest to zaawansowane narzędzie do tworzenia tych aplikacji.

## <a name="ide-tour"></a>Przewodnik po środowisku IDE

Visual Studio dla komputerów Mac jest zorganizowany w kilka sekcji do zarządzania plikami i ustawieniami aplikacji, tworzenia kodu aplikacji i debugowania.

## <a name="welcome-screen"></a>Ekran powitalny

Po uruchomieniu Visual Studio dla komputerów Mac wyświetla *ekran powitalny*:

![Ekran powitalny](media/ide-tour-image1.png)

Ekran powitalny zawiera następujące sekcje:

- **Pasek narzędzi** — zapewnia szybki dostęp do paska wyszukiwania. Po załadowaniu rozwiązania pasek narzędzi służy do ustawiania konfiguracji aplikacji, debugowania i wyświetlania błędów.
- **Wprowadzenie** — zapewnia szybki dostęp do przydatnych tematów dla deweloperów rozpoczynających pracę z programem Visual Studio dla komputerów Mac.
- **Najnowsze rozwiązania** — zapewnia szybki dostęp do ostatnio otwieranych rozwiązań, a także wygodne przyciski umożliwiające otwieranie i tworzenie projektów.
- **Wiadomości dla deweloperów** — kanał informacyjny z informacjami na temat najnowszych informacji dla deweloperów firmy Microsoft.

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Na poniższej ilustracji przedstawiono Visual Studio dla komputerów Mac z załadowana aplikacją:

![Visual Studio dla komputerów Mac z załadowana aplikacją](media/ide-tour-image17.png)

Poniższe sekcje zawierają omówienie głównych obszarów w Visual Studio dla komputerów Mac.

## <a name="solution-pad"></a>okienko rozwiązania

Okienko rozwiązania organizuje projekty w rozwiązaniu:

![Projekty zorganizowane w okienko rozwiązania](media/ide-tour-image18.png)

Jest to miejsce, w którym pliki kodu źródłowego, zasobów, interfejsu użytkownika i zależności są zorganizowane w projekty specyficzne dla platformy.

Aby uzyskać więcej informacji na temat korzystania z projektów i rozwiązań w Visual Studio dla komputerów Mac, zobacz artykuł [projekty i rozwiązania](/visualstudio/mac/projects-and-solutions) .

## <a name="assembly-references"></a>Odwołania do zestawów

Odwołania do zestawów dla każdego projektu są dostępne w folderze References:

![Odwołuje się do folderu w konsoli rozwiązania](media/ide-tour-image19.png)

Dodatkowe odwołania są dodawane za pomocą okna dialogowego **Edytowanie odwołań** , który jest wyświetlany przez dwukrotne kliknięcie folderu References lub wybranie polecenia **Edytuj odwołania** w jego akcjach menu kontekstowego:

![Edytowanie odwołań — okno dialogowe](media/ide-tour-image20.png)

Aby uzyskać więcej informacji na temat używania odwołań w Visual Studio dla komputerów Mac, zobacz [Zarządzanie odwołaniami w](/visualstudio/mac/managing-references-in-a-project) artykule dotyczącym projektu.

## <a name="dependencies--packages"></a>Zależności/pakiety

Wszystkie zależności zewnętrzne używane w aplikacji są przechowywane w folderze zależności lub pakiety, w zależności od tego, czy jesteś w projekcie .Net Core czy Xamarin. iOS/Xamarin. Android. Są one zazwyczaj udostępniane w postaci NuGet.

Pakiet NuGet jest najpopularniejszym menedżerem pakietów na potrzeby programowania na platformie .NET. Dzięki obsłudze NuGet programu Visual Studio można łatwo wyszukiwać i dodawać pakiety do projektu do aplikacji.

Aby dodać zależność do aplikacji, kliknij prawym przyciskiem myszy folder zależności/pakiety, a następnie wybierz polecenie **Dodaj pakiety**:

![Dodawanie pakietu NuGet](media/ide-tour-image21.png)

Informacje na temat korzystania z pakietu NuGet w aplikacji można znaleźć w temacie [zawierającym projekt NuGet w artykule dotyczącym projektu](/visualstudio/mac/nuget-walkthrough) .

## <a name="refactoring"></a>Refaktoryzacja

Visual Studio dla komputerów Mac zapewnia dwa przydatne metody refaktoryzacji kodu: akcje kontekstu i analiza źródła. Więcej informacji na ten temat można znaleźć w artykule [refaktoryzacji](/visualstudio/mac/refactoring) .

## <a name="debugging"></a>Debugowanie

Visual Studio dla komputerów Mac ma natywny debuger umożliwiający obsługę debugowania dla aplikacji Xamarin. iOS, Xamarin. Mac i Xamarin. Android. Visual Studio dla komputerów Mac używa debugera miękkiego mono, który jest implementowany w środowisku uruchomieniowym mono, umożliwiając IDE Debugowanie kodu zarządzanego na wszystkich platformach. Aby uzyskać dodatkowe informacje na temat debugowania, zapoznaj się z artykułem dotyczącym [debugowania](/visualstudio/mac/debugging) .

Debuger zawiera rozbudowane Wizualizatory dla typów specjalnych, takich jak ciągi, kolory, adresy URL, jak również rozmiary, współrzędne i krzywe Beziera.

Aby uzyskać więcej informacji na temat wizualizacji danych debugera, zapoznaj się z artykułem [wizualizacje danych](/visualstudio/mac/data-visualizations) .

## <a name="version-control"></a>Kontrola wersji

Visual Studio dla komputerów Mac integruje się z systemami kontroli źródła git i Subversion. Projekty w obszarze kontroli źródła są oznaczane rozgałęzieniem wymienionym obok nazwy rozwiązania:

![Nazwa rozgałęzienia wskazująca projekt pod kontrolą źródła](media/ide-tour-image22.png)

Pliki z niezatwierdzonymi zmianami mają adnotację w ikonach w okienku rozwiązanie, jak pokazano na poniższej ilustracji:

![Pliki niezatwierdzone w konsoli rozwiązania](media/ide-tour-image23.png)

Aby uzyskać więcej informacji na temat korzystania z kontroli wersji w programie Visual Studio, zobacz artykuł dotyczący [kontroli wersji](/visualstudio/mac/version-control) .

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Zobacz też

- [Środowisko IDE programu Visual Studio (w systemie Windows)](/visualstudio/ide/visual-studio-ide)
