---
title: Ogólne informacje o konfiguracjach kompilacji
description: W tym artykule opisano różne konfiguracje kompilacji w Visual Studio dla komputerów Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 0bd35d415a60ea64c479b19cb506c58c2c346cc0
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983597"
---
# <a name="understanding-build-configurations"></a>Informacje o konfiguracjach kompilacji

## <a name="project-build-configurations"></a>Konfiguracje kompilacji projektu

Projekty mają wiele konfiguracji i przełączać się między nimi i umożliwiają różne dane wyjściowe w czasie kompilacji. Na przykład konfiguracja debugowania będzie wyprowadzać symbole debugowania, umożliwiając debugerowi rozpoznawanie nazw funkcji, parametrów lub zmiennych ze śladu stosu aplikacji, które uległy awarii. Chociaż te dodatkowe informacje są przydatne podczas opracowywania, prowadzi do niewypełnionego rozmiaru pliku i nie jest idealnym rozwiązaniem do dystrybucji.

Każda platforma ma konkretne konfiguracje dla swojej kompilacji.

## <a name="solution-configurations"></a>Konfiguracje rozwiązania

Zbliżone do konfiguracji projektu, konfiguracje rozwiązań są używane do tworzenia konfiguracji niestandardowych dla całego projektu. Korzystając z karty **mapowania konfiguracji** w obszarze **konfiguracji > kompilacji** , można przypisać konfigurację docelową dla każdego elementu rozwiązania, jak pokazano na poniższej ilustracji:

![Opcje mapowania konfiguracji](media/projects-and-solutions-image3.png)

Aby uzyskać więcej informacji o konfiguracjach, zobacz [Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) Video, Kuba Montemagno.

## <a name="run-configuration"></a>Uruchom konfigurację

W poprzednich wersjach Xamarin Studio można wybrać opcję ustawiania projektu jako **projektu startowego**, czyli projektu, który jest uruchamiany/debugowany podczas korzystania z globalnego polecenia Run/Debug. Zostało to wskazane przez pogrubiony krój czcionki dla nazwy projektu w konsoli projektu.

W Visual Studio dla komputerów Mac, zamiast ustawiać projekt startowy, można ustawić _konfigurację uruchamiania_. Konfiguracje uruchomieniowe są wyświetlane na liście rozwijanej na pasku narzędzi obok selektora konfiguracji kompilacji, jak pokazano poniżej:

![Lista rozwijana uruchamiania konfiguracji](media/projects-and-solutions-image8.png)

Konfiguracja przebiegu to zestaw opcji wykonywania o nazwie i kilku konfiguracjach, które są zdefiniowane w projekcie do różnych celów. Konfiguracje uruchomieniowe są definiowane na poziomie projektu, a dla każdego projektu wykonywalnego zostanie automatycznie utworzone ustawienie domyślne, chociaż można dodać dowolną liczbę. Niektóre typy projektów automatycznie generują dodatkowe konfiguracje uruchomieniowe. Na przykład projekty systemu watchOS mogą generować _szybkie i konfiguracje powiadomień._

Konfiguracje mogą być udostępniane innym deweloperom (w tym przypadku konfiguracje będą przechowywane w pliku. csproj) lub przechowywane lokalnie (w takim przypadku będą przechowywane w pliku. user).

### <a name="android-run-configurations"></a>Konfiguracje uruchamiania systemu Android

Uruchom konfiguracje dla projektów systemu Android umożliwia określenie, które działanie, usługa lub odbiornik emisji mają być uruchamiane podczas uruchamiania lub debugowania projektu. Można przekazać dodatkowe dane i ustawić flagi zamierzeń, aby można było przetestować składniki w różnych warunkach uruchamiania.

Działania inne niż `MainLauncher` muszą mieć `Exported=true` dodawane do atrybutu Activity dla debugowania na urządzeniu fizycznym lub mieć zdefiniowane filtry.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Przykłady danych, które mogą zostać uwzględnione w konfiguracjach uruchomieniowych

Poniższa lista zawiera przykładowe dane, które mogą zostać uwzględnione w konfiguracjach uruchamiania:

* Zwykły projekt .NET
  * Alternatywna aplikacja startowa
  * Argumenty początkowe
  * Katalog roboczy
  * Zmienne środowiskowe
  * Opcje środowiska uruchomieniowego mono (do użycia tylko w przypadku uruchamiania w trybie mono)
* Projekt systemu Android
  * Punkt wejścia (działanie, usługa, odbiorca)
  * Argumenty i dane intencji
* projekt systemu iOS
  * Tryb (normalny, pobieranie w tle)
* projekt rozszerzenia systemu iOS
  * Aplikacja startowa: domyślna lub niestandardowa
* Projekt WatchKit
  * Tryb (w skrócie, powiadomienie)
  * Ładunek powiadomienia

## <a name="see-also"></a>Zobacz także

- [Informacje o konfiguracjach kompilacji (Visual Studio w systemie Windows)](/visualstudio/ide/understanding-build-configurations)
