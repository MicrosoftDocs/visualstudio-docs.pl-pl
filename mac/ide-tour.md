---
title: Przewodnik Visual Studio dla komputerów Mac
description: Visual Studio dla komputerów Mac zapewnia zintegrowane środowisko programistyczne do kompilowania aplikacji .NET w systemie macOS, w tym ASP.NET Core witryn sieci Web i projektów platformy Xamarin dla systemów iOS, Android, Mac i Xamarin. Forms.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 07/03/2020
ms.assetid: 7DC64A52-AA41-4F3A-A8A1-8A20BCD81CC7
ms.custom: video
ms.openlocfilehash: 56af8f7cd30ec8e41ece2772dc63d67a2dbf3976
ms.sourcegitcommit: 703c68667261df5985a73282c1cbb0541118989c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89402616"
---
# <a name="visual-studio-2019-for-mac-tour"></a>Przewodnik po programie Visual Studio 2019 for Mac

Visual Studio dla komputerów Mac to _zintegrowane środowisko deweloperskie_ platformy .NET na komputerze Mac, które może służyć do edytowania, debugowania i kompilowania kodu, a następnie publikowania aplikacji. Oprócz edytora kodu i debugera, Visual Studio dla komputerów Mac obejmuje kompilatory, narzędzia do uzupełniania kodu, graficzne projektantów i funkcje kontroli źródła ułatwiające proces tworzenia oprogramowania.

Visual Studio dla komputerów Mac obsługuje wiele takich samych typów plików jak odpowiedniki systemu Windows, takie jak `.csproj` , `.fsproj` lub `.sln` pliki, i obsługuje funkcje takie jak EditorConfig, co oznacza, że można użyć środowiska IDE, które najlepiej działa.
Tworzenie, otwieranie i opracowywanie aplikacji jest znanym doświadczeniem dla każdej osoby, która wcześniej korzystała z programu Visual Studio w systemie Windows. Ponadto Visual Studio dla komputerów Mac korzysta z wielu zaawansowanych narzędzi, które sprawiają, że system Windows ma odpowiedni, wydajny IDE. Platforma kompilatora Roslyn jest używana do refaktoryzacji i IntelliSense. Jego system projektu i aparat kompilacji używają programu MSBuild, a jego Edytor źródła używa tego samego podstaw, co program Visual Studio w systemie Windows. Używa tych samych aparatów debugera dla aplikacji Xamarin i .NET Core oraz tych samych projektantów dla Xamarin. iOS i Xamarin. Android.

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

## <a name="getting-started"></a>Wprowadzenie

Po pierwszym uruchomieniu programu Visual Studio 2019 dla komputerów Mac nowi użytkownicy zobaczą okno logowania. Zaloguj się przy użyciu konto Microsoft, aby aktywować płatną licencję (Jeśli masz ją) lub połączyć się z subskrypcjami platformy Azure. Można nacisnąć **i** zalogować się później za pomocą programu **Visual Studio > Zaloguj się** :

![Zaloguj się do konto Microsoft](media/ide-tour-2019-start-signin.png)

Następnie będziesz mieć możliwość dostosowania środowiska IDE, wybierając preferowane skróty klawiaturowe: Visual Studio dla komputerów Mac, Visual Studio, Visual Studio Code lub Xcode:

![Wybierz Ulubione skróty klawiaturowe](media/ide-tour-2019-keyboard-shortcut.png)

Po tym początkowym uruchomieniu Instalatora zobaczysz _okno Start_ po otwarciu programu Visual Studio 2019 for Mac, w którym jest wyświetlana lista ostatnich projektów i przyciski umożliwiające otwarcie istniejącego projektu lub Utwórz nowy:

![Wybierz z ostatnich projektów lub Utwórz coś nowego](media/ide-tour-2019-start-projects.png)

## <a name="solutions-and-projects"></a>Rozwiązania i projekty

Na poniższej ilustracji przedstawiono Visual Studio dla komputerów Mac z załadowana aplikacją:

![Visual Studio dla komputerów Mac z załadowana aplikacją](media/ide-tour-image17.png)

Poniższe sekcje zawierają omówienie głównych obszarów w Visual Studio dla komputerów Mac.

## <a name="solution-pad"></a>Konsola rozwiązania

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

Wszystkie zależności zewnętrzne używane w aplikacji są przechowywane w folderze zależności lub pakiety, w zależności od tego, czy jesteś w projekcie platformy .NET Core czy Xamarin. iOS/Xamarin. Android. Są one zazwyczaj udostępniane w postaci NuGet.

Pakiet NuGet jest najpopularniejszym menedżerem pakietów na potrzeby programowania na platformie .NET. Dzięki obsłudze NuGet programu Visual Studio można łatwo wyszukiwać i dodawać pakiety do projektu do aplikacji.

