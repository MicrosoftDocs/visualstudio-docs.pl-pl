---
title: Ogólne informacje o konfiguracjach kompilacji
description: W tym artykule opisano różne konfiguracje kompilacji w programie Visual Studio dla komputerów Mac
author: conceptdev
ms.author: crdun
ms.date: 04/14/2017
ms.assetid: 78107CFA-9308-4293-A92A-9B552A259E15
ms.openlocfilehash: 7f130f5dec77e0a1965c68cf71e642fdb636832f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62983363"
---
# <a name="understanding-build-configurations"></a>Ogólne informacje o konfiguracjach kompilacji

## <a name="project-build-configurations"></a>Konfiguracje kompilacji projektu

Projekty zazwyczaj mają wiele konfiguracji i przełączania się między nimi umożliwia różne dane wyjściowe w czasie kompilacji. Na przykład konfiguracji debugowania zwróci symbole debugowania, umożliwiając debugerowi rozwiązać nazwy funkcji, parametrów i zmiennych z ślad stosu awaria aplikacji. Chociaż te informacje są przydatne podczas tworzenia, prowadzi do rozmiaru pliku nadmuchany i nie jest idealnym rozwiązaniem dla dystrybucji.

Każda platforma ma konfiguracji specyficznych dla jego kompilacji.

## <a name="solution-configurations"></a>Konfiguracje rozwiązania

Podobnie konfiguracje projektu konfiguracje rozwiązania są używane do tworzenia konfiguracje niestandardowe dla całego projektu. Za pomocą **mapowania konfiguracji** karcie **kompilacji > konfiguracje** elementu, można przypisać konfigurację docelową dla każdego elementu rozwiązania, jak pokazano w poniższej ilustracji:

![Opcje mapowania konfiguracji](media/projects-and-solutions-image3.png)

Aby uzyskać więcej informacji o konfiguracji, zobacz [programu Configuration Manager](https://www.youtube.com/watch?v=tjSdkqYh5Vg) klip wideo od James Montemagno.

## <a name="run-configuration"></a>Uruchom konfigurację

W poprzednich wersjach programu Xamarin Studio, można wybrać możliwość ustawienia projektu jako **projekt startowy**, który jest projekt, który uruchomienia/debugowania podczas korzystania z polecenia globalnego uruchomienia/debugowania. To była wskazywana przez bold krój czcionki dla nazwy projektu w konsoli do projektu.

W programie Visual Studio dla komputerów Mac, zamiast ustawiać projekt startowy można ustawić _konfigurację uruchamiania_. Uruchom konfiguracje są prezentowane na liście rozwijanej na pasku narzędzi obok selektor konfiguracji kompilacji, jak przedstawiono poniżej:

![Uruchom konfigurację, listy rozwijanej](media/projects-and-solutions-image8.png)

Konfigurację uruchomieniową jest zestawem opcji wykonywania z nazwą i kilka konfiguracji, które są zdefiniowane w projekcie do różnych celów. Uruchom konfiguracje są definiowane na poziomie projektu, a domyślny zostaną utworzone automatycznie dla każdego projektu pliku wykonywalnego, mimo że można dodać dowolną liczbę wymaganych. Niektóre typy projektu automatycznie generować dodatkowe konfiguracje wykonywania. Na przykład projekty systemu watchOS mogą generować  _konfiguracje podstawowe informacje i powiadomienia._

Konfiguracje można współużytkowane z innymi deweloperami (w takim przypadku konfiguracje będą przechowywane w pliku .csproj) lub przechowywane lokalnie (w takim przypadku będą przechowywane w pliku .user).

### <a name="android-run-configurations"></a>Uruchamianie konfiguracji systemu android

Uruchom konfiguracje dla projektów systemu Android umożliwiają określenie, które działania, usługi lub odbiornik emisji do uruchomienia podczas uruchamiania lub debugowania projektu. Można przekazać dodatkowe dane dotyczące zamiarów i ustawienie intencji flagi, aby móc testować w warunkach uruchamiania różnych składników.

Działania innych niż `MainLauncher` będzie musiała mieć `Exported=true` dodana do atrybutu działanie do debugowania na urządzeniu fizycznym lub ma zdefiniowane filtry intencji.

## <a name="examples-of-data-that-might-be-included-in-run-configurations"></a>Przykładowe dane, które może znajdować się w konfiguracji uruchamiania

Poniższa lista zawiera przykładowe dane, które mogą zostać uwzględnione w konfiguracji uruchamiania:

* Regularne projektu .NET
    * Alternatywne uruchamianie aplikacji
    * Argumenty początkowe
    * Katalog roboczy
    * Zmienne środowiskowe
    * Opcje środowiska uruchomieniowego mono (do użycia tylko wtedy, gdy jest uruchomiona na Mono)
* Projekt dla systemu android
    * Punkt wejścia (działanie, usługi, odbiorcy)
    * Argumenty metody konwersji i danych
* Projekt dla systemu iOS
    * Tryb (normalny, pobieranie w tle)
* Projekt rozszerzenia systemu iOS
    * Uruchamianie aplikacji: domyślne lub niestandardowe
* WatchKit project
    * Tryb (rzut oka, powiadomień)
    * Ładunek powiadomienia

## <a name="see-also"></a>Zobacz także

- [O konfiguracjach kompilacji (Visual Studio Windows)](/visualstudio/ide/understanding-build-configurations)