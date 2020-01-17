---
title: Co nowego w programie Live Unit Testing w programie Visual Studio 2017
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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114272"
---
# <a name="whats-new-in-live-unit-testing-for-visual-studio-2017"></a>Co nowego w programie Live Unit Testing for Visual Studio 2017

W tym temacie wymieniono nowe funkcje, które zostały dodane do Live Unit Testing w każdej wersji programu Visual Studio, począwszy od wersji 15,3 programu Visual Studio 2017. Aby zapoznać się z omówieniem sposobu korzystania z Live Unit Testing, zobacz [Live Unit Testing with Visual Studio](live-unit-testing.md).

## <a name="version-154"></a>Wersja 15,4

Począwszy od programu Visual Studio 2017 w wersji 15,4, Live Unit Testing zawiera ulepszenia i ulepszenia w wielu obszarach:

- **Ulepszona możliwość odnajdywania**. W przypadku użytkowników, którzy nie wiedzą, że funkcja Live Unit Testing istnieje, środowisko IDE programu Visual Studio Wyświetla złoty pasek wskazujący Live Unit Testing za każdym razem, gdy użytkownik otworzy rozwiązanie, które zawiera testy jednostkowe, ale Live Unit Testing nie jest włączona. Informacje przedstawione na złotym pasku pozwalają użytkownikowi dowiedzieć się więcej na temat Live Unit Testing i włączyć go. Złoty pasek wyświetla również informacje, gdy Live Unit Testing wymagania wstępne nie są spełnione. Należą do nich następujące elementy:

  - Brak adapterów testowych.
  - Istnieją starsze wersje adapterów testowych.
  - Wymagany jest przywracanie pakietów NuGet, do których odwołuje się rozwiązanie.

- **Integracja z powiadomieniami centrum zadań**. Środowisko IDE programu Visual Studio wyświetla teraz Live Unit Testing powiadomienia o przetwarzaniu w tle w centrum zadań, dzięki czemu użytkownicy mogą łatwo określić, co dzieje się, gdy Live Unit Testing jest włączona. Eliminuje to kluczowy problem z uruchamianiem Live Unit Testing na dużym rozwiązaniu. Wcześniej przez kilka minut, aż pojawiły się ikony pokrycia, użytkownicy nie będą mogli określić, czy Live Unit Testing był naprawdę włączony i czy działał. Jeszcze nie!

- **Obsługa programu MSTest Framework w wersji 1**: Live Unit Testing już współdziałać z trzema popularnymi platformami testowania jednostek: XUnit, nunit i MSTest. Wcześniej Live Unit Testing działała tylko wtedy, gdy projekty testów jednostkowych MSTest korzystały z MS test w wersji 2. Począwszy od programu Visual Studio 2017 w wersji 15,4, obsługuje także również MSTest w wersji 1.

- **Niezawodność & wydajność**: Live Unit Testing teraz zapewnia, że system może lepiej wykryć, kiedy projekty nie zakończyły się w pełni i zapobiega awarii Live Unit Testing. Udoskonalenia wydajności kompilacji należy również unikać ponownej oceny projektów programu MSBuild, gdy system wie, że nic w pliku projektu nie uległo zmianie.

- **Różne udoskonalenia interfejsu użytkownika**: zmiana nazwy **zestawu testów aktywnych na żywo — dołączenie/wykluczenie** z gestu kliknięcia prawym przyciskiem myszy została zmieniona na **Live Unit Testing Uwzględnij/Wyklucz**. Opcja **Zresetuj czyste** w menu **Live Unit Testing** > **testowych** została usunięta. Jest teraz dostępna, wybierając pozycję **narzędzia** > **Opcje** > **Live Unit Testing** i wybierając pozycję **Usuń utrwalone dane**.

## <a name="version-153"></a>Wersja 15,3

Począwszy od programu Visual Studio 2017 w wersji 15,3, Live Unit Testing funkcje ulepszenia i ulepszenia w dwóch głównych obszarach:

- Obsługa platformy .NET Core i .NET Standard. Live Unit Testing można używać w przypadku rozwiązań .NET Core i .NET Standard zapisanych w C# obu lub Visual Basic.

- Usprawnienia wydajności. Zauważ, że wydajność jest znacznie szybsza po pierwszej pełnej kompilacji i uruchomieniu testów w obszarze Live Unit Testing. Zauważysz również znaczące zwiększenie wydajności w kolejnych uruchomieniach Live Unit Testing na tym samym rozwiązaniu. Teraz utrwalamy dane wygenerowane przez Live Unit Testing i wielokrotnego użytku.

Oprócz tych głównych dodatków, Live Unit Testing obejmuje następujące udoskonalenia:

- Nowa ikona zlewki jest teraz używana do odróżniania metody testowej od zwykłych metod. Pusta ikona zlewki wskazuje, że konkretny test nie jest uwzględniony w Live Unit Testing.

- Po kliknięciu metody testowej w oknie podręcznym interfejsie użytkownika ikony pokrycia Live Unit Testing masz teraz możliwość debugowania bezpośrednio z tego kontekstu w oknie interfejsu użytkownika i bez konieczności opuszczania edytora kodu. Jest to szczególnie przydatne, gdy przeglądasz test zakończony niepowodzeniem.

- Dodano kilka dodatkowych konfigurowalnych opcji Narzędzia/Opcje/Live Unit Testing/ogólne. Możesz wycap pamięć używaną dla Live Unit Testing. Możesz również określić ścieżkę pliku dla utrwalonych Live Unit Testing danych dla otwartego rozwiązania.

- Dodano kilka dodatkowych elementów menu pod paskiem menu test/Live Unit Testing. **Zresetuj czyste** usuwa utrwalone dane i wygeneruje je ponownie. **Opcja** przechodzi do opcji narzędzia/opcje/Live Unit Testing/ogólne.

- Teraz można użyć następujących atrybutów, aby określić w kodzie źródłowym, który ma zostać wykluczony dla określonych metod testowych z Live Unit Testing:

  - Aby uzyskać xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
  - Aby uzyskać NUnit: `[Category("SkipWhenLiveUnitTesting")]`
  - Aby uzyskać MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do funkcji Live Unit Testing](live-unit-testing-intro.md)
- [Live Unit Testing z programem Visual Studio](live-unit-testing.md)
