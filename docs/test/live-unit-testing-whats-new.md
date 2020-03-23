---
title: Co nowego w testach jednostek na żywo w programie Visual Studio 2017
titleSuffix: ''
ms.date: 10/11/2017
ms.topic: conceptual
helpviewer_keywords:
- Live Unit Testing
- Live Unit Testing What's New
author: mikejo5000
ms.author: mikejo
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: 7f7ab0c257bfed4521e95d9da12eaa0b9e25a71e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114272"
---
# <a name="whats-new-in-live-unit-testing-for-visual-studio-2017"></a>Co nowego w testach jednostek na żywo dla programu Visual Studio 2017

W tym temacie wymieniono nowe funkcje dodane do testowania jednostek na żywo w każdej wersji programu Visual Studio, począwszy od programu Visual Studio 2017 w wersji 15.3. Aby zapoznać się z omówieniem sposobu korzystania z testowania jednostek na żywo, zobacz [Testowanie jednostek na żywo w programie Visual Studio.](live-unit-testing.md)

## <a name="version-154"></a>Wersja 15.4

Począwszy od programu Visual Studio 2017 w wersji 15.4, testowanie jednostek na żywo obejmuje ulepszenia i ulepszenia w wielu obszarach:

- **Poprawiono wykrywalność**. Dla użytkowników, którzy nie wiedzą, że funkcja testowania jednostek na żywo istnieje, Ide programu Visual Studio pokazuje złoty pasek, który wspomina live unit testing, gdy użytkownik otwiera rozwiązanie, które zawiera testy jednostkowe, ale testowanie jednostek na żywo nie jest włączona. Informacje przedstawione w złotym pasku pozwala użytkownikowi dowiedzieć się więcej o Live Unit Testing i włączyć go. Złoty pasek wyświetla również informacje, gdy wymagania wstępne testowania jednostek na żywo nie są spełnione. Należą do nich:

  - Brakuje adapterów testowych.
  - Starsze wersje kart testowych są obecne.
  - Przywracanie pakietów NuGet, do których odwołuje się rozwiązanie, jest potrzebne.

- **Integracja z powiadomieniami Centrum zadań**. Ide programu Visual Studio pokazuje teraz powiadomienie o przetwarzaniu w tle testowania jednostek na żywo w Centrum zadań, dzięki czemu użytkownicy mogą łatwo stwierdzić, co się dzieje, gdy włączone jest testowanie jednostek na żywo. Rozwiązuje to kluczowy problem związany z uruchamianiem testów jednostkowych na żywo w dużym rozwiązaniu. Wcześniej przez kilka minut, aż pojawiły się ikony pokrycia, użytkownicy nie mogli określić, czy testowanie jednostek na żywo było naprawdę włączone i czy działało. Już nie!

- **Obsługa struktury MSTest w wersji 1:** Live Unit Testing już działa z trzema popularnymi strukturami testowania jednostek: xUnit, NUnit i MSTest. Wcześniej live unit testing działał tylko wtedy, gdy projekty testów jednostkowych MSTest używane MS Test w wersji 2. Począwszy od programu Visual Studio 2017 w wersji 15.4, teraz obsługuje również MSTest w wersji 1, jak również.

- **Niezawodność & wydajność:** Live Unit Testing zapewnia teraz, że system może lepiej wykryć, kiedy projekty nie zostały zakończone ładowanie w pełni i pozwala uniknąć awarii live unit testing. Ulepszenia wydajności kompilacji również uniknąć ponownej oceny projektów MSBuild, gdy system wie, że nic w pliku projektu uległa zmianie.

- **Różne udoskonalenia interfejsu użytkownika:** Mylące **Live Test Set - Dołącz / Wyklucz** opcję z gestu kliknięcia prawym przyciskiem myszy został zmieniony na Live Unit Testing Include / **Exclude**. Usunięto opcję **Resetuj czystość** w menu **Testowanie** > **jednostek testowych** na żywo. Jest teraz dostępny, wybierając opcję**Opcje** >  **narzędzi** > **testowania jednostek na żywo** i wybierając pozycję Usuń **utrwalone dane**.

## <a name="version-153"></a>Wersja 15.3

Począwszy od programu Visual Studio 2017 w wersji 15.3, testowanie jednostek na żywo zawiera ulepszenia i ulepszenia w dwóch głównych obszarach:

- Obsługa platformy .NET Core i .NET Standard. Można użyć live unit testing na .NET Core i .NET standard rozwiązań napisanych w języku C# lub Visual Basic.

- Usprawnienia wydajności. Można zauważyć, że wydajność jest znacznie szybsza po pierwszej pełnej kompilacji i uruchomieniu testów w ramach testowania jednostek na żywo. Można również zauważyć znaczną poprawę wydajności w kolejnych uruchomieniach live unit testing na tym samym rozwiązaniu. Teraz utrwalamy dane generowane przez testy jednostek na żywo i ponownie używamy ich tak bardzo, jak to możliwe za pomocą aktualnych kontroli.

Oprócz tych głównych dodatków, live unit testing zawiera następujące ulepszenia:

- Nowa ikona zlewki jest teraz używana do odróżnienia metody testowej od zwykłych metod. Pusta ikona zlewki wskazuje, że określony test nie jest uwzględniony w testach jednostek na żywo.

- Po kliknięciu metody testowej z okna wyskakującego interfejsu użytkownika ikony pokrycia testowania jednostek na żywo, masz teraz możliwość debugowania testu bezpośrednio z tego kontekstu w oknie interfejsu użytkownika i bez konieczności opuszczania edytora kodu. Jest to szczególnie przydatne, gdy patrzysz na test nie powiodło się.

- Do narzędzi/opcji/testowania jednostek na żywo/ogólnych dodano kilka dodatkowych opcji konfigurowalnych. Można ograniczyć pamięć używaną do testowania jednostek na żywo. Można również określić ścieżkę pliku dla utrwalonych danych live unit testing dla otwartego rozwiązania.

- Kilka dodatkowych elementów menu zostały dodane pod paskiem menu testu/live unit testing. **Resetuj clean** usuwa utrwalone dane i generuje je ponownie. **Opcja** przeskakuje do narzędzia/opcje/testowanie jednostek na żywo/ogólne.

- Teraz można użyć następujących atrybutów, aby określić w kodzie źródłowym, że chcesz wykluczyć ukierunkowane metody testowania z live unit testing:

  - Dla jednostki xUnit:`[Trait("Category", "SkipWhenLiveUnitTesting")]`
  - Dla NUnit:`[Category("SkipWhenLiveUnitTesting")]`
  - Dla MSTest:`[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do funkcji Live Unit Testing](live-unit-testing-intro.md)
- [Testowanie jednostek na żywo za pomocą programu Visual Studio](live-unit-testing.md)
