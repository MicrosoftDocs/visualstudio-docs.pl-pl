---
title: What's New in Live Unit Testing
ms.date: 10-11-2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
- Live Unit Testing What's New
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 2f032d062a751186c0abdaa37e5fb451d981e4c0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53962759"
---
# <a name="whats-new-in-live-unit-testing"></a>Nowości dotyczące funkcji Live Unit Testing

Ten temat zawiera listę nowych funkcji dodanych do Live Unit Testing w każdej wersji programu Visual Studio, począwszy od programu Visual Studio 2017 w wersji 15.3. Aby uzyskać omówienie sposobu użycia Live Unit Testing, zobacz [Live Unit Testing w programie Visual Studio 2017](live-unit-testing.md).

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-154"></a>What's new in Live Unit Testing dla programu Visual Studio 2017 w wersji 15.4

Począwszy od programu Visual Studio 2017 w wersji 15.4 Live Unit Testing obejmuje usprawnień i ulepszeń w wielu obszarach:

- **Ulepszone możliwości odnajdywania**. Dla użytkowników, którzy nie wiadomo, które Live Unit Testing funkcji istnieje, środowiska IDE programu Visual Studio pokazuje złoty pasek jest wspomniany Live Unit Testing zawsze wtedy, gdy użytkownik otwiera rozwiązanie, które zawiera testy jednostkowe, ale Live Unit Testing nie jest włączona. Informacje przedstawione w złoty pasek umożliwia użytkownikowi, aby dowiedzieć się więcej na temat Live Unit Testing i je włączyć. Złoty pasek też wyświetlane informacje, gdy Live Unit Testing wymagania wstępne nie są spełnione. Należą do nich następujące elementy:

   - Brak adaptery testowe.
   - Istnieją starsze wersje adaptery testowe.
   - Przywracanie pakietów NuGet przywoływane przez to rozwiązanie jest wymagana. 

- **Integracja z usługą powiadomień Centrum zadań**. Środowiska IDE programu Visual Studio zawiera obecnie Live Unit Testing przetwarzania w tle powiadomienia w Centrum zadań, dzięki czemu użytkownicy mogą łatwo stwierdzić, co się dzieje po włączeniu Live Unit Testing. Dotyczy to kluczy od Live Unit Testing z dużym rozwiązaniem problemu. Wcześniej przez kilka minut, dopóki nie znajdowała się ikony pokrycia, użytkownicy nie mógł określić czy Live Unit Testing naprawdę włączono i tego, czy była praca. Koniec!

- **Obsługa MSTest framework w wersji 1**: Live Unit Testing już współpracuje z trzech struktur testów jednostek pochodzących od popularnych: xUnit, NUnit oraz MSTest. Wcześniej Live Unit Testing działało tylko w przypadku projektów testów jednostkowych MSTest użycia MS Test version 2. Począwszy od programu Visual Studio 2017 w wersji 15.4 teraz obsługuje ona również MSTest w wersji 1 także. 

- **Niezawodność i wydajność**: Live Unit Testing teraz gwarantuje, że system może lepiej wykryć, kiedy projekty nie wykonano pełnego ładowania i pozwala uniknąć awarii Live Unit Testing. Tworzenie wydajnością ulepszenia również unikać reevaluating projektów programu MSBuild, gdy wiadomo, że nic w projekcie pliku została zmieniona.  

- **Udoskonalenia interfejsu użytkownika różnych**:  Mylenie **zestaw testów na żywo — uwzględnianie/wykluczanie** gestu kliknij prawym przyciskiem myszy opcję została zmieniona na **Live Unit Testing uwzględniania/wykluczania**. **Resetuj i wyczyść** opcja **testu** > **Live Unit Testing** menu zostało usunięte. Jest teraz dostępny, wybierając **narzędzia** > **opcje** > **Live Unit Testing** i wybierając polecenie **Usuń dane utrwalone** .

## <a name="whats-new-in-live-unit-testing-for-visual-studio-2017-version-153"></a>What's new in Live Unit Testing dla programu Visual Studio 2017 w wersji 15.3

Począwszy od programu Visual Studio 2017 w wersji 15.3, Live Unit Testing ulepszenia funkcji i ulepszeń w dwóch głównych obszarach:

- Obsługa platformy .NET Core i .NET Standard. Live Unit Testing można użyć w rozwiązania .NET Core i .NET Standard, napisany w języku C# lub Visual Basic.
 
-  Usprawnienia wydajności. Można zauważyć, że wydajność jest znacznie szybszy po pierwszej pełnej kompilacji i uruchomienia testów w ramach Live Unit Testing. Zauważysz również istotnie poprawiającą wydajność poprawy w kolejnych przewodnikach Start Live Unit Testing na tym samym rozwiązaniu. Teraz możemy utrwalić dane generowane przez funkcję Live Unit Testing i ponowne użycie go możliwie jak możliwego Sprawdzanie aktualności. 
 
Oprócz tych główne dodatki Live Unit Testing obejmuje następujące ulepszenia: 

- Nowa ikona zlewce obecnie jest używana do rozróżniania metodę testową z metodami regularnych. Ikona puste zlewce wskazuje, że określonego testu nie jest uwzględniony w Live Unit Testing. 

- Po kliknięciu metody testowej w oknie podręcznym interfejsu użytkownika z ikoną pokrycia Live Unit Testing, masz teraz możliwość debugowania testów bezpośrednio w tym kontekście, w oknie interfejsu użytkownika i bez konieczności opuszczania edytora kodu. Jest to szczególnie przydatne, jeśli patrzy testów zakończonych niepowodzeniem.  

- Dodano kilka dodatkowych opcji można skonfigurować do narzędzia/Opcje/Live Unit Testing / ogólne. Aby limit, pamięć używana na potrzeby Live Unit Testing. Można również określić ścieżkę pliku danych utrwalonych Live Unit Testing dla otwartego rozwiązania. 

- Dodano kilka dodatkowe elementy menu w menu paska z testów/Live Unit Testing. **Resetuj czysty** spowoduje usunięcie istniejących danych i wygeneruje ją ponownie. **Opcja** przechodzi do narzędzia/Opcje/Live Unit Testing / ogólne.
  
- Następujące atrybuty można teraz użyć, aby określić w kodzie źródłowym, chcesz wykluczyć metod testowych docelowych z Live Unit Testing:
   - Aby uzyskać xUnit: `[Trait("Category", "SkipWhenLiveUnitTesting")]`
   - Aby uzyskać NUnit: `[Category("SkipWhenLiveUnitTesting")]`
   - Aby uzyskać MSTest: `[TestCategory("SkipWhenLiveUnitTesting")]`

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do funkcji Live Unit Testing](live-unit-testing-intro.md)   
- [Live Unit Testing w programie Visual Studio 2017](live-unit-testing.md)