Aby dodać zależność do aplikacji, kliknij prawym przyciskiem myszy folder zależności/pakiety, a następnie wybierz polecenie **Dodaj pakiety**:

![Dodawanie pakietu NuGet](media/ide-tour-image21.png)

Informacje na temat korzystania z pakietu NuGet w aplikacji można znaleźć w temacie [zawierającym projekt NuGet w artykule dotyczącym projektu](/visualstudio/mac/nuget-walkthrough) .

## <a name="source-editor"></a>Edytor źródeł

Bez względu na to, czy piszesz w języku C#, XAML czy JavaScript, Edytor kodu współużytkuje te same podstawowe składniki z programem Visual Studio w systemie Windows za pomocą całkowicie natywnego interfejsu użytkownika.

W ten sposób przedstawiono niektóre z następujących funkcji:

* Natywny interfejs użytkownika systemu macOS oparty na platformie Cocoa (etykietki narzędzi, powierzchnia edytora, informacje wizualne na marginesach, renderowanie tekstu, IntelliSense)
* Filtrowanie typów IntelliSense i "Pokaż elementy importowane"
* Obsługa natywnego wprowadzania tekstu
* Obsługa języka RTL/BiDi
* Roslyn 3
* Obsługa wielu karetek
* Zawijanie wierszy
* Zaktualizowany interfejs użytkownika IntelliSense
* Ulepszone Znajdowanie/zamienianie
* Obsługa fragmentów kodu 
* Formatowanie zaznaczenia
* Żarówki w tekście

Więcej informacji o korzystaniu z edytora źródła w Visual Studio dla komputerów Mac można znaleźć w dokumentacji [edytora źródła](/visualstudio/mac/source-editor) .

Aby zapewnić widoczność kart przez cały czas, możesz skorzystać z przypięcia. Zapewnia to, że za każdym razem, gdy uruchamiasz projekt, zawsze będzie wyświetlana karta. Aby przypiąć kartę, umieść kursor nad kartą i kliknij ikonę _pinezki_ :

![Przypinanie karty](media/ide-tour-tabpin.png)

## <a name="refactoring"></a>Refaktoryzacja

Visual Studio dla komputerów Mac zapewnia dwa przydatne metody refaktoryzacji kodu: akcje kontekstu i analiza źródła. Więcej informacji na ten temat można znaleźć w artykule [refaktoryzacji](/visualstudio/mac/refactoring) .

## <a name="debugging"></a>Debugowanie

Visual Studio dla komputerów Mac ma debugery obsługujące projekty platformy .NET Core, .NET Framework, Unity i Xamarin. Visual Studio dla komputerów Mac używa debugera .NET Core i programu mono Soft Debugger, umożliwiając IDE Debugowanie kodu zarządzanego na wszystkich platformach. Aby uzyskać dodatkowe informacje na temat debugowania, zapoznaj się z artykułem dotyczącym [debugowania](/visualstudio/mac/debugging) .

Debuger zawiera rozbudowane Wizualizatory dla typów specjalnych, takich jak ciągi, kolory, adresy URL, a także rozmiary, współrzędne i krzywe Beziera.

Aby uzyskać więcej informacji na temat wizualizacji danych debugera, zapoznaj się z artykułem [wizualizacje danych](/visualstudio/mac/data-visualizations) .

## <a name="version-control"></a>Kontrola wersji

Visual Studio dla komputerów Mac integruje się z systemami kontroli źródła git i Subversion. Projekty w obszarze kontroli źródła są oznaczane rozgałęzieniem wymienionym obok nazwy rozwiązania:

![Nazwa rozgałęzienia wskazująca projekt pod kontrolą źródła](media/ide-tour-image22.png)

Pliki z niezatwierdzonymi zmianami mają adnotację w ikonach w okienku rozwiązanie, jak pokazano na poniższej ilustracji:

![Pliki niezatwierdzone w konsoli rozwiązania](media/ide-tour-image23.png)

Aby uzyskać więcej informacji na temat korzystania z kontroli wersji w programie Visual Studio, zobacz artykuł dotyczący [kontroli wersji](/visualstudio/mac/version-control) .

## <a name="next-steps"></a>Następne kroki

- [Instalowanie programu Visual Studio dla komputerów Mac](installation.md)
- [Przejrzyj dostępne obciążenia](workloads.md)

## <a name="related-video"></a>Pokrewne wideo

> [!Video https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Visual-Studio-for-Mac-Overview/player]

## <a name="see-also"></a>Zobacz też

- [Środowisko IDE programu Visual Studio (w systemie Windows)](/visualstudio/ide/visual-studio-ide)
